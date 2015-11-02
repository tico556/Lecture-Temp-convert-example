#include <stdio.h>
// preconditions and post condition ** REMEMBER!**

enum boolean { FALSE, TRUE };
typedef enum boolean Bool;
enum choice{CONVERT_FAHR_TO_CELS, 
			CONVERT_CELS_TO_FAHR};

enum temp_units { FAHRENHEIT, CELSIUS };
typedef enum temp_units Temp_units;

typedef enum choice Choice;

void convert_temperature_with_keyboard_input(void);



// Precondition: none
// Postcondition: returns appropriate value from the enumerated type
// choice according to user's selection.
Choice get_choice(void);



// Precondition: none
// Postcondition: User has entered and converted one temperature
// from F to C and the result was displayed.
void convert_f_to_c(void);
void convert_c_to_f(void);

double get_temperature(Temp_units units);
void convert_temperature(Choice conversion_direction,
	double initial_temp, double* pFinal_temp);

void display_temperature_conversion(Choice conversion_direction,
	double intitial_temp, double final_temp);

Bool temperature_is_less_than_absolute_zero(Temp_units, double temperature);

Bool user_wishes_to_continue();
void clear_key(void);
// Precondition: none
// postcondition: User has entered and converted one temp
// from C to F and the result was displayed



int main(int argc, char* argv[])
{
	do
	{
		convert_temperature_with_keyboard_input();

	} while (user_wishes_to_continue());

	return 0;


}


void convert_temperature_with_keyboard_input(void)
{
	Choice choice;
	
	choice = get_choice();

	switch (choice)
	{
	case CONVERT_FAHR_TO_CELS:
		convert_f_to_c(); // not being used in an expression, so its not returning anything
			break;

	case CONVERT_CELS_TO_FAHR:
		convert_c_to_f();
		break;

	}

	// do it

	return;
}


Bool user_wishes_to_continue()
{
	char input;
	
		do
	{		
			
			do{
				printf("Do you wish to continue?: ");
				scanf(" %c", &input);
				clear_key();
				printf("\n");
				if (input != 'y' && input != 'Y' && input != 'n' && input != 'N')
				{
					printf("That is an invalid input. ");
					printf("Please enter Y or N. \n ");
				}								
			} while (input != 'y' && input != 'Y' && input != 'n' && input != 'N');

			if (input == 'y' || input == 'Y')
		{
			return TRUE;
		}
	
	} while (input == 'y' || input == 'Y');
	
					
	return FALSE;
}

void clear_key(void)
{
char c;

scanf("%c", &c);
while (c != '\n')
{
scanf("%c", &c);
}
}

void convert_f_to_c(void)
{
	double temperature_in_f; //input
	double temperature_in_c; // output

	//get temperature
	temperature_in_f = 
		get_temperature(FAHRENHEIT);

	// convert it
	convert_temperature(CONVERT_FAHR_TO_CELS, 
		temperature_in_f, 
		&temperature_in_c);
	// display it
	display_temperature_conversion(CONVERT_FAHR_TO_CELS, 
		temperature_in_f,
		temperature_in_c);
	return;
}

void convert_c_to_f(void)
{
	double temperature_in_f;
	double temperature_in_c;

	//get temperature
	temperature_in_c =
		get_temperature(CELSIUS);

	// convert it
	convert_temperature(CONVERT_CELS_TO_FAHR,
		temperature_in_c,
		&temperature_in_f);
	// display it
	display_temperature_conversion(CONVERT_CELS_TO_FAHR, 
		temperature_in_c,
		temperature_in_f);
	return;
}

Choice get_choice(void)
{
	char answer;
	Choice final_answer;

//prompt
// ask which way to convert
	do{
		printf(" Please from one of the following options. \n");
		printf(" 1) Convert from Fahrenheit to Celsius \n");
		printf(" 2) Convert from Celsius to Fahrenheit \n");
// get and validate answer
		scanf(" %c", &answer);
		clear_key();
		if (answer != '1' && answer != '2')
		{
			printf("I'm sorry you may only choose '1' or '2'. \n");
			}
	} while (answer != '1' && answer  != '2');

	// return answer
	
	if (answer == '1')
	{
		final_answer = CONVERT_FAHR_TO_CELS;

	}
	else
	{
		final_answer = CONVERT_CELS_TO_FAHR;
		}


	return final_answer;

}

double get_temperature(Temp_units units) 
{
	double temperature;
	char unit_name_fahrenheit[] = "Fahrenheit"; // square bracket in declaration, tells how many elements is in an array,
	char unit_name_celsius[] = "Celsius";		// must use an initializer, can use double quotes for char array
	char* pUnits;
	int number_of_conversions;
	if (units == FAHRENHEIT)
	{
		pUnits = unit_name_fahrenheit;
		
	}
	else
	{
		pUnits = unit_name_celsius;

	}
	

	do{
		printf("Please enter the temperature in degrees %s:  ",  pUnits);
		number_of_conversions = scanf("%lf", &temperature);
		clear_key();
		if (number_of_conversions != 1 || temperature_is_less_than_absolute_zero(units, temperature))
		{
			printf("You must enter a temperature that is not less than absolute zero.");
		}

	} while(number_of_conversions != 1 || 
		temperature_is_less_than_absolute_zero(units, temperature));

	return temperature;

}

void convert_temperature(Choice conversion_direction, //stub
	double initial_temp, double* pFinal_temp)
{
	if (conversion_direction == CONVERT_FAHR_TO_CELS)
	{
		*pFinal_temp = (initial_temp - 32) * (5.0 / 9.0);
	}
	else
	{
		*pFinal_temp = initial_temp * (9.0 / 5.0) + 32;

	}
}

void display_temperature_conversion(Choice conversion_direction, 
	double initial_temp, double final_temp)
{
	printf("stuff\n");
	printf("conversion direction: %d \n", conversion_direction);
	printf("initial temperature: %f\n", initial_temp);
	printf("Final temperature: %f\n", final_temp);

	
	return;
}

Bool temperature_is_less_than_absolute_zero(Temp_units units, double temperature)
{
	const double ABSOLUTE_ZERO_IN_DEGREES_F = -459.67;
	const double ABSOLUTE_ZERO_IN_DEGREES_C = -273.15;
	
	if (units == FAHRENHEIT)
	{
		return temperature < ABSOLUTE_ZERO_IN_DEGREES_F;
		
	}
	else
	{
		return temperature < ABSOLUTE_ZERO_IN_DEGREES_C;

	}


}
