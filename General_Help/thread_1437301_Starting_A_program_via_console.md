---
title: "Starting A program via console"
date: 2010-03-23
forum: General Help
---

### Post by mike_ldis on 2010-03-23
Hello there!I am new user in ubuntu community. I would like to know if there is anyway of starting a program via console.

---

### Post by akand074 on 2010-03-23
Yeah just type the name of the application directly into the terminal. Watch out though, closing the terminal that the command was given in will also close the application.

---

### Post by DUKANE on 2010-03-23
Yes, you just type the name of the program!

```
firefox
``` for example

If the program is not in your path environment variable, you can go directly to the location and do it that way

```
/usr/bin/perl
``` for example

I know this is by no means a complete answer to your question, but it should get you started.

---

### Post by quadproc on 2010-03-23
A quick addendum: if you want your application to continue running without it being associated with a terminal, type an & at the end of the command line.  Note that this requires an application which can run successfully without a terminal.  For example:
```
gedit Desktop/testfile.txt &
```
The & tells the system to put the job into the background.

You can see such processes by using the ps command, or you can use the System Monitor's Processes tab.  If you need to get rid of such a process then the kill command (or one of its variations) will do.

quadproc

---

### Post by Hermite on 2010-03-25
I have installed Matlab2008r in Ubuntu 9.10. As I have no idea what I am doin I installed it in "filsystem/etc/MatLab2008r". I thought that would be a good place since I saw dirs named "firefox" and "python" and asumed all applications are installed here. But now I cant start matlab. There is no icon to click under "program". I have tried to browse through Matlab's directory to find some kind of startfile (something like .exe for windows) but I dont even know what I am looking for...help

I have found a way to start matlab double clicking on "/etc/MatLab2008r/bin/matlab". Can I do it from program menu?

---

### Post by Amof on 2010-03-25
Most prograsm in Ubuntu are installed in /usr/bin.

When you type:

```
firefox
```

The first place that Ubuntu will look in in /usr/bin.

If you installed it in a diffrent location then you're going to have to tell it where you installed it when you try to run it.

Example:

```
/etc/MatLab2008r*/NAMEOFBINARY*
```

Replace */NAMEOFBINARY* with the actually name of the program's main executable.

---

### Post by mike_ldis on 2010-04-06
> **quadproc said:**
> A quick addendum: if you want your application to continue running without it being associated with a terminal, type an & at the end of the command line.  Note that this requires an application which can run successfully without a terminal.  For example:
```
gedit Desktop/testfile.txt &
```The & tells the system to put the job into the background.

You can see such processes by using the ps command, or you can use the System Monitor's Processes tab.  If you need to get rid of such a process then the kill command (or one of its variations) will do.

quadproc

Quadproc thank you for your advise.This time i am studing o/s for my university.I knew that when you create a prosecc, it is associated with the parent prosecc(which in our case is the terminal).But i had no idea about that information that you gave me!;)

---

