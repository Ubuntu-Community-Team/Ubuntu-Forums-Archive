---
title: "I get a command line when I try to boot Ubuntu 9.10"
date: 2009-10-30
forum: General Help
---

### Post by Missing_Number on 2009-10-30
I installed Ubuntu 9.10 to my hard drive using Wubi. The installation went fine.
 
The problem is, whenever I try to boot Ubuntu 9.10 using the bootloader menu, I am given a command line with no idea what to do. I'm not sure what it's called, but I think it was GRUB or something. It tells me to press TAB to see what I can do. One choice was "boot". Typing BOOT says an error message?
 
What's wrong here? How do get on Ubuntu 9.10?

---

### Post by retrow on 2009-10-30
At the beginning, do you have a Grb screen that lets you choose between Windows and Karmic (Plus memtest and all that)?

---

### Post by Missing_Number on 2009-10-30
Yes, there is a menu that says "Choose the operating system to load" with a choice between "Microsoft Windows XP Professional" and "Ubuntu".  This issue occurs after I select "Ubuntu".

---

### Post by Missing_Number on 2009-10-30
More info:

It's called GNU GRUB.

When I type "boot" it says "error: no kernel loaded".

---

### Post by Missing_Number on 2009-10-30
Bump

---

### Post by beloved88 on 2009-11-06
yes, i have the identical problem.  It loads GNU Grub version 1.97~Beta4
command "linux" returns "no kernel specified", command "boot" returns "no loaded kernel"

---

### Post by wire.tap on 2009-11-09
I had the same problem as well, and so did my brother (which indicates to me that this is a very common problem). He told me to just reinstall it, because when he did a reinstall, it started working (very flaky). I completed a reinstall and it worked for about two days. I was elated. Then, this morning when I got up, all hell broke loose. I have no idea what changed between today and yesterday, but when I booted, I got the (Grub version 1.97~Beta4). When I type "boot" it says "error: no kernel loaded." I'll let you know if I discover anything new. I don't think reinstalling every time you get this error is a legitimate solution since it seems to be a recurring problem. If no one can find a solution in the next few days, I was thinking I would try downgrading to Ubuntu 9.04.

---

### Post by Ali008 on 2009-11-12
i have the same issue ....  any help!!

---

### Post by salar on 2009-11-12
Ditto, exactly the same problem here. I get the OS choice screen followed by the following when I choose Ubuntu 9.10.

> GNU GRUB version 1.97 beta4
[minimal BASH - like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions.]
sh:grub>Help! This was my chance to convince my other half that Ubuntu is a safe and simple OS to use. My arguments are falling a bit flat at this point and Windows 7 is increasingly becoming more viable...

John

---

### Post by salar on 2009-11-12
Looks like the [same problem]("http://ubuntuforums.org/showthread.php?p=8279015#post8279015") with the 64bit version as well. 
John

---

### Post by 3rdalbum on 2009-11-12
Try installing Ubuntu "the proper way" by booting from the CD and running the installer on there. The trouble with Wubi installs is that it's possible for Windows to interfere (unintentionally) with the Ubuntu file, causing problems.

---

### Post by salar on 2009-11-12
Do you mean the full installation or the installation inside windows, both of which are available on the Ubuntu disc?
John

---

### Post by wire.tap on 2009-11-12
I found these directions in the thread referenced above and they worked for me, at least to boot into Ubuntu. Now I just need to figure out a way to make this happen every time without having to type in all that nonsense. 

> **djhk said:**
> From the SH> prompt enter

sh:grub>insmod ntfs
sh:grub>set root=(hd0,1)
sh:grub>loopback loop0 /ubuntu/disks/root.disk
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

You can use the TAB key to enter the remaining string.

This should boot your system.

IIn Ubuntu open the terminal and enter

sudo update-grub2

This should fix your grub files.

As a side note the sudo update-grub2 did not fix my problem, but I think it may be a special case with me. Good luck.

---

### Post by jimmyneph on 2009-11-16
I'm having the same problem...
I've followed all instructions, but when I try to load kernel, looks like that not exists.
Using grub>ls (loop0), drop the message "Unknown Filesystem".
I'm using the wubi edition

---

### Post by julianb on 2009-11-16
If you are using WUBI, that is a type of "installation inside windows", which doesn't require you to repartition your hard drive.

If WUBI gives you problems loading your Ubuntu/Linux kernel, I recommend doing an ordinary "dual boot" install from a CD. You'll preserve your Windows OS and your existing files, but you will have to allow Ubuntu to partition your hard drive so that a partition of the drive is reserved for an Ubuntu file system.

If you want the very newest software, use Ubuntu 9.10 . However, the software available for Ubuntu 9.04 is excellent, and if you want a really reliable system then consider using Ubuntu 9.04 instead of 9.10:
[http://releases.ubuntu.com/9.04/](http://releases.ubuntu.com/9.04/)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

P.S. - It's likely that most new bugs/problems people have with Ubuntu 9.10 will be resolved by the time 9.10 is three months old.

---

### Post by jimmyneph on 2009-11-17
Hi julianb,
I've tried the dual boot way, but doesn't work too...
But I'll try the 9.04...

I'll be back with results

---

### Post by theDeeje on 2009-11-21
Hey guys,

I'm having the same problem with Ubuntu 9.10 64-bit. I installed it yesterday via Wubi and it worked like a charm for several hours, after numerous reboots and whatnot. However, the last time I rebooted I got the same GRUB command line others here seem to be getting. It states that there is no kernel loaded.

It seems to be completely random, as I did nothing out of the ordinary before rebooting. I have a feeling it might be the Nvidia graphics driver I installed earlier that caused the problem. Did any of you by chance install drivers for a Nvidia GPU before getting boot errors?

---

### Post by jimmyneph on 2009-11-22
Hi theDeeje!!
I've solved the problem, but I forget to reply here.
To solve it, you need to use a workarond. Install ubuntu 9.06 and then upgrade to 9.10.
It worked to me.:P

---

### Post by theDeeje on 2009-11-22
Thanks jimmyneph!

I'll give this a try when I get the time. If you run into another problem, would you mind to post about it on this thread? Just in case the workaround is temporary. I'll do the same.

Cheers

---

### Post by SPARTAN-118 on 2009-12-03
Help.

I got the same message in WUBI, though I don't want to have to re-install, since I'd rather not lose my files that I just put back on today, thanks.

I'll try to do those instructions relating to the sh> command. Get back to you perhaps sometime tomorrow?

Thanks,
Matt.

---

### Post by untappedpilot2 on 2009-12-08
I have a WUBI install and here is how I finally got this to work.

From the Grub Shell

1) sh:grub>insmod ntfs
2) sh:grub>set root=(hd0,1)
3) sh:grub>loopback loop0 /ubuntu/disks/root.disk
4) sh:grub>set root(loop0)
5) sh:grub>linux /boot/vmlinuz-2.6.31-15-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk
6) sh:grub>initrd /boot/initrd.img-2.6.31-15-generic
7) sh:grub>boot

pretty much the same as the other one of the other posts except for the 2.6.31-15-generic. this problem occured for me after trying to update my linux kernel. so this is the fix

---

### Post by Ratsock on 2010-01-07
Im having this exact problem and the fix above works for me. Unfortunately I cant find a way to do this automatically (grub should be doing this). I dont want to type this in everytime I reboot.

sudo update-grub2 doesn't work

---

### Post by justinweathersby on 2010-01-08
i tried this way and still cant get ubuntu back up and running

whenever i type loopback loop0/ubuntu/disks/root.disk
i get a error: file name required

---

### Post by Ratsock on 2010-01-10
> **justinweathersby said:**
> i tried this way and still cant get ubuntu back up and running

whenever i type loopback loop0/ubuntu/disks/root.disk
i get a error: file name required


There's a space after loop0
So 
loopback loop0 /ubuntu/disks/root.disk

Not
loopback loop0/ubuntu/disks/root.disk

---

### Post by NathanProenca on 2010-01-10
I'm not sure,  but it just happend when I update the Grub.
At first , I reinstalled , and then avoid to update the Grub.but unfortunatly , I updated it, and I don't want to reinstall because I have a lot of data that I don't want to lose

---

### Post by connectkevin on 2010-01-16
Hi Friends, just few minutes back i have updated the karmic, and i have come across the same problem, my computer got dual booting, i have installed ubuntu inside vista. Good news is that my problem got fixed, its very simple and easy thing which can be fixed in seconds. 
Download the file from the link given to your windows desktop, [https://bugs.edge.launchpad.net/ubun...04/comments/90]("https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90") 
replace it with the old file in your C: (drive)(as i have installed my windowsVista on C: drive), and reboot the computer and select your linux version and keep rocking, it works perfect like before.:popcorn:

---

### Post by inswwwa on 2010-02-16
i have this same problem and now an even bigger issue. i tried to reinstall as suggested and it will not boot from cdrom!

its an old IBM thinkpad T-40. i press the acess IBM (to get into bios same as F12) and then select to boot from something else. there is no option for my cd? where did it go?

-Rufus

---

