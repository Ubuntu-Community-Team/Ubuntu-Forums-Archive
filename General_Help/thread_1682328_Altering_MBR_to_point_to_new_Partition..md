---
title: "Altering MBR to point to new Partition."
date: 2011-02-05
forum: General Help
---

### Post by glene77is on 2011-02-05
Topic:
Altering MBR to point to new Partition.

History:
I trashed the MBR.
The Partitions and the OS are intact (sda7).

Fix (first):
I re-installed Ubuntu to a new partition (sda3) , 
and Ubuntu install changed the MBR to point to the new install (sda3).

Problem (second):
MBR points to the new installation (sda3).  
I want MBR to point to the old install (sda7).

Overall:
As a Linux skill, I want to be able to write an MBR 
which points into specific partitions as its starting point.

glene77is, Memphis, TN

---

### Post by nathan726 on 2011-02-05
The simplest solution is to boot from the Live CD, delete all files on sda3 (so that grub ignores it) and then repair grub...

Create the directories "mnt" and "newos" (for mounting later)
```
sudo mkdir /mnt /newos
```
Mount the new install (the one you don't want to keep) at /newos and remove all files there (so that grub skips it)
```
sudo mount /dev/sda3 /newos
sudo rm -rf /newos/*
```
Mount your old Ubuntu partition (the one you want to keep) at /mnt
```
sudo mount /dev/sda7 /mnt
```
Do some grub voodoo and fix your MBR
```
sudo grub-install --root-directory=/mnt /dev/sda
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt update-grub

```

And reboot.

Note: the above commands are for Grub2 (not grub legacy)

---

### Post by glene77is on 2011-02-05
Nathan,
Thanks for the expert advice.
First  I will study the commands, then apply.
Your tips on each line are appreciated, 
as this is a real learning opportunity .

All of this is running in RAM drive, from the Live-CD.   Right? 
Your code has been pasted at : 
     [http://paste.ubuntu.com/563657/](http://paste.ubuntu.com/563657/)   

Really great !
Sorry about all the rain and wind over your way, 
. . . I have been through 3 hurricane "eyes"  on the Atlantic Ocean (1950's) 
and it is no fun. 

Glen Ellis, Memphis, TN.

---

### Post by srs5694 on 2011-02-05
First, some basics: On most PCs, the Master Boot Record (MBR), which resides in the first sector of the disk, contains the boot loader's boot code and the primary partition table. These two components are managed by two entirely different programs -- the boot loader (GRUB Legacy, GRUB 2, LILO, or various others) and a partitioning program (GNU Parted, GParted, fdisk, etc.).

It sounds to me like your partitions are intact, and when you installed the new version of Ubuntu, it simply wrote its own boot loader into the MBR, rendering the old installation unbootable. If this is so, you should be able to get the old OS booting by reconfiguring GRUB. If so, I wouldn't bother with the commands nathan726. You may be able to get it working by typing "sudo update-grub". If that doesn't work, then you can either manually reconfigure GRUB or use [Super GRUB Disk](http://www.supergrubdisk.org/) to temporarily boot your old installation. (Pick the version from GRUB Legacy or GRUB 2 depending on which version your old installation used.) If you want to wipe the new installation, you could then re-install GRUB from the old installation (by typing "sudo grub-install /dev/sda") and use your partitioning software to remove the old installation.

---

### Post by glene77is on 2011-02-05
*******************************************************************
 Thank you for your help, both of you.  
I want know how to re-write the MBR to point into sda7.
*******************************************************************
  
> **srs5694 said:**
> 
First, some basics: . . . 
It sounds to me like your partitions are intact, 
and when you installed the new version of Ubuntu, 
it simply wrote its own boot loader into the MBR, rendering the old installation unbootable. . . . 
. . . (by typing "sudo grub-install /dev/sda") 
and use your partitioning software to remove the old installation.

SRS,
Thanks.

I can re-install and re-configure, and then copy-from-archive to reclaim everything.     
I have executable access to everything, and everything is intact.

. . . but I do see it as an opportunity to learn some more
. . . about the MBR and Grub workings. 
As convoluted as the BASH scripting is related to GRUB2, 
I have been able to make some useful mods on the templates, 
and add (the un-detectable) Puppy Linux into grub.cfg, 
along with 'blank lines' in the menu, and a 'reboot' option. 
Minor 'hacking' to be sure. 

Problem:
The install of Ubuntu to sda3 caused a re-write of MBR to point into sda3.
The /boot/grub/grub.cfg runs from sda3. 

Did this:
Boot,  sda3 grub.cfg,  selected Ubuntu sda7.
While running Ubuntu sda7,  at Terminal  executed the grub-update.
This updated the current OS, which is sda7.
This has MBR still booting into sda3. 


Thank you for your help. 
*******************************************************************

SRS, about your suggestion 
<<then re-install GRUB from the old installation (by typing "sudo grub-install /dev/sda")>>

<[http://linuxhelp.blogspot.com/2005/11/](http://linuxhelp.blogspot.com/2005/11/)
how-to-repair-corrupt-mbr-and-boot.html>
has a page about " sudo install-grub /dev/sda "  which is interesting.  
I got the idea, first read-thru, that I have already done this. 

<http://www.supergrubdisk.org/>
per your suggestion, needs some checking.   

Thank you for your help. 
I will be back in touch.

---

### Post by glene77is on 2011-02-06
Thank you NATHAN726, 
This is a "SOLUTION". 

The mount and bind and grub-install , etc, 
caused a re-link of MBR-to-partition, 
changing the bootup linked partitiion from #3 to #7. 

Your analysis and scripting were right on target.
Your use of existing tools, such as grub-install, etc., 
along with your clear notes, were very educational.
This old man, who first programmed in 8080 on an Altair 8000, 1979, 
thanks you again.   

I had wondered if there was a way to write to MBR, 
but you demonstrated that there are already tools available 
to cause a proper re-link MBR-to-partition, and they should be used. 

I formated your response to me, and pasted it at :
   [http://paste.ubuntu.com/563657/](http://paste.ubuntu.com/563657/)   
I hope that is OK.  

This is the best day of this week!
glene77is, Glen Ellis, Memphis, TN
**************************************

---

### Post by psusi on 2011-02-06
> **glene77is said:**
> 
sudo mount  --bind  /dev  /mnt/dev
sudo mount  --bind  /proc  /mnt/proc
sudo mount  --bind  /sys  /mnt/sys
# don't figure these, unless we are linking the sda7 system into the RamDrive /mnt system file area. 

They are making /dev, /proc, and /sys also appear in their respective locations in /mnt so that the chroot will have a fully functioning environment.

> **glene77is said:**
> sudo chroot  /mnt  update-grub   
#   we are changing root reference to be inside of the OS pointed to within RamDrive /mnt 
#   (which is my good install of Ubuntu, sda7).
#   then update-grub  will rebuild the MBR-to-grub link data , referring to sda7,
#   which will make MBR point into my good install of Ubuntu (sda7), 
#   where I have a good copy of grub.cfg   as   /boot/grub/grub.cfg. 


update-grub just rebuilds the boot menu ( /boot/grub/grub.cfg ).  The MBR is fixed with grub-install.  Since it sounds like your config was fine, you don't need this part.

---

### Post by glene77is on 2011-02-07
to PSUSI,
Thanks.    You are right.  config was OK. 

"They are making /dev, /proc, and /sys also appear in their respective  locations in /mnt 
so that the chroot will have a fully functioning  environment."
I accept your comments, my lingo is different.  

In my lingo, they are linked-in by reference.  
I think of them as 'mounted' and 'bound'  into RamDrive /mnt. 

In the '80s, I worked with Z80 & 6502 assembler a lot, 
and those terms are what are at hand, for the moment. 

As I progress with BASH scripting, I will pick up on new terms. 
Interesting experience with engineering help from Nathan726, and SRS5694.  

The Results as applied have been pasted at   [http://paste.ubuntu.com/563657/](http://paste.ubuntu.com/563657/)  
Thanks, again, for your comments. Always welcome.

---

### Post by glene77is on 2011-02-07
to SRS5694, 
Thanks for the help. 

In reading your post, I was wrong.    
YOU were right on this point,  
The grub-update was not required. 
The grub-install was Required, and that was the key code. 
Results Solution as applied is pasted at      [http://paste.ubuntu.com/563657/](http://paste.ubuntu.com/563657/)  

I owe thanks to several experienced people, including you.

---

### Post by psusi on 2011-02-07
> **glene77is said:**
> 
In my lingo, they are linked-in by reference.  
I think of them as 'mounted' and 'bound'  into RamDrive /mnt. 

In the '80s, I worked with Z80 & 6502 assembler a lot, 
and those terms are what are at hand, for the moment. 


Yep, that is why it is called a bind mount.  Funny enough, I actually happen to be working on a 24 bit extended Z80 right now ;)

---

### Post by glene77is on 2011-02-07
> **psusi said:**
> 
Yep, that is why it is called a bind mount.  
Funny enough, 
I actually happen to be working on a 24 bit extended Z80 right now ;)


PSUSI,
Wow!      :p     You are a Z80 Jockey !    :p
It has been nearly 3 decades, 
and the Z80 is still around,  albeit in a new form.   

I used to run 64K byte transfer comparisons 
between 6502 at 1Mhz  and  Z80 at 4Mhz. 
The 6502, with zero page in-direct addressing, 
and smaller instructions,  always came out on top.  
But, I had to admit that it was easier designing routines with the Z80, 
it had a more logical layout.   I think the word was 'orthogontal' layout. 

At the university, I wrote within the CP/M OS, 
on a Z80 card, plugged into an Apple II motherboard. 
My shop started with a Altair 8000, moved to a KIM (6502), then to Apple II.  
I did analog design instrumentation, 
and used the Apple setup for collecting and analyzing data.  
I developed in Pascal up to Borland 6, and found it easier (RAD) 
to design/write a program, but the machine interfacing was not as 
predictable as the assembler.  Some of what we did was 
to receive prototype instrument boards from Tufts Unv 
and we had to do out own interfacing, etc., in research / clinical projects.   

So, now I wonder about this 24 bit extended version of Z80.
Will have to look it up, just out of curiosity.  I still have boxes of chips, 
and a shelf of things we put together / invented along the way. 

Good luck to you,    :p   it is an interesting (sometimes tiresome ) field.  
I stopped writing for people years back, took my degrees with me, 
and now am an old man with other things of high priority.

---

