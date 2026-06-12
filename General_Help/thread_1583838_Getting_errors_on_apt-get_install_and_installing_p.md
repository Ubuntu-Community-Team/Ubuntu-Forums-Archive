---
title: "Getting errors on apt-get install and installing programs"
date: 2010-09-28
forum: General Help
---

### Post by TehThird on 2010-09-28
Hi. I have a boring problem. I tried to get wlan working on my asus eee 1000H after installing ubuntu 10.4 netbook edition on it. I dont remember exactly what I did, i copied some commands and pasted them in xterm. Wlan got working, but i got an error on every time i use apt-get now.

Error msg as follows (sorry for the norwegian):

Loading new rt2860sta-1.8LK DKMS files... 
 
Loading tarball for module: rt2860sta / version: 1.8LK 
 
Loading /usr/src/rt2860sta-1.8LK... 
Loading /var/lib/dkms/rt2860sta/1.8LK/2.6.27-7-generic/i686... 
Creating /var/lib/dkms/rt2860sta/1.8LK/source symlink... 
 
DKMS: ldtarball Completed. 
Installing prebuilt kernel module binaries (if any) 
Trying kernel: 2.6.27-7-generic 
 
Error! The directory /lib/modules/2.6.27-7-generic doesn't exist. 
You cannot install a module onto a non-existant kernel. 
Building module... 
 
Error!  The dkms.conf for this module includes a BUILD_EXCLUSIVE directive which 
does not match this kernel/arch.  This indicates that it should not be built. 
dpkg: Feil ved behandling av rt2860sta-dkms (--configure): 
 underprosessen installerte post-installation skript returnerte feilstatus 9 
Det oppsto feil ved behandling av: 
 rt2860sta-dkms 

Looks like it tried to install a kernel? and that  rt2860sta-dkms is a problem? I dont understand this.
My philosophy is that removing  rt2860sta-dkms from the apt-get library or something will fix this but i dont know. Can someone help me? Thanks :)

I get this errormsg every time i try to install a program or update

BTW i love the netbook edition!!

---

### Post by lrgmmc on 2010-09-28
It would help to know what all you did to get to this point.

---

### Post by rhoparkour on 2010-09-28
Ok, it seems to me that something went wrong with your kernel, since all troubles come from /lib/modules/whatever-kernel not existing.

It isn't trying to install a kernel, it's trying to install modules on it, but it can't find the kernel. 

Have you tried booting into another kernel (you should have at least 2 different kernels on your grub menu). Ever notice you have many linux booting into options i the grub menu? Time to use them and see if that works!

Once you have booted into the alternative kernel, try doing an apt update.

---

### Post by lrgmmc on 2010-09-28
so after some reading it looks like you downgraded the wireless driver and probly didnt have all the necessary file to do that. i would do like the post above said and use one of the other kernals then try gradeing the driver again.

---

### Post by rhoparkour on 2010-09-28
By the way, let us know how it goes!

---

### Post by TehThird on 2010-09-28
> **rhoparkour said:**
> By the way, let us know how it goes!

Hey thanks for answering and helping. I dont see any grub at all, it automatically goes into loading ubuntu.

But i fixed the problem. It could be fixed in two ways:

1. Computer Janitor. It found the packages troubling me automatically and could remove them. 
2. sudo apt-get autoremove - i think it basically does the same thing.

But atleast I got rid of the problem

---

### Post by rhoparkour on 2010-09-28
Great. Just i  case, for the future, enable the grub menu (I don't know how to do it, I hear it's disabled in clean ubuntu installs). This will allow you to boot into an alternative kernel in case something goes wrong. 

Nice to hear it's solved and glad to be at least of a little help.

---

### Post by CharlesA on 2010-09-28
You'd have to hold down shift to get access to the GRUB menu in a normal install (non dual boot)

---

