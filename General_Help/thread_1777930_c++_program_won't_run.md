---
title: "c++ program won't run"
date: 2011-06-08
forum: General Help
---

### Post by imu96 on 2011-06-08
I wrote a basic hello world c++ program in code blocks:: IDE but when I ran it a pop-up box popped up saying the permission was denied.

So i went to the file's properties and marked it as an executable file and compiled and ran it again... this time it said:

4: using: not found
6: Syntax error: "(" unexpected.

what the program said was:

#include <iostream>
#include <string>

using namespace std;

int main () {

cout << "Hello World" << endl;

return 0;
}

as you can see there is nothing wrong here no syntax error... so how do i get it to compile??

---

### Post by seawolf167 on 2011-06-08
Did you compile it first?

```
g++ *filename.cpp* 
```then run the program

```
./a.out
```

Also you don't need "#include <string>" in there

---

### Post by imu96 on 2011-06-08
when i type the first thing in i get the error 



g++: /home/imran/Desktop/Untitled1.cpp: No such file or directory
g++: no input files


i then tried just the file name not the directory and i got:

g++: Untitled1.cpp: No such file or directory
g++: no input files

---

### Post by seawolf167 on 2011-06-08
Files in *nix are case sensitive, are you 100% sure that is the correct file name, and that the file has been saved?

Please post the output of (or just type this in and look through it yourself)

```
ls ~/Desktop
```

to get a list of the files on your desktop to ensure you are using the correct name

---

### Post by imu96 on 2011-06-08
ok... i'm sorry i know so little but... what do you mean by *nix files... and... the name is 100% correct... so what exactly am I doing wrong and why can't Code Blocks:: IDE compile the file???

---

### Post by seawolf167 on 2011-06-08
Are you able to manually compile it through the terminal using the g++ command?

```
g++ ~/Desktop/Untitled1.cpp
```

---

### Post by mme oscar on 2011-06-08
[LIST]
[*] the compiler (here g++) is what will transform your code into an executable program
[*] when you ran it it said that it can not find the file containing your code
[*]that means that either the file is not where you think it is, or you don't provide the right filename to the complier
[/LIST]

My guess: maybe you did not save your file in the editor (so your file does not exist) -> save it first and retry to compile.

---

### Post by Mr. Shannon on 2011-06-08
> what do you mean by *nix files...

He means Linux and Unix filenames are case sensitive.

> ...why can't Code Blocks:: IDE compile the file???

Probably for the same reason g++ can't (the file does not exist).

---

### Post by imu96 on 2011-06-08
but the file does exist... i can see it sitting on my desktop... and if the computer really thinks that it doesn't exist... how do i make it realise that it does exist...

also remember that when i try to compile and run from code blocks it says permission denied and then when i get passed that it starts giving me random errors....

the bottom line remains the same: what's the solution???

---

### Post by seawolf167 on 2011-06-08
> **imu96 said:**
> but the file does exist... i can see it sitting on my desktop... and if the computer really thinks that it doesn't exist... how do i make it realise that it does exist...

also remember that when i try to compile and run from code blocks it says permission denied and then when i get passed that it starts giving me random errors....

the bottom line remains the same: what's the solution???

Please save your file, then post the output of

```
ls ~/Desktop
```inside CODE tags

---

### Post by imu96 on 2011-06-09
the results were: 

```
Dropbox        Untitled1       Playlist1       Playlist2
```

---

### Post by seawolf167 on 2011-06-09
> **imu96 said:**
> the results were: 

```
Dropbox        Untitled1       Playlist1       Playlist2
```

Please save and close any editor you are running, then run the following commands, hitting enter after each line and report back with the results

```
cd ~/Desktop
mv Untitled1 Untitled1.cpp
g++ Untitled1.cpp
./a.out
```

---

### Post by imu96 on 2011-06-09
The final result was was: 

```
Hello World
```

which is what the program was supposed to do...

Thanks! Ummm... but how exactly did that work... and how would I compile and run say a visual basic or java file because I have the same permission denied problem with all programming files which i try to compile.

---

### Post by seawolf167 on 2011-06-09
The problem was that the file wasn't named correctly when you were trying to compile it; which is why I added the *mv* command to rename the file.

Give [Geany ]("http://www.geany.org/")a try and see if you have permission problems with it, I use it for my programming needs (when gedit or vi won't suffice) and I really like it, it has built in options to compile and run programs too. You can install it with 

```
sudo apt-get install geany
```It will then appear under the "Programming" menu in the Applications menu on the top panel.

---

### Post by imu96 on 2011-06-09
I got the same errors as before after I made another file with Geany the same as the other except I name it Hello World:

1. ```
./geany_run_script.sh: 5: ./Hello: Permission denied

```

After the above error I renamed the file to Hello and marked the file as executable and got this error... you said I was naming the file wrong... so how do I name it right?

2. ```
./Hello: 4: using: not found
./Hello: 6: Syntax error: "(" unexpected
```

---

### Post by seawolf167 on 2011-06-09
In the middle top of the Geany GUI, there is a button that says "Compile" and "Compile & Run". Try clicking that. 

I'm not sure what this script does
./geany_run_script.sh

And you said you named it Hello World, but you are trying to run "Hello"
./Hello

If you have spaces in the name, the proper compiling & run commands for a file named "Hello World" would be

```
cd /path/to/file
g++ Hello\ World
./a.out
```

where /path/to/file you'll replace with the actual path to the file.

---

### Post by imu96 on 2011-06-09
For some reason it won't let me click on the build or compile button.

> ```
cd /path/to/file
g++ Hello\ World
./a.out
```

When I type in the second command I get:

```
Hello World: file not recognized: File format not recognized
collect2: ld returned 1 exit status

```

---

### Post by seawolf167 on 2011-06-09
Try renaming the file with an extension then so it knows what language it is in

```
mv Hello\ World hello_world.cpp
g++ hello_world.cpp
./a.out
```

---

### Post by imu96 on 2011-06-09
Oh... that worked! Okay, so now I get how to compile and run C++ but what about Visual Basic and Java and C? What are their respective file name extensions? Also, do I have to change g++ to respective compilers for them or does g++ work just fine?

---

### Post by imu96 on 2011-06-09
Actually, I can compile with all compilers and programs when all I have to do is add the file extension to the end of every file name!

---

### Post by seawolf167 on 2011-06-09
> **imu96 said:**
> Actually, I can compile with all compilers and programs when all I have to do is add the file extension to the end of every file name!


Hehe :P glad it is working

---

### Post by imu96 on 2011-06-10
Ya! Thanks! :D

But how do I compile visual basic files because it's got the file extension thingy at the end of its name but it still won't compile. So... how do I get visual basic to compile?

---

### Post by seawolf167 on 2011-06-10
I haven't even looked at VB code in a couple years, take a look at the VB Wiki under Ubuntu [here ]("http://vb.wikia.com/wiki/Running_Visual_Basic_under_Ubuntu_Linux")and see if that helps you out.

---

### Post by axatrikx on 2011-06-10
the problem has to be with the file's name or ur in a diff directory

the file is in the desktop, so run the terminal(the pwd wud be Desktop) 
so just run the command
```
g++ filename.cpp
```

(the filename should be in the correct case)

---

