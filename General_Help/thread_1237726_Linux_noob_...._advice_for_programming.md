---
title: "Linux noob .... advice for programming"
date: 2009-08-11
forum: General Help
---

### Post by rocky35 on 2009-08-11
I am new to Linux, I have just had enough of windows and decided no matter how frustrated I get I am not going back. 

I have been reading on different programming languages and I am a complete noob in this matter. I have decided to learn C. My reason is for fun not some way of earning a living, and from what I have read it is probably not the easiest choice but in the end I will learn a great deal more about how the computer itself will work.... and get a much more in depth look at how programming logic works. I am saying opposed to a gui based platform. I have a couple books on programming in C and I have emacs as well. I am so new I am clueless as to how I get the program to run or if I need to create a file on my pc somewhere. All I know is when I finish my helloworld program and choose compile nothing happens. I have tried using a.out name and a few others as well as using the -o hello title to name the program. I feel like I just dont know how to use these tools to make it work. Any help? Sorry for the long post but I am so lost. lol

---

### Post by credobyte on 2009-08-11
Install ( if not already installed ) compilers:
```
sudo apt-get install build-essential

```Compile & run:
```
gcc hello.c -o hello
./hello
```"nothing happens" - can we see what you are trying to compile ( source code ) ?

---

### Post by rocky35 on 2009-08-11
/* C Programming for the Absolute Beginner */
//by Michael Vine
#include <stdio.h>
main()
{
   printf("\nC you later\n");
}

This is one that I tried and nothing seemed to happen. Michael Vine and the info bar above his name that is the author and name of the book I am using. I also tried to enter an int above main() and a return below printf but nothing changed so much. I honestly think I am doing somthing wrong with emacs I dunno. but the code you put in above is that just a way to compile and run at the command prompt? that would be sweet.  Thank you for the reply I am really lost and I feel once I get started I will be able to do alot on my own. I am stubborn like that once I get going I will beat myself to death before I give up. lol

---

### Post by WRDN on 2009-08-11
All methods must have a return type. In the case of the main method (the program entry point), you return an integer, as is shown below:

```

#include <stdio.h>

int main()
{
printf("\nC you later\n");
return 0;
}

```

Now, just compile and run the program:

```

gcc main.c -o myProgram
./myProgram

```

---

### Post by credobyte on 2009-08-11
Does this ( instructions below ) result in any errors ( or even worse, in nothing happening ) ?


Create a new dir in your home directory:
```
cd $HOME && mkdir c_temp && cd c_temp
```Create a new C++ source file and paste in your code ( the one you pasted in your previous post ):
```
gedit source.c
```Compile it:
```
gcc source.c -o application
```Run it:
```
./application
```> **WRDN said:**
> All methods must have a return type. In the case of the main method (the program entry point), you return an integer, as is shown below:


```

#include <stdio.h>

int main()
{
printf("\nC you later\n");
return 0;
}

```Now, just compile and run the program:

```

gcc main.cpp -o myProgram
./myProgram

```

int main() **!=** main() ( eg. doesn't require to return anything )

---

### Post by |{urse on 2009-08-11
/* C Programming for the Absolute Beginner */
//by Michael Vine
#include <stdio.h>
int main()  //main needs to be defined as a datatype
{
   printf("\nC you later\n");
return 0;   //main needs to return a value
}

---

### Post by rocky35 on 2009-08-11
is C++ the same as C because I am trying to learn the old C not C+ or C++ I thought these 3 were all different. Is it not possible to use just C anymore? is that my problem? Again sorry but I am new and lost lol

---

### Post by michy99 on 2009-08-11
> **credobyte said:**
> Create a new C++ source file and paste in your code ( the one you pasted in your previous post ):```
sudo gedit source.cpp
```

Why would he open the editor as root?

---

### Post by credobyte on 2009-08-11
> **michy99 said:**
> Why would he open the editor as root?

Ahh, bad habit ( quick */var/www* edits always result in *sudo blah blah* ) :(

---

### Post by rocky35 on 2009-08-11
> **credobyte said:**
> Does this ( instructions below ) result in any errors ( or even worse, in nothing happening ) ?


Create a new dir in your home directory:
```
cd $HOME && mkdir c_temp && cd c_temp
```Create a new C++ source file and paste in your code ( the one you pasted in your previous post ):
```
gedit source.cpp
```Compile it:
```
gcc source.cpp -o application
```Run it:
```
./application
```

int main() **!=** main() ( eg. doesn't require to return anything )
when you say just compile and run the program the only way I know to compile is to hit a selection in emacs that says compile as far as run I thought I just hit ./name of file on my command prompt. Is this correct or should I use nano and do it that way. lol man seems odd but I honestly believe if I can figure out how to get the compile/run to work for me I will be fine at least enough to start to learn.

---

### Post by credobyte on 2009-08-11
> **rocky35 said:**
> when you say just compile and run the program the only way I know to compile is to hit a selection in emacs that says compile as far as run I thought I just hit ./name of file on my command prompt. Is this correct or should I use nano and do it that way. lol man seems odd but I honestly believe if I can figure out how to get the compile/run to work for me I will be fine at least enough to start to learn.

Open your terminal and do all the stuff from there ( for now ) - compilation is the first step towards learning a new language ( eg. you can't just start writing applications without knowing how to compile them ).

---

### Post by WRDN on 2009-08-11
> **credobyte said:**
> Does this ( instructions below ) result in any errors ( or even worse, in nothing happening ) ?


Create a new dir in your home directory:
```
cd $HOME && mkdir c_temp && cd c_temp
```Create a new C++ source file and paste in your code ( the one you pasted in your previous post ):
```
gedit source.cpp
```Compile it:
```
gcc source.cpp -o application
```Run it:
```
./application
```

int main() **!=** main() ( eg. doesn't require to return anything )

True you can return nothing (void) from the main method in C, but promoting good coding practices, you should return an integer- this value allows the user to see if the program exited successfully or not (assuming the developer used standard return values or documented different ones).
Also, for C programs, the source files should have the prefix .c, not .cpp. It shouldn't cause a problem, but I have had issues trying to compile files with the .cpp extension with gcc. When I changed the extension to .c, it compiled without a problem.

---

### Post by rocky35 on 2009-08-11
gcc source.c -o application

Where do I type this to compile? Do I put my home:~/c_temp$ back in the terminal?
After I hit gedit source.c the cursor returns to the next line and is blank. If I 
put that compile command in nothing happens so I typed my home:~c_temp$ and the next 
command and still nothing? Where do I put these commands after the source.c window is
up and I put my code in?

---

### Post by credobyte on 2009-08-11
> **WRDN said:**
> True you can return nothing (void) from the main method in C, but promoting good coding practices, you should return an integer- this value allows the user to see if the program exited successfully or not (assuming the developer used standard return values or documented different ones).
Also, for C programs, the source files should have the prefix .c, not .cpp. It shouldn't cause a problem, but I have had issues trying to compile files with the .cpp extension with gcc. When I changed the extension to .c, it compiled without a problem.

Gee .. How did I managed to add .cpp if we are talking about C ? :D Anyway, I understand your point, however, we should avoid changing *his* source code ( returning a value will not change anything in what he's trying to do at the moment, except, if he sees the exit code ).

> **rocky35 said:**
> gcc source.c -o application

Where do I type this to compile? Do I put my home:~/c_temp$ back in the terminal?
After I hit gedit source.c the cursor returns to the next line and is blank. If I 
put that compile command in nothing happens so I typed my home:~c_temp$ and the next 
command and still nothing? Where do I put these commands after the source.c window is
up and I put my code in?

Put them right into your terminal - don't change anything ( location ). Before typing in gcc command, ensure that you are in c_temp directory.

---

### Post by WRDN on 2009-08-11
As a simple example, you may create the source file HelloWorld.c on your Desktop. To compile it, open the Terminal, and change to your Desktop directory.

```
cd ~/Desktop
```

Now, you can ensure HelloWorld.c exists by listing the files and finding it:

```
ls *.c
```

That will list all files that have the extension ".c".

Finally, to compile it:

```
gcc HelloWorld.c -o HelloWorldProgram
```

And finally, run it:

```
./HelloWorldProgram
```

---

### Post by rocky35 on 2009-08-11
whooohoooooo it worked hehe. Thank you all so much well I am sure I will be asking 90347593578935789375 other questions but for now I am gonna go see what I can learn on my own. Thank you all so much. I gotta say I was hesitant about asking a question on here I am so new I figured I would just be told I should quit. lol thanks again hopefully I will be able to pass the favor on some day, but for now I have a bunch of learning to do. how exciting :)

---

