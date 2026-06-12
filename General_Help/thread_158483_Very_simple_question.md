---
title: "Very simple question"
date: 2006-04-11
forum: General Help
---

### Post by altainta on 2006-04-11
I want to know how to hide (totally background) a program

i know that 
**command &**
but it doesn't works for me
i want a better way what happen when i use the
**perl ./ok.pl &**
it hide the window for a second but than it start output of the program on the screen which makes the screen ugly. I want a clean prompt and the program running in background. Every thing of the program should be hidden. For closing the programm i will only use kill command.
please help me i am searching this thing for a long time but no one replied and helped me.](*,) :(

Example : 
In dos we can't multitask
but i heared that in CLI (unix) u can multi task if yes than how come i will run a many program from command line but can still be able to use the command line.
I want a solution on console not on GNOME OR KDE. The problem is related to non-GUI system.

---

### Post by tedius on 2006-04-11
You need to root the output to someplace other than your terminal.

You can root all stdout to a file like this;
```
command > output.txt
```
That will put all the standard output into the file ouput.txt

If you want to root error too, you need to root stderr to stdout like this
```
command > output.txt 2>&1 &
```
Here the number 1 and 2 mean stdout and stderr respectevely.

The finale thing you can do if you are not interested in the output at all, then you can root it to /dev/null
```
 command > /dev/null 2>&1 &
```

Hope this helps.

---

### Post by altainta on 2006-04-11
wow gr8 so quick reply i though i will get the answer in 2 days!
I am shocked.
I used to batch program in dos and know this > but didn't tried it in linux.
Thx dude thx a lot for the help u did i will try it soon.

PS: hey its working thx dude working like a charm
**perl ok.pl > /dev/null 2>&1 &**

---

### Post by xenmax on 2006-04-11
> but i heared that in CLI (unix) u can multi task if yes than how come i will run a many program from command line but can still be able to use the command line.
You can have as many instances of gnome-terminal running as you wish.. you can also try using multiple Tabs feature in gnome-terminal...

---

### Post by altainta on 2006-04-11
[QUOTE=xenmax]You can have as many instances of gnome-terminal running as you wish.. you can also try using multiple Tabs feature in gnome-terminal...[/QUOTE]

I want that feature in command line (total text mode no gnome system installed)
if it is possible than can u tell me how to get that shell ? Any command ?

---

### Post by Gustav on 2006-04-11
you can check the screen command (man screen) that should do what you want (if I understood you correctly)

---

### Post by xenmax on 2006-04-11
This might help: [http://www.dbaoncall.net/references/ref_linux_console.html](http://www.dbaoncall.net/references/ref_linux_console.html)

---

### Post by altainta on 2006-04-11
actually i never understood the screen command can u tell me abt the screen command and how to use it under perl program ?
Also is there any way to autologin and auto execute program without interaction of user

(in gui & also in text mode)

btw thx xenmax for the tip but i already know abt virtual thing but i want to use only one mode i can't use this for a multimode (suppose if i want 20 program instances in background  than ?)

---

