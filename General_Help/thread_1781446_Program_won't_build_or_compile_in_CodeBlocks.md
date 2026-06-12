---
title: "Program won't build or compile in CodeBlocks"
date: 2011-06-13
forum: General Help
---

### Post by Leo Dragonheart on 2011-06-13
Hi, I am back with a question? I wrote this code awhile back and it worked. I am now trying to load it into codeblocks but can't get it to compile and run, can someone help please?


#include <iostream>				// Leo M. Dragonheart...
#include <string>				// Tue 24 Feb 2009 11:32:40 PM CST...
#include <sstream>				// My very 1st unassisted working program...!
using namespace std;

int main()
{
    string mystr;
    bool ispasscode=false;
    int passcode;

    while (!ispasscode)
    {
        cout << "Please enter your passcode: ";
        getline (cin,mystr);
        stringstream(mystr) >> passcode;

        if (passcode == 64) {
            ispasscode = true;
            cout << "You have entered the correct passcode: Have a nice day! " << endl;
        }
        else {
            cout << "This is not your passcode!...Please try again! " << endl;
        }
    }
    cin.get();
    return 0;
}

---

