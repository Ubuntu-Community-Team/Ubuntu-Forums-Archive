---
title: "computer boots but can't log on"
date: 2009-11-20
forum: General Help
---

### Post by admiralbaty on 2009-11-20
running 9.10 on a i386 dell. i added a user from the administration menu, logged off, and now i can't get into either account. the computer boots normally, but login screen now only has a blank black box where user selection would be. also, the universal access button shows, and it works when i click on it.  

when i try to shut down or reboot, a box pops up saying gdm-simple-greeter.desktop is still running, and it is listed as not responding, but when i switch to command line interface and run top i can't see it there to know the pid to kill it. nor does "which gdm*" return anything.

how do i fix this?

---

### Post by LinuxBob on 2009-12-18
Same problem on my Dell 1505n laptop.


Seriously folks, this has got to be fixed

---

### Post by john newbuntu on 2009-12-19
Hit Ctrl+Alt+F2 to get into command mode, login and run the "df -h" command to see if you have filled up the root filesystem(/). If so, delete a few unnecessary files.
If you are using Gnome:
sudo /etc/init.d/gdm stop
dpkg-reconfigure gdm
sudo /etc/init.d/gdm start
Then get back to gdm using Ctrl+Alt+F7 and see if things are better.

---

### Post by humpiedumpie on 2010-02-03
I have exactly the same problem after using 9.10 for the last few months without problem at all. 
I left the computer on overnight and probably it tries to go into power saving mode or something, but the next
morging I have the problem. The commands suggested does not provide a solution. I appreciate any other 
attempts or tips to fix this. I am using Toshiba Satellite P100-442.

Thank you so much,

---

### Post by humpiedumpie on 2010-02-28
The problem is gone after I re-installed Ubuntu 9.10 after backing up the home folder and restoring it. However, now, my wireless is unstable (encrypted or not). 

Tx,

---

### Post by tkershenbaum on 2010-03-07
> **admiralbaty said:**
> running 9.10 on a i386 dell. i added a user from the administration menu, logged off, and now i can't get into either account. the computer boots normally, but login screen now only has a blank black box where user selection would be. also, the universal access button shows, and it works when i click on it. 
 
when i try to shut down or reboot, a box pops up saying gdm-simple-greeter.desktop is still running, and it is listed as not responding, but when i switch to command line interface and run top i can't see it there to know the pid to kill it. nor does "which gdm*" return anything.
 
how do i fix this?
 
This has just happened to me...I added a user, logged off and now have a blank box where the user selection would be. Has anybody been able to resolve this without backing up/reinstalling? I very much appreciate any help.

---

### Post by tkershenbaum on 2010-03-08
I was able to solve this in my case. The problem had something to do with the user I had added just prior to the problem occuring...I believe it stemmed from a character in the name that "broke" the menu, the character being the "&" symbol (my guess?). I rebooted into the recovery menu and selected "Drop to root shell prompt". I then typed "userdel -r loginname". After that the problem was gone. For a newbie that was a very difficult problem to solve...

---

