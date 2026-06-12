---
title: "intalling Kubuntu"
date: 2006-02-23
forum: General Help
---

### Post by lance17 on 2006-02-23
i am just switching over to linux and i tried 4 times to install kubuntu along with ubuntu. it goes to a point after i set the time zone where it goes to a black screen and there is a underscore that just sits there and does nothing. i left it for 24 hours and it still did nothing. i restarted it and it goes threw the loading screen then it goes back to the black screen.  

the computer is 
intel celeron 433 MHz 
255 Mb ram 
6 gig HD 

what do i do???

---

### Post by pestilence4hr on 2006-02-23
Are you sure the media is good?  Did you check the md5sum on the iso file you downloaded?  Those would be my first guesses.

---

### Post by lance17 on 2006-02-23
what am i looking for?

---

### Post by pestilence4hr on 2006-02-23
Well, if you do an md5sum on the iso it will tell you if the file downloaded correctly (the md5sums are available in the same place you downloaded it from).  You could also try just popping in the cd into a working machine and copying all the files from the cd onto the hard drive, that will most likely show if there is some corrupted file on the disc.

Or are you using a cd they mailed to you?

---

### Post by lance17 on 2006-02-23
i am using a iso file. i just went on their site to get them to send me a disk. 

i am reinstalling it right now so i will see where it goes.

it got past the part where it restarts and it says it is installing packages

could it be that the computer is to old. i dont want to mess my other computer up before i get to know linux

---

### Post by pestilence4hr on 2006-02-23
No, unless the hardware is bad ubuntu should run on it ok.  I suppose it could be the cdrom you have is old enough that it has trouble reading cd-r's, that used to be a big issue.

Anyways, if you have reached the reboot, you should be golden.  Anything you need to do now can be done over the internet if needed.

---

### Post by lance17 on 2006-02-23
it just finished that instalation. it went to fast to read but i think it said starting gnome and  now it is at the black screen with the underscore on it and it doing nothing

---

### Post by pestilence4hr on 2006-02-23
Sounds like the xserver failed to start or crashed, if you hit (ctrl+alt+f*) where * is in [1,6], you should get a command prompt.

---

### Post by lance17 on 2006-02-23
when i hit ctrl alt f1/f6 it does nothing. i also copied  the cd to my computer and all the files came over it never said anything about corrupt or anything. it also says when it is loading that the hotplug subsystem does not say ok and sycronizing clock to a web site says failed, but i took out the modem and the ethernet card to see it that is what causeing it.

---

### Post by lance17 on 2006-02-23
hey i think i got it. i took out my video card. there is an onboard video card. now it went all the way to the log on and i got loged on so thanks for the help

---

### Post by massmur on 2006-02-27
I put my installing problem in the same thread.

So, I had win xp and installed kubuntu 5.10 on an own hard disk.
At first grub and it went straight to windows didn't start so I changed 
the hard disks' boot order. Then it was fine until I got an error message: "ALERT! /dev/hdc1 does not exist. Dropping to a shell!"
I reinstalled the whole thing, but it didn't help.
Here's copy of the screen:

> Booting 'Ubuntu, kernel 2.6.12-9-amd64-generic Default '
kernel direct mapping tables upto ffff810100000000 @ 8000-c000
root (hd0,0)
Filesystem type is ext2s, partition type 0x83
kernel /boot/vmlinuz root=/dev/hdc1 ro quiet splash
[Linux-bzImage, setup=0x1c00, size=0x13e30e]
initrd /boot/initrd.img
[Linux-initrd @ 0x3faf0000, 0x4ef2ba bytes]
savedefault
boot.
Decompressing Linux...done.
Booting the kernel.
Loading, please wait...
ALERT! /dev/hdc1 does not exist. Dropping to a shell!


BusyBox v1.00-pre10 (Debian 20040623-1ubuntu22) Built-in shell (ash)
Enter 'help' for a list of built in commands.

/bin/sh: can't access tty: job control turned off
#
What could be the problem?

---

### Post by Jucato on 2006-02-27
during installation, after recognizing that you have another operating system installed, you will be asked where you would like to install GRUB. The best choice would be the MBR (master boot record) of the pimary master (first hard drive of the first IDE). Where did you install yours?

Also, when you boot for the first time, did GRUB appear and went by fast or it didn't appear at all?

---

### Post by massmur on 2006-02-28
> during installation, after recognizing that you have another operating system installed, you will be asked where you would like to install GRUB. The best choice would be the MBR (master boot record) of the pimary master (first hard drive of the first IDE). Where did you install yours?
I installed it on the MBR. And no, the GRUB didn't appear at all.

---

