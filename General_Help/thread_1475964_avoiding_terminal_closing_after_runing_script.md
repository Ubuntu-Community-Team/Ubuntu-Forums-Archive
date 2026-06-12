---
title: "avoiding terminal closing after runing script"
date: 2010-05-07
forum: General Help
---

### Post by quimkaos on 2010-05-07
[using Ubuntu 10.04 - Gnome]

I know this is probably a dumb question, but after few years of not using linux i'm back to it and trying to catch up what i already forgot...

i'm trying to make a shell script were when all the commands end or when i interrupt it (using ctrl+c) it wont close my terminal window.

i made a test scrip like this:

#!/bin/sh
echo hi there

and created a launcher by right clicking create  launcher, selected console application, naming it and putting in the command field: sh "<path to file>/test.sh". (without sh at start it wont work)

so how can i avoid shell window closing after running/terminating the script?
and is there any way i can do this by doing something like right click>add new link... i think that in kde it works like that...

---

### Post by steviefordi on 2010-05-07
Not sure if it will work but try changing you shebang to:

```
#!/bin/bash -i
```

---

### Post by quadproc on 2010-05-07
> **quimkaos said:**
> [using Ubuntu 10.04 - Gnome]
...
i'm trying to make a shell script were when all the commands end or when i interrupt it (using ctrl+c) it wont close my terminal window.

I am not exactly sure of what you need to do, but I think that just putting the task into the background will do it.  For example,
```
gedit somefile &
```will return your terminal to a command prompt and you can continue to use the terminal independently of the editor.

However, if your terminal window is killed then the dependent process (the editor) will also be killed.

Another way to do this is to use the bash command coproc.

Yet another way is to start the task without using &, type ctrl-Z in the terminal, type bg.

There are also some shell methods for handling signals; ctrl-C generates a signal.  You can catch signals and take specified action(s) when one occurs.

quadproc

---

### Post by Portmanteaufu on 2010-05-07
If you run:
```
xterm -e 'myprogram; read KEYPRESS'
```
it will launch your program in a new terminal. When your program finishes (or is interrupted), the terminal will move on to the next command: 'read KEYPRESS', which will wait until you hit enter before closing the window. If you wanted the xterm to remain a usable window afterwards, you could make it:
```
xterm -e 'myprogram; /bin/bash'
```

(Caveat: I'm not on my Linux box atm, so I haven't tested this.)

---

### Post by quimkaos on 2010-05-08
mmm my English must be really bad, since i failed to make myself understandable...
-_- my bad...

anyway thanks for the replays!

and I'll try again... will it work?

again... using gnome...
I'm trying to aggregate a few terminal commands in a single file so i don't have to repeat them over and over... and over... so... i made a file were i state the commands and i need to make a link/luncher to run it. I can't just click the script file or drop to a terminal and run it, since it's just an text file. i'll have always have to do something like: "sh <path to the file>". i think this is called something like shell scripting that had (or has) some similarities to ruindows batch files/scripting, thou i think more powerful.

after my "rant" I'm going to post examples! and here they are:
1- open a terminal window and write each line followed by an enter:
```
echo linux
echo is 
echo fun
```
2- create a file named test1.sh in your desktop, open in gedit and paste
```
echo linux
echo is 
echo fun
```
(and no you dont nead #!/bin/sh at the top)

now try to run it...
if you open an terminal window and run it by using "sh <location>/test1.sh" and you can read something like :
```
linux
is 
 fun
```

all is ok but now i want to make a "link" to the script in gnome so i can run it easily. but on gnome (or maybe it's not that much out of the box) you don't have links so i made a launcher with the box options of type = console aplication , name = wtf , command = sh "<location>/test1.sh"... and it woks, but it's so fast i can't even see the terminal window popping up and closing. to test what I'm saying try replacing  the script with a single line: sudo top... it will work like you had manually opened an terminal window and typed sudo top, but will not close the window after pressing "q" or "ctrl+c"...


...

---

### Post by quadproc on 2010-05-08
> **quimkaos said:**
> 
 all is ok but now i want to make a "link" to the script in gnome so i can run it easily. but on gnome (or maybe it's not that much out of the box) you don't have links so i made a launcher with the box options of type = console aplication , name = wtf , command = sh "<location>/test1.sh"... and it woks, but it's so fast i can't even see the terminal window popping up and closing. to test what I'm saying try replacing  the script with a single line: sudo top... it will work like you had manually opened an terminal window and typed sudo top, but will not close the window after pressing "q" or "ctrl+c"...
...
I think that you are looking for a way to keep the script from exiting when it has finished, something like displaying "Press enter to proceed".  To do this, add two lines to the end of your script:
```
echo -n "Press enter to proceed:"
read xx
```The variable xx can actually be named anything that is not being used already.  That variable is just a place to put the input; the input does not get used for anything so it just gets thrown away when the script finishes.  But the script will wait until something which contains the "enter" character is typed in.

quadproc

---

### Post by fwin on 2010-05-08
I am a newbie but i have done a few simple programs like the ones you have shown. At the beginning i had the same issue and adding the following line to the end of my .sh file fixed it.

read -p "press enter"


Now the terminal will only close after you press enter. Also don't forget to change the permissions on your .sh file (using chmod). I hope this helps.

---

### Post by quimkaos on 2010-05-08
thank you

read xx is working but read -p is not
thou what i wanted was to return to the command prompt, it does help...

still doesn't work if i terminate using ctrl-c

---

### Post by quadproc on 2010-05-08
> **quimkaos said:**
> thank you

read xx is working but read -p is not
thou what i wanted was to return to the command prompt, it does help...

still doesn't work if i terminate using ctrl-c
You should be able to catch and handle control-C.  That keypress causes a signal to be sent to the associated process; if that signal is not caught then the process will terminate.  This is what happens now with your script but you can change that.

I suggest looking up the signal entry in the manual
```
man signal
```
There is a lot of info there and you can probably find an appropriate action to handle the signal.

Please note that if you handle control-C yourself then you cannot terminate the process by using that character; you can still kill the process with some of the various kill command options.

quadproc

---

