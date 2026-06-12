---
title: "Ubuntu problem with GRUB"
date: 2009-11-04
forum: General Help
---

### Post by ALF102 on 2009-11-04
Usually after I choose Ubuntu at the OS chooice menu, there's another menu giving me the choice to start with whether the normal Ubuntu or the recovery mode ubuntu..but now the menu is gone. I dunno what happen. Right now all is shown is a command list menu with the title "GRUB 1.97 Beta4" saying something about BASH writing enable or something like that, so I pres the TAB button to show "Possible Commands", then I try type in "linux" and the reply is "no loaded kernel". What is happening here? I just got Ubuntu like 2 days ago

---

### Post by fox.esq on 2009-11-04
I am having the same problem as well.  When I boot up my computer GRUB won't load and I get the same thing the guy who posted this did.  It has worked for me in the past; I just installed 9.10 the other day and it booted up fine 5-6 times.  Now it won't.

---

### Post by grandtoubab on 2009-11-04
If you perform a clean install you are now using grub2

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


the former grub-legacy remains only if you upgrade from 09.04
[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by ALF102 on 2009-11-04
I have two OS now do I have to delete windows in order to do clean install? this is my first Ubuntu and I install 9.10

---

### Post by grandtoubab on 2009-11-04
welcome to the grub2 mess :lolflag:

---

### Post by hwttdz on 2009-11-04
Well if you're looking for a truly clean install you can put in a live cd, delete all partitions (or the partition table), then create new partitions and install using those partitions.  So live cd, open terminal, sudo gparted, delete partition table, make new partitions, shutdown and install using new partitions.

---

### Post by grandtoubab on 2009-11-04
dual-boot and more should be possible
[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

, why tell him to destroy his machine??
[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)

[http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu)

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

**Install Ubuntu**

  When the CD is ready, simply put it in your CD  drive, restart your computer and follow the instructions that will  appear on your screen. Don't forget that you can create more copies and  pass the CD to as many people as you like.

---

### Post by ALF102 on 2009-11-04
Apart from having to REINSTALL ubuntu (which I don't want to do for the 2nd time and this is the second time this happens to me) is there any other option to regain back the usual grub menu?

---

### Post by hwttdz on 2009-11-04
Sorry, misread, the lack of any punctuation doesn't help, nor does people posting separate issues in the same thread.  Anyways to restore grub2 check out the instructions here

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by grandtoubab on 2009-11-04
is it painful to read???
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

---

### Post by nvance on 2009-11-04
I have done the upgrade (not fresh install) and I am missing a few packages.  What I have done in the past is delete the partitions that deal with my Ubuntu install (do not touch any Windows partitions if you are dual booting) and create the new partitions (boot, swap and home) therefore all the newly created partitions will be formatted and ready for the install and your Windows has not been touched at all.  I have to say that 9.10 is the best so far and as in the past a fresh install is the best because each of us installs different packages to tweak the install to our liking therefore you might not get the right upgraded packages or GRUB fixes/upgrades.

---

### Post by ST3ALTHPSYCH0 on 2009-11-04
Yes, it is possible to uninstall Grub2 and install legacy grub.... that said, I don't personally know the commands to accomplish this. I'll do some research to see if I can find them for you.

---

### Post by grandtoubab on 2009-11-04
[http://ubuntuforums.org/showpost.php?p=8243067&postcount=10](http://ubuntuforums.org/showpost.php?p=8243067&postcount=10)

---

### Post by fox.esq on 2009-11-04
I've tried entering the various commands that are supplied on some of the guides etc. but it comes up as: 'no such disk' or 'try 'help' for usage'.  For some reason I think it stopped recognizing where the partitions are or something like that.  For me it was working just fine then this morning GRUB2 decided: "hey, I'm just going to be an a**hole and not work all of a sudden; eat sh*t and die loyal Ubuntu user!"

I'm thinking that I may need to reinstall 9.10 with a special partion for booting; I've had to do this before with previous versions - I'm not sure exactly how to set it up with 9.10 though because it is using ext4 instead of ext3; if that makes any difference.

---

### Post by ALF102 on 2009-11-04
well, I've tried the part of "express boot to recent kernel" and "boot to specific kernel manually" but I got no luck with both ways.

For "Express boot to recent kernel"

sh:grub>ls
(loop0) (hd0) (hd0,1) (hd0,0) (hd0,5) (hd1,1)
sh:grub>set root=(hd0,5)
sh:grub>linux  /vmlinuz root=/dev/sda5 ro
    [file not found]

I've even tried for (hd0,1), (hd0,0) and (hd1,1)

the result is :[file not found]

so I reboot and try it again and I did it like this:

sh:grub>linux  /vmlinuz root=/dev/sda5 ro
     [Linuz-bzImage, setup=0x3o00, size=0x3b7f00]
sh:grub> initrd /initrd.img
     [Initrd, addr=02f932000, size=0x7018d5]
sh:grub>boot

I did it without "set root" but then the boot process is stuck.

The same goes "Boot to specific kernel manually"

---

### Post by ALF102 on 2009-11-04
Ok, I've tried again but then the result is the same. And after reading and readin and reading the guides I just realised that whenever I choose Ubuntu at the dual-boot, Grub 1.97 beta 4 didn't show me the graphical menu but instead it show me this:

[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]

sh:grub>


As I follow the guide carefully, I just noticed the "Express Boot to the Most Recent Kernel" is only to use if the user has problems booting 'but' the menu is available. In this case the menu is 'not' available. And what I'm trying to asked in my previous question was in fact that I wanna know how to revert this back to the previous state where Grub will display the menu and boot normally? 

(I'm really sorry if my thread wasn't understandable as there are so many things that I have to understand yet about using Linux Ubuntu, so many functions unknown yet. pls forgive me for being a noob)

---

### Post by fox.esq on 2009-11-05
I _solved the problem_ that I'm having that is similar to yours.  I think what might be going on is that the GRUB is no longer recognizing your boot info on your hard disk.  Do you have windows on one hard drive and Linux on another?  That's what I have.  When I install Ubuntu much of the booting info is located further inside the disk instead of at the beginning where it is readily read by GRUB.  In the past with previous editions I've had to pre-arrange partitions specifically for booting and for Linux software etc.  I have had to put the boot partition at the beginning so the motherboard and GRUB will pick it up right away instead of going into some error mode.

You won't have to reinstall 9.10 but you will have to mess around with the partitions.  I suggest you download a program called Gparted live.  It is sort of similar to Ubuntu live except it will only partition your hard disk.  Burn the program on a cd as an .iso image and boot off the cd like you did with 9.10. (Find a friend or relative that will let you borrow their computer [in Windows you'll also have to download a program called infra-recorder to burn an .iso image] burn the image at the slowest possible speed). When the program starts up it will allow to examine your hard drives and their partions.  DO NOT mess with any NTSF partitions because that is where your Windows is.  

What you are looking for is your Linux partitions, the ext4 in particular.  Click on that partition then look for the buttons above that will allow you to move it.  Another window will come up allow you to select how you want to move it.  Start with the left hand side and move the beginning of that partition to the right (it is probably labelled something like sdb1 ext4), move it to the right so that it is going to create ~10 Gb of unformatted space at the beginning of your disk, then click apply.  It will take somewhere around 3 hours for it to move everything over and create the blank space.  Once it is finished, format that blank space as a primary partition and as ext4.  Don't install Linux in that space or anything else, just leave it formatted as ext4.

Shut down Gparted live and remove the cd and reboot.  It might be buggy the first few times when starting but give it a few goes.  Grub should now pick up on Ubuntu and Windows and be able to load them.  You should still have all your files and docs in Linux intact, they should have just been moved over instead of deleted.

This is what I did, and so far it has worked for me.  I had a lot of files in Windows and Linux that I wanted to get and was unable to access until I did this; needless to say I have taken advantage of the success and backed all my stuff up just in case.

If you have any questions or want me to clarify, feel free to ask.

---

### Post by nixed242 on 2009-11-05
> hen I install Ubuntu much of the booting info is located further inside the disk instead of at the beginning where it is readily read by GRUB.

Could this be why Grub attempts to access my hard drive for 20 seconds before showing me the actual Grub Menu? Is it because it's looking for the Windows info on my first partition? (Windows is first, Linux is second). This never happend with the previous version.

---

### Post by fox.esq on 2009-11-05
> **nixed242 said:**
> Could this be why Grub attempts to access my hard drive for 20 seconds before showing me the actual Grub Menu? Is it because it's looking for the Windows info on my first partition? (Windows is first, Linux is second). This never happend with the previous version.

I'm guessing it is looking for your booting info, which, because of GRUB is on your Linux hard drive.  There is something going on, I think, with the motherboard or bios that is partnered with GRUB in finding what operating systems are available to load.  If Grub is not picking up on either readily or they are located further inside your hard drive, it might take awhile or never to find it.  

With my computer, for some reason, it will only look so far into a disk before it gives up.  When I initially installed 9.10 is was probably on the very edge of where it is read; after loading some files and installing some updates it must have pushed the boot info stuff over past the point of where it is read.

---

### Post by ALF102 on 2009-11-05
> **fox.esq said:**
>   Do you have windows on one hard drive and Linux on another? .

No, I install both of them on the same drive. Oh and about Gparted is that, its for x86 machine. How do I know if Gparted is usable for me?

---

### Post by fox.esq on 2009-11-05
> **ALF102 said:**
> No, I install both of them on the same drive. Oh and about Gparted is that, its for x86 machine. How do I know if Gparted is usable for me?

It's Gparted live you want; I don't think it matters for the live version.  Here's a link to the specific site: <http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.4.8-1/>  Download only the .iso portion.

Even if all your stuff is on one drive, you might be able to scoot everything over and create ~1-5 Gb partition that is a primary ext4 partition for booting.  You won't have to delete anything, but you'll have to shrink the other partition's sizes.  It will take a few hours to move everything over, just so you know.  Then you can format the new section as a sort of boot partition.

---

### Post by ALF102 on 2009-11-05
Ok thx, this should be helpful for me in the future

---

### Post by chareen on 2009-11-09
Hi,
 
I have recently uninstalled Ubuntu 9.04 (which was installed on Windows) from my laptop. However, when I rebooted the machine the OS option (Windows / Ubuntu) still exist. 
 
I have tried repairing the Windows and typing in the Bootrec.exe /FixMbr command. However it doesn't seem to work. I have also tried uninstalling wubi but the problem remains.
 
Appreciate if you could help me.

---

### Post by hwttdz on 2009-11-09
If you have a different problem, use a different thread.  If no thread with your problem exists, start a new one.  This is not to be unhelpful, this is rather to help people who may have your problem later on find the solution they need and not be confused as every thread is just a bunch of people outlining their own unrelated problem.

---

### Post by chareen on 2009-11-09
Sorry I had used this thread. i thought the problem I am facing with was dealing with the GRUB, that was why I didn't start a new thread.

---

