---
title: "Please help mdcrack setup"
date: 2010-03-10
forum: General Help
---

### Post by perl3z on 2010-03-10
Please help to install the program
I do not know what the problem

Wich kind of cpu endianness (default: little) ? [little/big]
read: 84: arg count
Compiling and installing mdcrack, please wait a few minutes ..... src/NTLM1/core3.c: In function ‘crack_NTLM_core3’:
src/NTLM1/core3.c:53: warning: incompatible implicit declaration of built-in function ‘exit’

[http://mdcrack.df.ru/download/mdcrack-1.2.tar.gz](http://mdcrack.df.ru/download/mdcrack-1.2.tar.gz)


[IMG]http://www3.0zz0.com/2010/03/10/12/815521756.gif[/IMG]






2



[IMG]http://www3.0zz0.com/2010/03/10/12/709071715.gif[/IMG]

---

### Post by perl3z on 2010-03-10
:popcorn::popcorn::popcorn:


:)-

---

### Post by perl3z on 2010-03-10
:popcorn::popcorn::popcorn::popcorn::popcorn:

---

### Post by hydrox24 on 2011-08-20
I am sorry to be dragging up an old thread but I encountered this issue too and I would really like to know the answer as it was sad that I had to go to windows to crack an md4 hash easily.
Would also be nice if someone with the experience could post a response on what that "endiannes" thing means. Mostly would be good to have a decent tutorial on how to compile the thing though. If you don't have the people skills to do that then could you atleast package the thing into a basic 32-bit .deb?
hopefully this will be solved soon

---

### Post by hydrox24 on 2011-08-20
OK, so I have done some more research into this and have found that the dev's of this app haven't supported linux since the 1.2 version (now up to 1.8) and have focused on the windows platform. however, the latest EXE runs buetifully under WINE.

Here's how to use it:

[LIST=1]
[*]type ```
 wine cmd 
``` into a terminal window in linux. This will bring up the CMD application in the same window.
[*]Move the EXE of MDCrack (something like MDCrack-sse.exe) to the "Program Files" directory using a normal linux terminal or nautilus (it's under ~/.wine/drive_c/)
[*]move into the Program files directory using the wine CMD. Try using the "CD" command to change directory and the "DIR" command to list contents.
[*]Then just type the following: ```
 MDCrack-sse.exe --help 
```
[*]Now that you have a help pane just use like normal
[*]E.G: ```
 MDCrack.exe --algorithm=MD4 <place MD4 hash here>
```
[/LIST]

Hopefully this helps!

Here is a site that may help a little more too:
[http://www.airdemon.net/passwordcracking2.html#For%20BackTrack4%20users:](http://www.airdemon.net/passwordcracking2.html#For%20BackTrack4%20users:)

---

### Post by lisati on 2011-08-20
As well as this being an old thread relating to Windows software, there are linux-friendly alternatives, and some software can be misused.

---

