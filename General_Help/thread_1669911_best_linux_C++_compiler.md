---
title: "best linux C++ compiler"
date: 2011-01-18
forum: General Help
---

### Post by Arminius on 2011-01-18
what's the Best linux C++ compiler for newbs?
I was trying Anjuta, typed in some simple code from the text book, but it came back with a completely unhelpful error message, is there a gui compiler that will give some pointers or idea's as to what mistake you made with the code?

Before I moved to linux I used to use Auto IT and it was pretty good at debugging.

---

### Post by cipherboy_loc on 2011-01-18
Not to rant or anything, but technically speaking, a compiler is just a utility that reads a file and converts it to a format that the machine can read. What you mean is an IDE. If you can spare the bloat of Java, you can download the Eclipse CDT (the C/C++ Developers Toolkit) plugin for Eclipse (You need to install Eclipse and Java first).

Now, most, if not all, of these programs interface into GCC. GCC is the GNU Compiler Collection that supports C, C++, Obj-C and a couple others. This is, except in a few rare and specialized occasions, what people use. From a terminal (Applications -> Accessories -> Terminal):

```

sudo apt-get install build-essentials g++-4.4 gcc-4.4

```to install the GCC C and C++ compilers plus common libraries.



Cipherboy

> **Arminius said:**
> what's the Best linux C++ compiler for newbs?
I was trying Anjuta, typed in some simple code from the text book, but it came back with a completely unhelpful error message, is there a gui compiler that will give some pointers or idea's as to what mistake you made with the code?

Before I moved to linux I used to use Auto IT and it was pretty good at debugging.

---

### Post by Simian Man on 2011-01-18
On Windows "compiler" and "IDE (Integrated Development Environment)" are almost synonymous because the major IDEs come with compilers.  On Linux, they are separate concepts.  Most people use the g++ compiler on Linux which all of the IDEs support.

There are several good IDEs for Linux, but Anjuta is *not* one of them.  Check out Eclipse (with the cdt plugin), Code::Blocks or Geany.

---

### Post by hwttdz on 2011-01-18
I like gedit as my editor, the syntax highlighting is actually not bad and no bloat to speak of (unless you want to break out the vi, vim or emacs).  And I use either g++ or icc (intel c compiler).

---

### Post by cipherboy_loc on 2011-01-18
+1 gedit. There are additional plugins that can be used for things such as auto completion, etc.

Cipherboy

---

### Post by NevilleBamshoe on 2011-01-18
Codelite is an excellent IDE for getting started in C++ on linux.
Its very lightweight and has all the features you would expect from modern IDEs (code completion etc.)

Its also available in the standard repo so using synaptic you can be coding in a few minutes ...

Only thing I miss is the blatant speed of text processing available with VIM ...

---

### Post by Arminius on 2011-01-18
I tried Eclipse
and I tried the code ```
#include <iostream>
using namespace std;

int main () {
    cout <<  "Never fear, C++ is here!";
    return 0;
    }
```

but it came back with "build failed, unable to find an ant file to run"

That's very unhelpful, I googled ant file to find out what that is, came up with nothing.

---

### Post by Vaphell on 2011-01-18
eclipse is more java oriented and rather bloated, try codelite or codeblocks - they specialize in c/c++ and are much leaner.

---

### Post by sum1nil on 2011-01-18
Hi ya.
Codelite is great (Ubuntu needs to upgrade it's disto I think)
Monodevelop is an altervative. It does both unmanaged and managed c/C++ code and of course C#/Mono all in the same IDE and in the same workspace. It does have a few issues but the mono project is very active.

psssst, write Bioshock 3 for linux. :)

---

### Post by sum1nil on 2011-01-18
Hi ya.
Codelite is great (Ubuntu needs to upgrade it's disto I think)
Monodevelop is an altervative. It does both unmanaged and managed c/C++ code and of course C#/Mono all in the same IDE and in the same workspace. It does have a few issues but the mono project is very active.

psssst, write Bioshock 3 for linux. :)

Sorry everyone for the duplicate.

---

### Post by Arminius on 2011-01-18
Codelite's run button is all greyed out, looking through the help files and so far can't figure out how to get it to run the damn code.

---

### Post by Simian Man on 2011-01-18
> **Arminius said:**
> but it came back with "build failed, unable to find an ant file to run"

That's very unhelpful, I googled ant file to find out what that is, came up with nothing.
Ant is a Java build system.  I suspect that you either don't have the CDT (C Development Tools) plugin installed, or didn't create a C++ project properly.

> **Vaphell said:**
> eclipse is more java oriented and rather bloated, try codelite or codeblocks - they specialize in c/c++ and are much leaner.
Eclipse with the CDT has more features for C and C++ than Code::Blocks has, despite being good for Java as well.  It's also a lot leaner than it used to be I think.  Though Code::Blocks is decent too.

---

### Post by Arminius on 2011-01-18
and code blocks just comes back with sh: /home/user/Desktop/test: Permission denied

every time I try to run the code

```
#include <iostream>
using namespace std;

int main () {
    cout <<  "Never fear, C++ is here!";
    return 0;
    }

```

---

### Post by pqwoerituytrueiwoq on 2011-01-18
This will compile and run that test

nano Desktop/test.cpp
save this:
```
#include <iostream>
 using namespace std;  
int main () {
     cout <<  "Never fear, C++ is here!";
     return 0;
     }
```
g++ Desktop/test.cpp
./a.out

---

### Post by Arminius on 2011-01-19
code blocks came up with that permisson denied again
and everything else had the run command greyed out
```
#include <iostream>
 using namespace std;  
int main () {
     cout <<  "Never fear, C++ is here!";
     return 0;
     }
```

---

### Post by NevilleBamshoe on 2011-01-19
To run a simple program in codelite ...

1. Workspace Tab -> New Workspace
2. Create Your Workspace
3. Workspace Tab -> New Project
4. In the categories select Console
5. Select G++ executable
6. Fill in the name ...
7. Under your project in the left pane you should find a src folder
    main.cpp should already be created with a sample program.
8. Run and enjoy

P.S. Get the newest version of Codelite from [www.codelite.org](www.codelite.org) ... Its in .deb format so you get hassle free install

---

### Post by pqwoerituytrueiwoq on 2011-01-19
> **NevilleBamshoe said:**
> To run a simple program in codelite ...

1. Workspace Tab -> New Workspace
2. Create Your Workspace
3. Workspace Tab -> New Project
4. In the categories select Console
5. Select G++ executable
6. Fill in the name ...
7. Under your project in the left pane you should find a src folder
    main.cpp should already be created with a sample program.
8. Run and enjoy

P.S. Get the newest version of Codelite from [www.codelite.org]("http://www.codelite.org") ... Its in .deb format so you get hassle free install
app looks useful :)
it put my executable here:
/home/$USER/.codelite/testSpace/Debug

convent link to codelite
[http://sourceforge.net/projects/codelite/files/Releases/](http://sourceforge.net/projects/codelite/files/Releases/)

---

