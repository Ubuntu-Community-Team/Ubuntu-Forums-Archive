---
title: "Problem with codeblocks help please"
date: 2010-01-26
forum: General Help
---

### Post by tkblackbelt on 2010-01-26
Hi I just installed codeblocks in ubuntu and when i compile this 

#include <iostream>

using namespace std;

int main()
{
    char choice;
    do
    {
    cout << "Enter your name: ";
    cin >> choice;
    cout << choice<<endl;
    }
    while(choice != 0);
    return 0;
}

it outputs this in console project:

Enter your name: chuck
c
Enter your name: h
Enter your name: u
Enter your name: c
Enter your name: k

why is it doing that when I use codeblocks in windows it works perfectly

---

### Post by t4thfavor on 2010-01-26
Windows and Linux are a bit different even it c++ is a standard. The Windows one may be using Microsoft C++ while Linux is probably using ANSI c++. Just because it's called c++ doesn't mean it's all the same.

---

