---
title: "boot ubuntu problem"
date: 2011-03-11
forum: General Help
---

### Post by anifort on 2011-03-11
Dear all,
When i boot my computer i get the screen where i have to choose between linux / windows. Now in that list there are two options for Linux and both have a recovery mode as well. Out of a sudden, the very first option in the list (which is the one that it auto selected if the 10 seconds pass) when selected gives me the following error:
kernel panic - not rsyncing: VFS: unable to mount root fs on unkown-block(0,0)
Pid: 1, comm: swapper Not tainted 2.6.35-27-generic #48-Ubuntu

Any solution to that?

---

### Post by vivek.pandey on 2011-03-11
for the 10  seconds thing you need to choose an os before 10 seconds...you can do by using your arrow keys to move from one to other and then enter to choose one. once you have pressed any key after countdown started, countdown stops.
try the second kernel and see if you are getting any error

---

### Post by anifort on 2011-03-11
> **neo_aryan said:**
> for the 10  seconds thing you need to choose an os before 10 seconds...you can do by using your arrow keys to move from one to other and then enter to choose one. once you have pressed any key after countdown started, countdown stops.
try the second kernel and see if you are getting any error
Yes i know how to choose a different os and stop the counting. the second kernel works just fine, but the thing is that i want the first one to run fine because sometimes i reboot remotely and i want it to go again into the ubuntu os. Since i am not there i want it to be automatically but with my issue the first kernel(i dont know if thats the right term to call it) has a problem

---

### Post by jaayll on 2011-03-11
You can change the grub to boot by default to the 3rd line in the kernel list.
Open gnome-terminal
~$ sudo gedit /etc/default/grub
It will ask your root password before opening gedit.
Edit this line
GRUB_DEFAULT= (0 is first line, 1 is second, etc.)
You can change this line also
GRUB_TIMEOUT= (if you want to wait less than those 10 secs)
Close gedit and update the grub with:
~$ sudo update-grub2
I hope it helps you.

---

### Post by anifort on 2011-03-11
> **jaayll said:**
> You can change the grub to boot by default to the 3rd line in the kernel list.
Open gnome-terminal
~$ sudo gedit /etc/default/grub
It will ask your root password before opening gedit.
Edit this line
GRUB_DEFAULT= (0 is first line, 1 is second, etc.)
You can change this line also
GRUB_TIMEOUT= (if you want to wait less than those 10 secs)
Close gedit and update the grub with:
~$ sudo update-grub2
I hope it helps you.

It is really helpful (ill try it later). This is a problem bypass! :) what is the real solution though.. how can i fix this? what if the other kernel dies as well? then there is no way for me to login! can i reset the first one? Thanks for the help!

---

