---
title: "how to compile c++"
date: 2010-02-18
forum: General Help
---

### Post by selvavicto on 2010-02-18
hi my dear community ............ 
 i'm a new entry to this....... i dont know how to compile c++ in ubuntu 9.10....... i  have tried the  following method i got ---------------


""selva@selva-desktop:~$ sudo gedit first.cpp
[sudo] password for selva: 
then i typed following program
----------------------------------------
#include<iostream.h>
#include<conio.h>
void main()
{
cout<<"hi";
getch();
}
-------------------------------
selva@selva-desktop:~$ g++ first.cpp -o test
first.cpp:1:21: error: iostream.h: No such file or directory
first.cpp:2: error: ‘::main’ must return ‘int’
first.cpp: In function ‘int main()’:
first.cpp:4: error: ‘cout’ was not declared in this scope
first.cpp:5: error: ‘getch’ was not declared in this scope
selva@selva-desktop:~$ ./test
bash: ./test: No such file or directory
selva@selva-desktop:~$

ple tell how compile java also....................

---

### Post by hj_ebfe on 2010-02-18
In c++ the headers do not take the .h extension. You must also use namespaces. In your case you need to do either std::cout where std in the namespace containing the c++ function cout or put the line using namespace std; before the cout call.  Don't want to bash or anything but a quick search for a basic c++ programming tutorial would have solved the problem.

---

### Post by wojox on 2010-02-18
[PHP]
#include <iostream>

int main()
{
std::cout<<"Hello World"<<std::endl;
return 0;
}
[/PHP]

---

### Post by point_man on 2010-02-18
I do not think conio is a standard header file. You would not need getch() because you are not exiting the 'output screen'.
Also, as a beginner if you find it difficult to write std::cout everytime you could simply add this line after header files :

using namespace std;

Read up on namespaces to know what they are. [http://en.wikipedia.org/wiki/Namespace_(computer_science)]("http://en.wikipedia.org/wiki/Namespace_(computer_science)")

Did this help you out? Ask if you have doubts.

---

### Post by gmargo on 2010-02-18
> **selvavicto said:**
> selva@selva-desktop:~$ sudo gedit first.cpp

There's no need to use **sudo** here.

---

### Post by azagaros on 2010-02-18
this is how that c++ code should look like

[PHP]
#include <iostream>

void main()
{
   char cChar = 0;
   
   std::cout<<"Hi!"<<endl;
   std::cin>>cChar;
}
[/PHP]


The other form is 
[PHP]
#include <iostream>
using namespace std;

void main()
{
   char cChar = 0;

   cout<<"Hi!"<<endl;
   cin>>cChar;
}
[/PHP]

at a command line "gcc myprog.cpp"  should generate a file that reads "myprog" in the directory that you compiled from.

Just my two cents to this discussion.

---

