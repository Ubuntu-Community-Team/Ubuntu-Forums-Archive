---
title: "Grub 2 question"
date: 2010-10-10
forum: General Help
---

### Post by GreatKeyHunter on 2010-10-10
Hi, recently, i had to re-install Win XP on another hard-drive.  Upon trying to re-install grub 2 on my sda, HD, i encountered a problem.  it goes into grub rescue screen when rebooting, in which im stuck.  I dont have a problem booting from sdb since it loads up just fine and it is where i have my Ubuntu installed on.  I was wondering how i can fix it, or what am i doing wrong.  any tips would be highly appreciated.

---

### Post by garvinrick4 on 2010-10-10
> **GreatKeyHunter said:**
> Hi, recently, i had to re-install Win XP on another hard-drive.  Upon trying to re-install grub 2 on my sda, HD, i encountered a problem.  it goes into grub rescue screen when rebooting, in which im stuck.  I dont have a problem booting from sdb since it loads up just fine and it is where i have my Ubuntu installed on.  I was wondering how i can fix it, or what am i doing wrong.  any tips would be highly appreciated.What Operating Systems do you have on sda?

---

### Post by andrewthomas on 2010-10-10
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
 
 
Make sure that you follow the instructions.  
 
If you have any problems, boot from a liveCD and go to 
 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
 
follow the instructions and reply with the results.

---

### Post by GreatKeyHunter on 2010-10-10
> **garvinrick4 said:**
> What Operating Systems do you have on sda?

Win XP,

---

### Post by andrewthomas on 2010-10-10
Set the ubuntu drive to boot first in BIOS 
 
 boot into ubuntu and then 
 
```
 
sudo update-grub

```
 
should pick up the XP

---

### Post by GreatKeyHunter on 2010-10-10
> **andrewthomas said:**
> Set the ubuntu drive to boot first in BIOS 
 
 boot into ubuntu and then 
 
```
 
sudo update-grub

```should pick up the XP

I can boot fine into XP from sdb, its just trying to boot into ubuntu/xp from sda that i am stuck at.  

*** currently reading other pages to see if something works.

---

### Post by andrewthomas on 2010-10-10
Can I ask why you would need to be able to do this?

---

### Post by GreatKeyHunter on 2010-10-10
> **andrewthomas said:**
> Can I ask why you would need to be able to do this?
Just in case my second HD dies out on me.  It has happened to me before.  and since i can't boot into windows without it, it be nice if i could copy the current grub settings from sdb into sda.  -- even though i don't use windows anymore thanks to Ubuntu, its a nice feature to have.

---

### Post by andrewthomas on 2010-10-11
You could set your BIOS boot priority to 1st CD/DVD 2nd winHD 3rd Ubuntu HD then boot a live cd and using the link I posted reinstall grub2 to the windows drive. 
 
after checking the correct partitions with 
 
```
 
sudo fdisk -l

```
 
you would assuming that ubuntu root is on sdb1
 
```
 
sudo mount /dev/sdb1 /mnt

```
again assuming that the windows drive turns out to be sda
```
 
sudo grub-install --root-directory=/mnt/ /dev/sda
 

```
 
Then you could boot off the either drive.

---

### Post by GreatKeyHunter on 2010-10-11
> **andrewthomas said:**
> You could set your BIOS boot priority to 1st CD/DVD 2nd winHD 3rd Ubuntu HD then boot a live cd and using the link I posted reinstall grub2 to the windows drive. 
 
after checking the correct partitions with 
 
```
 
sudo fdisk -l

```you would assuming that ubuntu root is on sdb1
 
```
 
sudo mount /dev/sdb1 /mnt

```again assuming that the windows drive turns out to be sda
```
 
sudo grub-install --root-directory=/mnt/ /dev/sda


 

```Then you could boot off the either drive.

I thought that would work, which it has in the past. but it didn't.   Instead i had both drives go into grub rescue mode. Which, in my case, in order to get out of the rescue mode, i  had to type ls to find out where the boot loader was at, by typing
ls 
ls(hd1,msdos1)/boot/grub (its where my boot files are at)
set prefix=(hd1,msdos1)boot/grub
set root=(hd1,msdos1)
then type normal to get back into the  normal grub 2 menu so i could get back in Ubuntu.  However, there is one problem on the other drive.   which its my fault for not mentioning it either. it says grub_xputs not  found.  Maybe thats whats giving me a hard time getting it to work.

---

### Post by GreatKeyHunter on 2010-10-11
andrewthomas, my friend you are a genius.  apparently the command lines you gave me cleared the error "grub_xputs".  Having both hard drives set to the grub rescue mode enabled me to boot from either drive via command line.  After booting into Ubuntu all i had to do was type , sudo update-grub, then sudo grub-install /dev/sdb and then after another reboot, sudo, update-grub, then sudo grub-install /dev/sda.  Now i can boot from either drive.  Thank you so much i highly appreciated your help.  and thank you garvinrick4 you also help out =D

---

