---
title: "xrdp and program crashing"
date: 2010-11-17
forum: General Help
---

### Post by okey666 on 2010-11-17
My school recently bought the "computing club" our own server. This runs virtual machines on VMWare Server and so allows us to run whatever operating systems we want, and install any programs we want. We have a Ubuntu 10.10 Desktop (x86) virtual machine which we use as our main system. We want multiple users to access the same vm simultaneously, so I installed xrdp and set it up so users could use Remote Desktop on any machine on the 100% Windows school network to access it. This works very well and seems to be stable apart from some strange problems which seem to be related to the way the sessions are managed by xrdp and sesman.

The first one of these problems is that the .Xauthority file was not present on remote sessions, so gksudo would not run as it could not find the file to copy to /tmp. I managed to fix this by running xauth and generating a new magic cookie (not that I really knew what I was doing). Gksudo runs now, but I thought I would include this problem anyway incase it gives any hints to the heart of the problem.

The second problem we are having is by far the strangest. Like the first problem, it too only seems to happen when using a remote session. Performing a specific action in some programs will cause them to crash. They print an error message which I will quote when I am at school and able to use the machine, but its something to do with a "free()" command being called when the memory was not allocated.

The following programs seem to have this problem (that I know so far):
[LIST]
[*]system monitor - crashes on startup
[*]java - eclipse - crashes on change perspective and closing a tab
[*]java - android sdk manager - various actions
[*]scite - opening a file
[/LIST]
All these things crash with exactly the same error message.

Anyone got any ideas? It makes the system really quite frustrating to use!

---

### Post by okey666 on 2010-11-18
The exact error given by scite when crashing is:
```
*** glibc detected *** gnome-system-monitor: free(): corrupted unsorted chunks: 0x0a098708 ***

```

I have also noticed that the user manager does not work; the buttons do nothing.

---

### Post by zdea on 2010-11-27
I've experienced the same behavior. I was never able to get that error message though as I can't even start a terminal under xrdp to view stderr or stdout from the crashing programs.

I've submitted a bug report (bug 682279) on launchpad.

---

### Post by okey666 on 2010-11-28
I am very interested to see if anyone can come up with a fix for this, but for now we have switched to Fedora which seems to work ok with xrdp. However, I would love to use Ubuntu at school simply because of its greater support and my always pleasant experience of using it at home.

---

### Post by dabubu on 2011-09-14
I've had the same problem for months now. 

XRDP causes a number of Gnome programs to crash.

The story so far:

Disk utility always crashes .

System monitor always crashes .

Nautilus always crashes when files and directories are displayed in "List View" (but not Icon View) and then you click, or press Enter, to go into a directory.

It's a pity. It would be an almost perfect solution for me to connect with no hassle from my work laptop (I have to use Windows 7) to my Ubuntu computers at home.

---

### Post by dabubu on 2011-09-14
I've just had a bit of luck.....

I changed the desktop background theme to Clearlooks, and all of the problems I had (see my post above) went away (needed to log out and in again though).

I remember seeing this suggestion somewhere else, but wrongly didn't give it any credit. I can't remember where I saw it - so I can't link back. Apologies. 

"Clearlooks" doesn't look as nice as some of the other themes, but so what, I now have all of my functionality back.

I'd still say it's a bug not being able to use the other themes though.


ANOTHER UPDATE: everything works except for the System Monitor...!

---

