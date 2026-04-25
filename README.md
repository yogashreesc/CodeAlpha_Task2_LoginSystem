 Login & Registration System (C++)

Description

This project is a simple Login and Registration System developed using C++. It allows users to register and log in using file handling to store and verify credentials.

---

 Code
```cpp
#include <iostream>
#include <fstream>
#include <string>
using namespace std;

void registerUser() {
    string username, password;

    cout << "\n--- Register ---\n";
    cout << "Enter username: ";
    cin >> username;
    cout << "Enter password: ";
    cin >> password;

    ofstream file("users.txt", ios::app);
    file << username << " " << password << endl;
    file.close();

    cout << "Registration successful!\n";
}

void loginUser() {
    string username, password;
    string fileUser, filePass;
    bool found = false;

    cout << "\n--- Login ---\n";
    cout << "Enter username: ";
    cin >> username;
    cout << "Enter password: ";
    cin >> password;

    ifstream file("users.txt");

    while (file >> fileUser >> filePass) {
        if (fileUser == username && filePass == password) {
            found = true;
            break;
        }
    }

    file.close();

    if (found)
        cout << "Login successful! Welcome " << username << endl;
    else
        cout << "Invalid username or password!\n";
}

int main() {
    int choice;

    do {
        cout << "\n===== MENU =====\n";
        cout << "1. Register\n";
        cout << "2. Login\n";
        cout << "3. Exit\n";
        cout << "Enter choice: ";
        cin >> choice;

        switch(choice) {
            case 1: registerUser(); break;
            case 2: loginUser(); break;
            case 3: cout << "Exiting...\n"; break;
            default: cout << "Invalid choice!\n";
        }

    } while(choice != 3);

    return 0;
}
```
## Sample Output

[![Output](IMG-20260426_002149.jpg)](IMG-20260426_002149.jpg)

---

Author

Yogashree S C