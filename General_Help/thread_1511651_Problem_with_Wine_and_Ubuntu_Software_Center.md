---
title: "Problem with Wine and Ubuntu Software Center"
date: 2010-06-17
forum: General Help
---

### Post by JLYap on 2010-06-17
Hi everyone, 

I am currently using Ubuntu Netbook Remix 10.04 on an HP mini. I recently tried installing Wine and then decided that I didn't really need it. I've decided to try and remove the program now but it seems like there was some problem with the initial installation process. Now every time I try to remove or install a program through Ubuntu Software Center I get the following message:

Previous installation hasn't been completed

The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.

I am very sure that this error message has to do with the initial installation of Wine as I have not installed anything since through Ubuntu Software Center or otherwise. 

How may I go about 'repairing' this error?

Thanks in advance.

---

### Post by kerry_s on 2010-06-17
accessories-> terminal
type-> **sudo apt-get -f install**

---

### Post by JLYap on 2010-06-17
Thanks! Worked great!

---

### Post by elliotn on 2010-06-17
Ya never interupt the installation, it gave me a headache last time

---

### Post by indunil on 2010-09-27
[B]accessories-> terminal
type-> sudo apt-get -f install[/B]

I use this command, and it is passing this error..

"**E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem**."

when i use "s**udo dpkg --configure -a**"
it gives a black screen with terminal and it automatically log off the current user...

Then if I go to Ubuntu Software Center. It again pass the
"**Ubuntu Software Center - Previous installation hasn't been completed**" ERROR.   :(


Please hep me...

I, using Ubuntu version 10.04.1
and my pc is Intel core two quad 2.4GHz, 2Gb ram and using intel DG35EC m-board with shared vga.

Thanks!

---

