---
title: "Ability to run Terminal Command as Batch File?"
date: 2011-12-22
forum: General Help
---

### Post by TPReggie on 2011-12-22
Hi All, 

I am pretty new to Linux, but have used Windows for many years. I have a simple question which I hope you can all help me with.  I am running Ubuntu 11:10 on my laptop and have an issue where it will not shut down correctly, this seems to be something many are struggling with. 

I can get my laptop to shutdown correctly by typing sudo shutdown -P now

However I am giving this to my wife and dont want to ask her to type this to shut down every time, Am I amble to create a file and save it to her that will run when selected - similar to a Windows batch file which will run when double clicked? If I can give her something to just double click and have that shutdown the laptop that would be great. 

Hope you can all help. Many thanks in advance. 

Reg.

---

### Post by davethewave83 on 2011-12-22
> **TPReggie said:**
> Hi All, 

I am pretty new to Linux, but have used Windows for many years. I have a simple question which I hope you can all help me with.  I am running Ubuntu 11:10 on my laptop and have an issue where it will not shut down correctly, this seems to be something many are struggling with. 

I can get my laptop to shutdown correctly by typing sudo shutdown -P now

However I am giving this to my wife and dont want to ask her to type this to shut down every time, Am I amble to create a file and save it to her that will run when selected - similar to a Windows batch file which will run when double clicked? If I can give her something to just double click and have that shutdown the laptop that would be great. 

Hope you can all help. Many thanks in advance. 

Reg.

just tried this and it worked. 

Create new file on desktop, edit it and type in sudo shutdown -P now

save and exit

right click the file on the desktop and click properties
under the "Permissions" tab click "Allow executing file" 

double click the file and say "run in terminal" 
this will ask for your sudo password 

you still have to type the password though.

---

### Post by tjoff on 2011-12-22
Write a file with the content:

```
#! /bin/bash
sudo shutdown -P now

```
The first line sets how the file is going to be interpreted, in this case with "bash" which is the default program that interprets what you write on the command line.
Be sure to mark the file as "executable" under properties.
Now double-click the file.

---

### Post by Lars Noodén on 2011-12-22
What you are looking for is called a shell script.  Put a file, [font=Courier New]shutdownnow[/font] in [font=Courier New]/home/TPReggiewife/bin[/font].  
```

mkdir /home/TPReggiewife/bin
touch /home/TPReggiewife/bin/shutdownnow

```

Make it executable, ```
chmod +x /home/TPReggiewife/bin/shutdownnow
```.  Then fill it with the following.  You can use nano or gedit.

```

#!/bin/sh

/usr/bin/sudo /sbin/shutdown -P now

```

Then to make it run without a password, you need to edit [font=Courier New]/etc/[sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html)[/font] and add a line.  Use visudo or nano -w

```

%TPReggiewife ALL=(ALL)NOPASSWD:/sbin/shutdown

```

Ask if anything needs clarification.

---

### Post by TPReggie on 2011-12-22
Wow that was quick:D

Thanks everyone, a few things to try, I have already tried the first one which works great. I will try the others too, to see if I can get it working without a password required. 

Thanks again :)

---

### Post by davethewave83 on 2011-12-22
> **Lars Noodén said:**
> What you are looking for is called a shell script.  Put a file, [font=Courier New]shutdownnow[/font] in [font=Courier New]/home/TPReggiewife/bin[/font].  
```

mkdir /home/TPReggiewife/bin
touch /home/TPReggiewife/bin/shutdownnow

```

Make it executable, ```
chmod +x /home/TPReggiewife/bin/shutdownnow
```.  Then fill it with the following.  You can use nano or gedit.

```

#!/bin/sh

/usr/bin/sudo /sbin/shutdown -P now

```

Then to make it run without a password, you need to edit [font=Courier New]/etc/[sudoers](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html)[/font] and add a line.  Use visudo or nano -w

```

%TPReggiewife ALL=(ALL)NOPASSWD:/sbin/shutdown

```

Ask if anything needs clarification.
thanks, I was trying to figure out the sudoers file for them, but that stuff is over my head :confused:

---

### Post by Lars Noodén on 2011-12-22
> **davethewave83 said:**
> thanks, I was trying to figure out the sudoers file for them, but that stuff is over my head :confused:

The line above should do what you need.  The tutorials and other documentation get quite fancy, but they might make more sense next time you look at them.

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)
[http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sudoers.5.html)

---

