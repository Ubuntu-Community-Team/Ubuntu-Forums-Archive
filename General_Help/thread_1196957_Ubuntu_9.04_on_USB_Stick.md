---
title: "Ubuntu 9.04 on USB Stick"
date: 2009-06-25
forum: General Help
---

### Post by BJinMontreal on 2009-06-25
I have tried a few times to install the 9.04 to my Kingston 16Gb USB Stick - but on startup, the initial splash screen seems to be displaying the old Ubuntu 8.10 graphic - but that is not my problem.
Once the stick has complied all that needs to be compiled (I am guessing because I have no idea what it is doing - it takes so long) I am left with a text-based screen prompt which I am not sure what to do with.  I can typr help and receive a list of commands that I could run - but I have no clue what most of these do.  I thought I would load the program to the stick, and when I used it I would have the same, yet slower graphical environment that I get on my desktop.

Can someone please direct me to an install guide that will give me the graphical environment I want, or point me to a distro that will.

---

### Post by Mighty_Joe on 2009-06-25
You don't tell us how you installed 9.04.  If you used the usb-creator from the Live CD, there's [this problem]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") which affects you if you try to create a persistent partition larger than 2GB. 
I take it you had a previous 8.10 install on that drive?  
[This post]("http://ubuntuforums.org/showthread.php?t=1193680") pretty much covers every possible way to install Ubuntu (or any Linux distro) to flash drive.  My post in that thread has links to the procedure I used to do a full install.

---

### Post by BJinMontreal on 2009-06-25
> **Mighty_Joe said:**
> You don't tell us how you installed 9.04.  If you used the usb-creator from the Live CD, there's [this problem]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/321544") which affects you if you try to create a persistent partition larger than 2GB. 
I take it you had a previous 8.10 install on that drive?  
[This post]("http://ubuntuforums.org/showthread.php?t=1193680") pretty much covers every possible way to install Ubuntu (or any Linux distro) to flash drive.  My post in that thread has links to the procedure I used to do a full install.

Sorry - Yes I tried the USB Creator from the live cd and thinking that I had all that extra room set the persitent partition to about 11 GB.  I'll check out your install directions and see if it works for me.

---

### Post by BJinMontreal on 2009-06-25
Actually I wasn't getting any errors in the creation process - as it created the installation ok with no errors - it was only when I tried to use the USB that I noted the malfunction.

---

### Post by BJinMontreal on 2009-06-25
> **BJinMontreal said:**
> Actually I wasn't getting any errors in the creation process - as it created the installation ok with no errors - it was only when I tried to use the USB that I noted the malfunction.

I reformatted the stick and reinstalled with usb-creator using 3.5 GB for persistence.  Same result - no graphical interface:

BusyBox v1.10.2 (ubuntu 1:1.10.2-1ubuntu6) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs):

I have no idea where to go from here ... except maybe another distro that will give me a graphical desktop that I want and know how to use.  Isn't the whole talk about putting a distro on a stick supposed to be so you can take your work with you?  I can't work with this - unless there is something else that needs to be done from the prompt before the stick is useable.

---

### Post by Mighty_Joe on 2009-06-26
> **BJinMontreal said:**
> I reformatted the stick and reinstalled with usb-creator using 3.5 GB for persistence.  


As I said before, there is a known problem using the usb-creator to make a persistence file larger than 2GB. 
Did you install Grub to the USB drive?  
Did you try a full install or one of the other options in the post I linked (UNetbootin , for example)?

---

### Post by BJinMontreal on 2009-06-26
> **Mighty_Joe said:**
> As I said before, there is a known problem using the usb-creator to make a persistence file larger than 2GB. 
Did you install Grub to the USB drive?  
Did you try a full install or one of the other options in the post I linked (UNetbootin , for example)?

Not sure - I assumed the install would have put GRUB on the stick.

---

### Post by Mighty_Joe on 2009-06-26
I retract the comment about Grub.  The usb-creator would install Grub.  
Try a full install using the directions I linked to in the other topic.  It works fine for me.

---

### Post by BJinMontreal on 2009-06-26
> **Mighty_Joe said:**
> I retract the comment about Grub.  The usb-creator would install Grub.  
Try a full install using the directions I linked to in the other topic.  It works fine for me.

Thanks Joe,
You've been very helpful.  I'm going to try it with Netbootin and see if that works. Do you know if I can put more than one distro on the stick - since it's so large (16 GB)?

---

### Post by Gen2ly on 2009-06-26
Probably off-topic so feel free to ignore :D but installed arch on a usb stick, see post below.  Also on post there's a link to a person that installed ubuntu on a usb stick.

---

### Post by Mighty_Joe on 2009-06-26
> **BJinMontreal said:**
> Do you know if I can put more than one distro on the stick - since it's so large (16 GB)?

I've seen people [say it's possible]("http://www.justlinux.com/forum/showthread.php?threadid=150078").  It looks non-trivial.

---

