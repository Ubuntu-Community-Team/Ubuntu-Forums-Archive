---
title: "Partition and double-boot problems"
date: 2011-08-21
forum: General Help
---

### Post by Phil Mastro on 2011-08-21
I just installed 11.04 on my PC that has Windows 7 installed, in hopes of getting some practice in a Linux OS. I probably did something wrong during the installation, and I never got the option to double-boot, so it boots up straight into Ubuntu. I've checked to see if the partition for windows was still there, and it seemed like it at first, being marked as the sdb1 partition, but now it has apparently disappeared, except for the separate sdh1 16 gig partition, which is very likely the repair partition.

Has this happened to anyone before? Is there any way I can "boot" the repair partition to fix up Windows? I've just moved so my Windows disc is still hidden in a box somewhere, so I was hoping to find a method that would not require it.

Thank you for your time,
Phil Mastro

---

### Post by spec36 on 2011-08-22
This is a perfect time to drop Windows as your main OS. 

I would recommend doing a full blown Ubuntu install and then install VMware player inside Ubuntu and load Widows as a virtual machine. Now you can run Ubuntu and access Windows at the same time. This of course prevents you from needing to reboot every time you want the other OS.

---

### Post by Miljet on 2011-08-22
Hi and welcome to Ubuntu forums. It would help if we know a little more about your setup. Please go to this site,  [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/),  download the script file and run it. It will create a text file. Copy and post that text file here and enclose it it code tags.

---

### Post by Mark Phelps on 2011-08-22
While you're waiting to run the script, you can see if Win7 will still work by opening a terminal in Ubuntu, entering "sudo update-grub" -- and watching while it enumerates the kernel versions and OS's on your PC.  If you see a line something like "Windows 7 Loader on (xxx)", then Win7 is still there, and once the GRUB menu is rebuilt, you should then be able to reboot into it.

IF you don't see that line, or anything like it, you most probably overwrote your Win7 install when you installed Ubuntu.  The script you were asked to run will provide detailed information that will help us figure out if that happened.

---

### Post by Phil Mastro on 2011-08-22
Thanks for the help. So just I ran the boot info script, and my other partitions are gone. I did the update-grub too, and my windows partition is nowhere to be found. I think I actually formatted the other partitions while trying to fix it. 

Thankfully I didn't erase anything important. But I suppose I have one more question: 
Why is there a Goku holding a LOL sign smiley on the Ubuntu forums?

Thanks for your help.

---

