# TerminalHacker
Unity/C # Tutorial
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class Hacker : MonoBehaviour {
    const string menu = "You can type Menu at anytime.";
    string[] CostcoPassword = { "Apples", "Chips", "Yakult", "Steak", "Cookies" };
    string[] ApplePassword = { "Macbook", "iPhone", "Airpods", "iPad", "iWatch" };
    string[] CarPassword = { "Mustang", "Maserati", "Model X", "Lamborghini" };
    int level;
    enum Screen {MainMenu, Password, Win}
    Screen currentScreen;
    string password;

    // Start is called before the first frame update
    void Start() {
        ShowMainMenu();
    }

    void OnUserInput(string input) {
        if (input == "Menu") {
            ShowMainMenu();
        }
        else if (currentScreen == Screen.MainMenu) {
            RunMainMenu(input);
        }
        else if (currentScreen == Screen.Password) {
            CheckPassword(input);
        }

    }

    void ShowMainMenu() {
        // this is how to create a function (function is void because it's not returning anything)
        currentScreen = Screen.MainMenu;
        Terminal.ClearScreen();
        Terminal.WriteLine("What would you like to hack into?");
        Terminal.WriteLine(" ");
        Terminal.WriteLine("Press 1 for the local Costco");
        Terminal.WriteLine("Press 2 for the Apple Store");
        Terminal.WriteLine("Press 3 for the car shop");
        Terminal.WriteLine("Enter your selection: ");
    }

    void RunMainMenu(string input) {
        bool ValidLevelNumber = (input == "1" || input == "2" || input == "3");
        if (ValidLevelNumber) {
            level = int.Parse(input);
            // will be used in RandomPassword method
            // used to determine which level of words the user will guess
            AskforPassword();
        }
        else {
            Terminal.WriteLine("Please choose a valid level");
            Terminal.WriteLine(menu);
        }
    }

    void AskforPassword() {
        Terminal.ClearScreen();
        currentScreen = Screen.Password; // because StartGame is called, current screen is now at Password which will call CheckPassword and run that method
        RandomPassword();
        Terminal.WriteLine("Enter your password, hint: " + password.Anagram());
        Terminal.WriteLine(menu);

    }

    private void RandomPassword() {
        switch (level) {
            case 1: // case is determined by what level user inputted
                int index = Random.Range(0, CostcoPassword.Length);
                password = CostcoPassword[index];
                break;
            case 2:
                int index2 = Random.Range(0, ApplePassword.Length);
                password = ApplePassword[index2];
                break;
            case 3:
                int index3 = Random.Range(0, CarPassword.Length);
                password = CarPassword[index3];
                break;
            default:
                Debug.LogError("Invalid Level Number");
                break;
        }
    }

    void CheckPassword(string input) {
        if (input == password) {
            DisplayWinScreen();
        }
        else {
            AskforPassword();
        }
    }

    void DisplayWinScreen() {
        currentScreen = Screen.Win;
        Terminal.ClearScreen();
        LevelReward();
        Terminal.WriteLine(menu);
    }

    void LevelReward() {
        switch (level) {
            case 1:
                Terminal.WriteLine("Have a cookie...");
                Terminal.WriteLine(@"
Congrats you won! Enjoy a cookie!
     ___
    /. .\
    | . |
    \___/

          "
                    );
                break;
            case 2:
                Terminal.WriteLine("Enjoy a Vintage Macintosh ...");
                Terminal.WriteLine(@"

Congrats you won!. Enjoy this apple logo!
           .:'
        __ :'__
     .'`  `-'  ``.
    :          .-'
    :         :  
     :         `-;
      `.__.-.__.'
"
                );
                break;
            case 3:
                Terminal.WriteLine("Congrats, enjoy this car!");
                Terminal.WriteLine(@"
             ~ (@\   \
---   _________]_[__/_>________
     /  ____ \ <>     |  ____  \
    =\_/ __ \_\_______|_/ __ \__D
________(__)_____________(__)____
"
                );
                break;
        }
        
    }
}
