---
title: "Ubuntu boob here, need help"
date: 2012-04-05
forum: General Help
---

### Post by rolldawg on 2012-04-05
Why cant i delete folders in the 'file system' menu? 
 - how do i delete them?

What packages and other stuff are needed to seamlessly compile and install drivers in vbox? apparently ive been trying for hours just to install my Asus usb n13 (driver rt2780/3070?) networking card to no avail. I tried googling for a fix but i still cant find a working solution. I always end up having either(s) error 1 or error 2 in compiling or installing. :frown:

Any help would be appreciated. :D

---

### Post by Cheesemill on 2012-04-05
Unless you know exactly what you are doing then deleting folders in the / filesystem will almost definitely break your system.

As for installing wireless drivers in VirtualBox, you don't need to. The virtual machine cannot even see your wireless adapter. Instead it sees a virtual wired adapter, the drivers for which are already included in the Linux kernel.

---

### Post by NexusSloth on 2012-04-05
oh!
I see what you mean.
he's not talking about deleting things from a directory, he's talking about deleting things from the "computer" sidepanel (home, filesystem, music, pictures) when you browse the filesystem.
...or something.

from one n00b to another, 
I'd guess you'd just need to log in as root and delete them, or something.
cuz like... the option "remove" is there, it's just greyed out.

otherwise, elaborate? 
:-?

---

### Post by QIII on 2012-04-05
Yes.  Please elaborate on your first sentence.

Also, to take Cheesemill's post further:  It's not only the wireless adapter.   There is a hardware abstraction layer between the virtual machine and your physical hardware.  In general, the vm never sees the physical hardware, but rather an abstraction in Virtualbox.  Virtualbox brokers the communication between those abstract hardware items and the physical ones.  

The drivers for the physical hardware are installed on the host system.

---

### Post by rolldawg on 2012-04-05
Thanks for the reply guys! And yess i do know what i'm doing when deleting stuff. :) Thing is, im a hardcore windows user and i just moved to linux ubuntu cuz of some papers im taking this year. :D

anyways, *how do i login as root?* more like have admin rights to delete stuff on the 'file system' directory. :D

I already know how to setup Vbox - host net connection. Im using my linux guest right now, LOL :P. Since my original wifi card doesnt support monitor mode (yes i know it sounds dodgy, but my papers this sem focuses on network vulnerabilities and how prone they are to brute force attacks - this is for educ purposes =]) i bought a usb wifi card (Asus N-13) which i need my guest OS to recognize and use.

Notes / install run through:
- compilation of rt2780/3070 - errors 1 / 2
- patched it (followed a guide somewhere), compiled it properly w/ no errors?
- tried to install it - errors 1 / 2

Im going to try and fix it again tonight

---

### Post by oldos2er on 2012-04-05
```
sudo -i
``` will give you a persistent root shell. Type **exit** when you're done.

---

### Post by Cheesemill on 2012-04-05
Which version of Ubuntu are you using?

---

### Post by chestycuogth on 2012-04-05
> anyways, *how do i login as root?* more like have admin rights to delete stuff on the 'file system' directory. :D

most admin tasks can be accomplished by using the sudo command in the terminal.
apparently you should avoid logging in as root because 'bad things can happen' but if you do need to login as root then go to the terminal and type in```
sudo passwd root
```
it will then ask you to set a new UNIX password (which is the root password). once the task is completed, logout and go to 'other'
on the login page, type 'root' as the username and whatever your UNIX password is for the password.

---

### Post by Cheesemill on 2012-04-05
> **chestycuogth said:**
> most admin tasks can be accomplished by using the sudo command in the terminal.
apparently you should avoid logging in as root because 'bad things can happen' but if you do need to login as root then go to the terminal and type in```
sudo passwd root
```it will then ask you to set a new UNIX password (which is the root password). once the task is completed, logout and go to 'other'
on the login page, type 'root' as the username and whatever your UNIX password is for the password.

There is no need at all to do this, it is against forum policy to recommend this method at all.
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

Instead just follow oldos2er's instructions above.

---

### Post by F.G. on 2012-04-05
hey, so, just my two cents, but if you want to use usb devices (either internal or external) you need to use the PUEL licence version of virtualbox, not the OSE (opensource) one, don't worry though they are both free. then i think your wifi card should probably be supported by ubuntu.

good luck with your paper.

---

