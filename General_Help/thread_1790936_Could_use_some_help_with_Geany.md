---
title: "Could use some help with Geany"
date: 2011-06-25
forum: General Help
---

### Post by Vizerox on 2011-06-25
I'm trying to do the super basic hello world code in c++. I typed it in just how the walk-through showed me, but I get an error every time I click the build button.

g++ -Wall -o "untitled" "untitled.cmm" (in directory: /home/hunter)
Compilation failed.
untitled.cmm: file not recognized: File format not recognized
collect2: ld returned 1 exit status

I really have no idea what the **** I'm doing :)

```
#include <iostream>

using namespace std;

int main()    {
    cout << "hello world!";
    getchar();
    return 0;
}
```
 
Is what I have typed in.

---

### Post by Toz on 2011-06-25
First, rename your file to **untitled.cpp**.

Secondly, your use of getchar() is incorrect. You need to #include cstdio and declare it first. ```
#include <iostream>
#include <cstdio>

using namespace std;

int main()
{
        char c;
        cout << "hello world!";
        c=getchar();
        return 0;
}

```

---

### Post by Vizerox on 2011-06-26
```
#include <iostream>

using namespace std;

int main() {

     string strName;
     cout << "Hello World!";
     return 0;
}


```I ended up just deleting the " getchar(); " line and it worked just fine. Is there any reason I needed that in there? And what is " #include <cstdio> " for?

---

### Post by Toz on 2011-06-26
cstdio is the header file that includes the function declaration for getchar(). In other words, to use getchar(), you must include cstdio.

---

### Post by Vizerox on 2011-06-26
Hello World!

----------------
(Program exited with code:0)
press return to continue 

that shows up at the buttom of my command prompt when I run it like this 
```
#include <iostream>

using namespace std;
int main() {
        string strName;
        cout << "Hello World!";
        return 0;
}

```but if  I run it how you did, it just shows "Hello World".  Is that what the extra header file and function declaration are there for?

---

### Post by Toz on 2011-06-26
The getchar() function waits for you to press a key (then the enter key) then exits the program. 

You had getchar() in your first example so I thought you were trying to get it to wait for a keypress (and enter) before exiting.

Try this:```
#include <iostream>
#include <cstdio>

using namespace std;

int main()
{
        char c;
        cout << "hello world!\n";
        cout << "waiting for key press.....";
        c=getchar();
        cout << "exiting\n";
        return 0;
}

```

---

### Post by Vizerox on 2011-06-26
Na I'm just trying to learn this... I see what you did there though.

Does that cstudio header do other things then just set the script up for waiting on someone to press a button or does it have a bunch of other uses?

---

### Post by The Cog on 2011-06-26
There are lots of pre-made functions that you can make use of. I wouls probably call them library functions. But you don't want to include the definitions of all these thousands of functions in every program you compile - it would take too much time (and maybe memory). So the definitions are grouped into related categories ane put in a header file. The getchar function is defined in the cstudio header file, which contains definitions for standard input/output functions. 

So if you want to use getchar (or other io funtions like that), you have to include the cstudio header file that described the function (what arguments it takes, what value it returns) so the compiler can make use of the function. Without including the header file, the compiler would complain that it doesn't know what getchar is.

---

### Post by Vizerox on 2011-06-26
Thanks for all your help man!

---

