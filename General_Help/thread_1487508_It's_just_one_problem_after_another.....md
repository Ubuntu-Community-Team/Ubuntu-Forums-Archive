---
title: "It's just one problem after another...."
date: 2010-05-19
forum: General Help
---

### Post by pr0t3g3 on 2010-05-19
I can't install programs via the terminal... but I WANT to ... My problem is:

Once I give it a command to install a program it prompts me for my password... ok... 
but when I type it in NONE of the keys I press register on the screen... I don't want alternatives I just want to fix this so It will work .... help?


Edit:  When I press enter it just closes the terminal out!

---

### Post by Agent ME on 2010-05-19
That's normal. Type your password out, and then press enter. It's similar to how many other places show asterisks instead of your password as you type it, except it just doesn't even do asterisks.

---

### Post by SushiR on 2010-05-19
That's normal behaviour. Just type in your password and hit Enter. That's it.

---

### Post by mmmichael on 2010-05-19
That's just the default behavior of the terminal. Passwords don't appear when you type them. Just type it and hit enter.

---

### Post by pr0t3g3 on 2010-05-19
> **Agent ME said:**
> That's normal. Type your password out, and then press enter. It's similar to how many other places show asterisks instead of your password as you type it, except it just doesn't even do asterisks.

T_T that didn't work it came up with nothing...

---

### Post by amite on 2010-05-19
not printing of anything doesn't mean ur terminal is not accepting ur password.In most of linux distro u won't find any printed character for password ,even on ubuntu u can find this thing when u login on text console.

it saves u from people around u to know size of ur password and so it would more difficult for them to guess ur password........isn't it?

---

### Post by pr0t3g3 on 2010-05-19
> **amite said:**
> not printing of anything doesn't mean ur terminal is not accepting ur password.In most of linux distro u won't find any printed character for password ,even on ubuntu u can find this thing when u login on text console.

it saves u from people around u to know size of ur password and so it would more difficult for them to guess ur password........isn't it?
I understand _-_ but it didn't DO anything when I hit enter

---

### Post by mmmichael on 2010-05-19
> **pr0t3g3 said:**
> I understand _-_ but it didn't DO anything when I hit enter

Let's back up a bit. What command did you type that asked for a password?

---

### Post by pr0t3g3 on 2010-05-19
> **mmmichael said:**
> Let's back up a bit. What command did you type that asked for a password?
sudo apt-get install python

---

### Post by mmmichael on 2010-05-19
Python should already be installed if you're using Ubuntu. Just type the word python and hit enter and you should go into a python shell.

As for the password problem, if you typed your password (which doesn't appear on the screen as you type it) and hit enter, you should have gotten a message that python was already installed.

---

### Post by pr0t3g3 on 2010-05-19
> **mmmichael said:**
> Python should already be installed if you're using Ubuntu. Just type the word python and hit enter and you should go into a python shell.

As for the password problem, if you typed your password (which doesn't appear on the screen as you type it) and hit enter, you should have gotten a message that python was already installed.
:shock: what the hay is wrong with my pc then.....

---

### Post by elliotn on 2010-05-19
type python in terminal and post the output.

---

### Post by pr0t3g3 on 2010-05-19
> **elliotn said:**
> type python in terminal and post the output.
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.

---

### Post by mmmichael on 2010-05-19
> **pr0t3g3 said:**
> I understand _-_ but it didn't DO anything when I hit enter

When you say it didn't do anything, do you mean that it just returned a shell prompt, or that it just froze?

---

### Post by pr0t3g3 on 2010-05-19
> **mmmichael said:**
> When you say it didn't do anything, do you mean that it just returned a shell prompt, or that it just froze?
when I typed my pass and hit enter it closed out....

---

### Post by pr0t3g3 on 2010-05-19
anthony@anthony-laptop:~$ sudo apt-find install python
[sudo] password for anthony:

and then it closes out on me... i type my pass and hit enter.. boom gone

---

### Post by ryan858 on 2010-05-19
> **pr0t3g3 said:**
> I understand _-_ but it didn't DO anything when I hit enter
It didn't do *anything*?? Not even an error? It just blinks the cursor, or what?

edit: Oh, so it goes back to the shell prompt?

Does sudo work with other programs? Or when installing other programs with apt?

---

### Post by mmmichael on 2010-05-19
> **pr0t3g3 said:**
> when I typed my pass and hit enter it closed out....

It closed the terminal window? That's odd! 
Does your computer have enough resources to run Ubuntu? Did you have other apps running?

Try going to the console: hit ctrl + alt + F2 together. Then log in and see if the behavior is the same. (you can hit ctrl + alt + F7 to get back to your desktop environment)

---

### Post by pr0t3g3 on 2010-05-19
> **ryan858 said:**
> It didn't do *anything*?? Not even an error? It just blinks the cursor, or what?
it closed out on me bro....

i'm not sure why... but i'm worried.. if the ubuntu I have can't do something as simple as install a program via terminal I'm in trouble... I came to ubuntu solely for stuff like that... to use it and learn all about it... but it requires me becoming familiar with installation and stuff like that.. .I don't want to give up and go back to windows... half the reason I switched to this operating sytem was to get away from instability.. I don't want to relive that here...

---

### Post by pr0t3g3 on 2010-05-19
aw man... my pc restarted....what did you make me do with that ctrl alt f2


... hmm it's a alot faster than before when I restarted... why is this... ?


Excellent it works!  Thank you.  one more thing. Where do I find python


edit:  it seems I had alot of other programs tearing at my 'resources'.  It couldn't even handle going into a full screen terminal; so it restarted.

---

### Post by 11cerealkiller26 on 2010-05-19
> **pr0t3g3 said:**
> I can't install programs via the terminal... but I WANT to ... My problem is:
 
Once I give it a command to install a program it prompts me for my password... ok... 
but when I type it in NONE of the keys I press register on the screen... I don't want alternatives I just want to fix this so It will work .... help?
 
It is normal when you type a password in terminal not showing any characters. when it prompts for password..just input and press enter key...by the way, make sure your password is correct.

---

### Post by pr0t3g3 on 2010-05-19
I have a new problem .... DX I can't find python!!!!


where do I launch python from??

---

### Post by ankit singh on 2010-05-19
I think u have problems with synaptic, open synaptic and mark reload to the left on top.

---

### Post by mmmichael on 2010-05-19
> **pr0t3g3 said:**
> Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.

When you posted the above, that was python. It was followed by >>>.
That's the python prompt.
If you want a graphical program to launch python try
 ```
sudo apt-get install idle
```

---

### Post by pr0t3g3 on 2010-05-19
> **ankit singh said:**
> I think u have problems with synaptic, open synaptic and mark reload to the left on top.
I'm starting to lose it here... where do I find synaptic and where do I find python...

---

### Post by pr0t3g3 on 2010-05-19
> **mmmichael said:**
> When you posted the above, that was python. It was followed by >>>.
That's the python prompt.
If you want a graphical program to launch python try
 ```
sudo apt-get install idle
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  firefox-3.5-branding
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  blt idle-python2.6 python-tk tcl8.5 tk8.5
Suggested packages:
  blt-demo tix python-tk-dbg tclreadline
The following NEW packages will be installed:
  blt idle idle-python2.6 python-tk tcl8.5 tk8.5
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,632kB of archives.
After this operation, 13.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main tcl8.5 8.5.8-2 [1,570kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main tk8.5 8.5.8-1 [1,128kB]  
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main blt 2.4z-4.2 [1,617kB]   
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main python-tk 2.6.5-0ubuntu2 [25.8kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main idle-python2.6 2.6.5-1ubuntu6 [287kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main idle 2.6.5-0ubuntu1 [2,752B]
Fetched 4,632kB in 16s (282kB/s)                                               
Selecting previously deselected package tcl8.5.
(Reading database ... 146517 files and directories currently installed.)
Unpacking tcl8.5 (from .../tcl8.5_8.5.8-2_i386.deb) ...
Selecting previously deselected package tk8.5.
Unpacking tk8.5 (from .../tk8.5_8.5.8-1_i386.deb) ...
Selecting previously deselected package blt.
Unpacking blt (from .../archives/blt_2.4z-4.2_i386.deb) ...
Selecting previously deselected package python-tk.
Unpacking python-tk (from .../python-tk_2.6.5-0ubuntu2_i386.deb) ...
Selecting previously deselected package idle-python2.6.
Unpacking idle-python2.6 (from .../idle-python2.6_2.6.5-1ubuntu6_all.deb) ...
Selecting previously deselected package idle.
Unpacking idle (from .../idle_2.6.5-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up tcl8.5 (8.5.8-2) ...

Setting up tk8.5 (8.5.8-1) ...

Setting up blt (2.4z-4.2) ...

Setting up python-tk (2.6.5-0ubuntu2) ...
Setting up idle-python2.6 (2.6.5-1ubuntu6) ...

Setting up idle (2.6.5-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by pr0t3g3 on 2010-05-19
nothing launched.... well the shell .. at least i think thats the shell that launched ... T_T i'm a complete noob... I don't care though... please teach me more!!!

---

### Post by mmmichael on 2010-05-19
OK, you installed a program using the terminal. 
Look under Applications and see if there is a submenu for Programming. If so, idle should be there. It is an IDE for programming in python. 
If you don't have the programming submenu you can add it by going to System>Preferences>Main Menu.

---

### Post by ankit singh on 2010-05-19
thats done, python is installed. Synaptic is in System-> administration. Use this for installing any program.The earlier problem u said of terminal bashing out was because of another synaptic application was running in background via terminal.Remember u cannot run 2 instances of packetmanager at same time

---

### Post by mmmichael on 2010-05-19
The next step is to google "python tutorial". There are many to choose from.

---

### Post by pr0t3g3 on 2010-05-19
Heheh... I was so excited I didnt think to check applications to see that theres a new bar:  Programming :)  Thank you!

---

### Post by pr0t3g3 on 2010-05-19
> **mmmichael said:**
> The next step is to google "python tutorial". There are many to choose from.lmao...right your done eh?  yeah.. google WOULD be my best friend... if it had the answers I need... sometimes I have to hunt them down to places that the answer's by rights should not even be located at...  most of the time it comes down to me messing with it till I figure it out... .  thanks you guys saved me alot of time compared to what might have happend  if i tried on my own

---

### Post by mmmichael on 2010-05-19
Check out this page:
[http://wiki.python.org/moin/BeginnersGuide/NonProgrammers]("http://wiki.python.org/moin/BeginnersGuide/NonProgrammers")
Got to go, I have to get up for work in an hour.

---

### Post by elliotn on 2010-05-19
one thing to know is that u can launch any program via terminal, eg```
gimp
``` would launch gimp  ```
audacious
```would lauch audacious etc. If a program isnt installed terminal would tell u

---

### Post by ankit singh on 2010-05-19
u can launch any program from terminal. if any program is not install and u type it in terminal ,it say as following.For example i want to launch program nexuiz but i have not installed it and so  when i write it in terminal, i will get 

> 
ankit@ankit-desktop:~$ nexuiz
The program 'nexuiz' is currently not installed.  You can install it by typing:
sudo apt-get install nexuiz
ankit@ankit-desktop:~$ 
here u can see it gives me message the pogram is not installed and it also gives the me code to install it. here u can see the code  > sudo apt-get install nexuiz .
u write this code in the terminal and install it.

---

### Post by ankit singh on 2010-05-19
> **elliotn said:**
> one thing to know is that u can launch any program via terminal, eg```
gimp
``` would launch gimp  ```
audacious
```would lauch audacious etc. If a program isnt installed terminal would tell u

i completed it

---

### Post by pr0t3g3 on 2010-05-22
Thanks you've all been very helpful.

---

