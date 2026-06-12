---
title: "On startup tty1 instead of X console"
date: 2011-03-04
forum: General Help
---

### Post by monoab314 on 2011-03-04
Hi everyone

I want to use Ubuntu to build an information terminal.  This will basically be an X application that displays interesting information.  I has to be lightweight seeing that it is installed on compact flash memory.

I started with a 10.04 command line install and added xserver-xorg.  Please note I am not using a window manager or desktop environment; bare bones X only.  I have created a /etc/init.d/myapp file which can start my application by calling "/usr/bin/xinit ${MYAPP}".  I used update-rc.d to create a symlink in rc2.d that points to /etc/init.d/myapp.  Here is my problem:

On startup the application runs but the system sometimes switches to tty1 (virtual console 1) instead of displaying the X console.  I then have to manually switch to it by pressing Ctrl-Alt-F7.  How can I make it *always* display the X console with my application?  Another thing I noticed is sometimes the X server runs on virtual console 7 and other times on 8.  I though that X starts on the first available console and Ubuntu has 6 ttys configured by default.  So I would expect it to always run on 7, like and ordinary Ubuntu desktop.

Any thoughts would be appreciated!

Cheers,
mono

---

### Post by vivek.pandey on 2011-03-04
well sorry i wont be proving to be of any help but your work sounds interesting...if you dont have any problem can you please give some hint about it and what should i do if even i wanna do something similar to you?
thanx in advance

---

