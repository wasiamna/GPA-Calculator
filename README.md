# GPA-Calculator
A GPA Calculator built in C++ that helps students calculate their GPA quickly and accurately without wasting time on manual calculations. It takes obtained marks, total marks, credit hours, and number of courses as input, validates the data, and instantly returns the GPA.


#include <iostream>
#include<iomanip>
using namespace std;

// Returns gradepoints according to percentage
float getGradePoint(float percentage)
{
    if (percentage >= 85)
        return 4.0;
    else if (percentage >= 80)
        return 3.7;
    else if (percentage >= 75)
        return 3.3;
    else if (percentage >= 70)
        return 3.0;
    else if (percentage >= 65)
        return 2.7;
    else if (percentage >= 61)
        return 2.3;
    else if (percentage >= 58)
        return 2.0;
    else if (percentage >= 55)
        return 1.7;
    else if (percentage >= 50)
        return 1.0;
    else
        return 0.0;
}

int main()
{
// Take user input and validate it
    int subjects;
    do 
    {
    cout << "Enter number of subjects: ";
    cin >> subjects;
     
    if(subjects <= 0){
        cout << "Invalid Input!" << endl;
    }

    } while(subjects <= 0);

    float obtained, total, percentage;
    float creditHours;
    float totalPoints = 0;
    float totalCredits = 0;

    for (int i = 1; i <= subjects; i++)
    {
        cout << "\nSubject " << i << endl;
        
        do 
        {
        cout << "Enter obtained marks: ";
        cin >> obtained;

        cout << "Enter total marks: ";
        cin >> total;

        if (total <= 0)
        {
        cout << "Total marks must be greater than zero" << endl;
        }
        else if (obtained < 0 || obtained > total)
        {
        cout << "Obtained marks must be between 0 and total marks" << endl;
        }

        } while (obtained < 0 || total <= 0 || obtained > total);

        do 
        {
            cout << "Enter credit hours: ";
            cin >> creditHours;

            if(creditHours <= 0)
            {
                cout << "Credit hours must be greater than zero" << endl;
            }
        } while (creditHours <= 0);

        percentage = (obtained / total) * 100;


        //Call function to get gradepoints
        float gp = getGradePoint(percentage);

        totalPoints += gp * creditHours;
        totalCredits += creditHours;

        cout << "Percentage = " << percentage << "%" << endl;
        cout << "Grade Point = " << gp << endl;
    }
    // Calculate final GPA
    float GPA = totalPoints / totalCredits;

    //Limit output to two decimal places
    cout << fixed << setprecision(2);
    cout << "\n GPA = " << GPA << endl;

    return 0;
}
