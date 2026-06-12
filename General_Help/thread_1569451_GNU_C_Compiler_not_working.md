---
title: "GNU C Compiler not working"
date: 2010-09-06
forum: General Help
---

### Post by samishxc on 2010-09-06
Hey guys. So I downloaded Linux just for the heck of it and decided I would try to learn some C in my spare time. So I found a tutorial, and the first code they told me to do was this: 
```
 #include <stdio.h>

int main()
{
  printf( "I am alive!  Beware.\n" );
  getchar();
  return 0;
}

```So I copied it into gedit and saved it as "hello.c". Then I followed the instructions and opened up the Terminal and typed this:
```
gcc hello.c
```And this happens
```
sam@sam-desktop:~$ gcc hello.c
sam@sam-desktop:~$ 

```But when I go back to the file and screw it up by randomly erasing characters, it tells me what I did wrong.

I have no idea why this won't work. I also am pretty bad at some of this complexer stuff (to me it's complex) and anywhere I look online elsewhere people talk as if everybody knows how to do these things.

---

### Post by lloyd_b on 2010-09-07
By default, gcc will create an executable named "a.out" unless you explicitly tell it to do otherwise.  So, open a terminal window, and type "./a.out", and it should execute the program you compiled (compiling a program doesn't automatically execute it, it just creates the executable).

If you want to create the executable under another name, use the "-o" option.  For instance:```
gcc -o hello hello.c
```will compile hello.c, and create an executable named "hello" in the current directory.  Then type "./hello" to run it.

I recommend installing the build-essential package if you haven't already done so - it contains a lot of things that will be required if/when you move on to making more complex programs. The command to do this is ```
sudo apt-get install build-essential
```.

Lloyd B.

---

### Post by samishxc on 2010-09-07
Thank you so much! You don't know how frustrating that was. Not a single tutorial actually explained how to get the executable.

---

### Post by GregBrannon on 2010-09-07
Uh, oh.  You've opened the door for all those in the wings waiting (dying!) to say, "I told you it's important to learn how to program from the command line."

Continue to study programming and ask questions, but I recommend you use the Programming Talk area for questions like these.  Good luck.

---

