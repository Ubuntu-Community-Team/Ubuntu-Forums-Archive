---
title: "Totally messed up my boot menu... need help"
date: 2009-07-16
forum: General Help
---

### Post by domorovich on 2009-07-16
So I got a Toshiba NB-205 earlier today and tried throwing netbook remix onto it. After having some problems with bad .img files, I went with the 9.10 version because it was the only one with correct md5sum. I booted from a flash drive at first and used GParted to make a 50gig ext4 partition and a 5gig swap partition, set ubuntu to install from the drive and let it do its work. Afterwords, it restarted and ubuntu loaded no problem, everything working.

So then I restarted to boot into XP (pre-installed). I get a boot menu that has 4 ubuntu boot options (2 safe modes) and 4 other boot options (2 safe modes), all linux. So I couldn't get into XP. I booted off the flash drive and loaded GParted again and deleted the ubuntu off, and restored the partitions to their original state. Now when I boot the computer I get:

> GRUB loading.
Welcome to GRUB!

Entering rescue mode...
error: no such partition
grub rescue>
>If I load from the flash drive, I can still see all my XP files and whatnot exactly where they're supposed to be, and the drive looks right from ubuntu's browser.

So any ideas how I can get it back to normal so it just boots XP like it did factory?

Thanks,
Joseph

---

### Post by -=hazard=- on 2009-07-16
Did you totaly removed linux and left only xp ?

---

### Post by domorovich on 2009-07-16
Yeah so all I have is XP that I can't boot, and ubuntu running off a USB.

---

### Post by ddivney on 2009-07-16
Try reinstalling micosoft MBR (the bootloader). It seems to me like GRUB overwrote it and now that GRUB is gone, XP doesn't have a bootloader.

---

### Post by -=hazard=- on 2009-07-16
First of all I suggest you to totally remove windows and reinstall ubunut (thats your choice).

anyway try this command on grub FDISK /MBR

---

### Post by domorovich on 2009-07-16
Where would I go to reinstall the MBR? That's normally on the OS CD, but with no optical drive (or XP CD), that's not really an option...

Excuse the ignorance, but do I put the FDISK /MBR into terminal or into GRUB when it boots up and I get the message I posted? I tried it at bootup and I get "command not recognized", but it won't recognize *any* commands. Probably because they were deleted...

---

### Post by -=hazard=- on 2009-07-16
> **domorovich said:**
> Where would I go to reinstall the MBR? That's normally on the OS CD, but with no optical drive (or XP CD), that's not really an option...

Excuse the ignorance, but do I put the FDISK /MBR into terminal or into GRUB when it boots up and I get the message I posted? I tried it at bootup and I get "command not recognized", but it won't recognize *any* commands. Probably because they were deleted...

Ok then 

First you have to boot from your xp cd then go to repair then do the following commands:

you are here C:\WINDOWS

then type
 
CD .. 
FIXBOOT C: 
FIXMBR 
BOOTCFG /rebuild

---

### Post by domorovich on 2009-07-16
Well I don't have an XP CD because the computer didn't come with one, and it doesn't have an optical drive, so I can't use a CD even if I did have one. 

I've found that with the CD it's an easy fix, but I can't go that route. Surely there's a workaround...?

---

### Post by -=hazard=- on 2009-07-16
> **domorovich said:**
> Well I don't have an XP CD because the computer didn't come with one, and it doesn't have an optical drive, so I can't use a CD even if I did have one. 

I've found that with the CD it's an easy fix, but I can't go that route. Surely there's a workaround...?

It can be done with a diskette, but I never tried that, anyway take a boot-disk here [http://www.bootdisk.com/bootdisk.htm](http://www.bootdisk.com/bootdisk.htm) I know that win98 cant fix the boot for xp but win98 SE maybe, so take it and make a diskette than boot from it and on dos type: fdisk /mbr

-Edited-
Sorry I didn't add the site..

---

### Post by ddivney on 2009-07-16
Here's what I would do. Try to reinstall ubuntu on a separate partition from XP. Then use GRUB to load XP. If that doesn't work, I believe there are ways of running usb drives as if they were CD's. There are alot of versions of Windows floating around that only support the repair feature, but not the install. Use the repair feature.

---

### Post by domorovich on 2009-07-16
Alright, right now I'm repartitioning and reinstalling ubuntu. Hopefully that will fix the boot problem, but before I didn't have an option to boot XP from that boot menu, just ubuntu. How do I get XP to be an option?

---

### Post by -=hazard=- on 2009-07-16
> **domorovich said:**
> Alright, right now I'm repartitioning and reinstalling ubuntu. Hopefully that will fix the boot problem, but before I didn't have an option to boot XP from that boot menu, just ubuntu. How do I get XP to be an option?

If during linux distro install you choose to install the grub loader on the first disk, windows loader will be there.

---

### Post by ddivney on 2009-07-16
Load Ubuntu. Once in there, find the file "grub.conf". Open it and scroll to the bottom.
Add this to the very bottom:

**title Windows XP**
**root (hd0,0)**
**makeactive**
**chainloader +1**

then save the file and reboot. XP should be good!

---

### Post by -=hazard=- on 2009-07-16
> **ddivney said:**
> Load Ubuntu. Once in there, find the file "grub.conf". Open it and scroll to the bottom.
Add this top the very bottom:

**title Windows XP**
**root (hd0,0)**
**makeactive**
**chainloader +1**

then save the file and reboot. XP should be good!

it's not grub.conf but menu.lst
exactly its located here /boot/grub/menu.lst

---

### Post by domorovich on 2009-07-16
So it's installed and XP isn't showing again. Inside /boot/grub there isn't a grub.conf or a menu.lst though there are a lot of files in there... this is netbook remix 9.10

Any ideas? (thanks for all the help so far)

---

### Post by domorovich on 2009-07-16
A search for menu.lst brought me to a sample /boot/grub/menu.lst entry for memtest86

Since /boot/grub/menu.lst doesn't exist, could that be where the real problem is? That could explain why I have 4 linux boot options, 4 memtest options, and no XP...

Any thoughts/ideas?

---

### Post by -=hazard=- on 2009-07-16
> **domorovich said:**
> A search for menu.lst brought me to a sample /boot/grub/menu.lst entry for memtest86

Since /boot/grub/menu.lst doesn't exist, could that be where the real problem is? That could explain why I have 4 linux boot options, 4 memtest options, and no XP...

Any thoughts/ideas?

The last grub version that comes with Ubuntu 9.04 is /boot/grub/menu.lst
No the problem is not that you have 4 linux boot option, I have them too. You can have 10 if you want. How did you search for menu.lst ?

---

### Post by domorovich on 2009-07-16
I'm not using 9.04, I'm using 9.10. And I just used the search box in the file browser.

---

### Post by merlinus on 2009-07-16
IIRC, 9.10 uses grub 2.

Good info here:

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

---

### Post by domorovich on 2009-07-16
Ah that makes sense cause it says they replaced menu.lst with grub.cfg which I have. Currently adding the XP example in the post...

---

### Post by domorovich on 2009-07-16
Actually, even simpler. Just had to go to terminal and run

> sudo update-grub2

And it found it and added it for me. Now to test...

---

### Post by -=hazard=- on 2009-07-16
> **domorovich said:**
> I'm not using 9.04, I'm using 9.10. And I just used the search box in the file browser.

Go Aplications -> Accessories -> Terminal then on terminal type sudo nautilus, it will open the computer browser with root privileges so you can modify stuff, then go on Filesystem (menu on left) then open folder boot then grub. Inside grub folder must be the file that configure the grub loader, on ubuntu 9.04 is menu.lst

The file that we want should contain in the first line this txt

# filename - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

after finding it add on the end this entries before ### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows 95/98/NT/2000
root        (hd0,0)
makeactive
chainloader    +1


 (hd0,0) means xp is installed on the first disk that is connected with the first slot of your ata and on the first partition of the first disk.

---

### Post by -=hazard=- on 2009-07-16
> **merlinus said:**
> IIRC, 9.10 uses grub 2.

Good info here:

[http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")

didnt know this :)

---

### Post by domorovich on 2009-07-16
Well now XP is an option in the boot menu, and clicking it brings me to the first loading screen for XP, but about 3 seconds in the computer restarts... 

I have to run to the gym for a bit, but afterwards I'll be back to seek more help... 

Thanks guys, you've been awesome!

---

### Post by merlinus on 2009-07-16
Yeah, we have about another 3 months to learn the new stuff before the official version of 9.10 is released!

---

### Post by domorovich on 2009-07-16
Ha, I just restarted and now I don't even get a boot menu. I just get a "Welcome to GRUB 1.96" screen with a terminal... fantastic.

---

### Post by -=hazard=- on 2009-07-16
> **domorovich said:**
> Well now XP is an option in the boot menu, and clicking it brings me to the first loading screen for XP, but about 3 seconds in the computer restarts... 

I have to run to the gym for a bit, but afterwards I'll be back to seek more help... 

Thanks guys, you've been awesome!

If I was you I would ask my self. Why do I need windows anymore? If you have good reasons then try to fix dual boot things and windows bugs and other stupid things like viruses etcetera but if it doesn't worth it, then purge xp :P

---

### Post by -=hazard=- on 2009-07-16
Take a look at some grub commands here [http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList)
I have to go sleep now, @ me is 3:40 of the morning.
Do NOT format because with some search and help here you will resolve.
I'll check up this thread tomorrow again and see what you have done and how I can help, but do not format.

G. Night

---

### Post by domorovich on 2009-07-17
Well I've gotten the boot menu back up, and XP is an option again.

I can boot ubuntu fine (granted it takes about 2 minutes to boot...), but XP doesn't make it longer than 5 seconds into its startup screen before the computer restarts.

So any ideas? :/ 

The way I see it, if I can get it back to factory where XP is the only thing booting and ubuntu is completely removed, I can start fresh with the dual boot idea, this time using 9.04 which you all know better. So how can I get to that?

---

### Post by merlinus on 2009-07-17
Boot from xp disk, select restore, and then FIXMBR and FIXBOOT.  Upon restarting, your computer should boot into xp.

Then you can use the 9.04 cd to install that version into the partitions you were using for 9.10.

---

### Post by domorovich on 2009-07-17
Like I've said, 1: I don't have an XP disk, 2: even if I did, it's a netbook, so there's no optical drive. 

Is there any workaround? :/

---

### Post by -=hazard=- on 2009-07-17
> **domorovich said:**
> Like I've said, 1: I don't have an XP disk, 2: even if I did, it's a netbook, so there's no optical drive. 

Is there any workaround? :/

I explained some posts above, use a diskette, I posted a link where you can take a windows boot

---

### Post by btberch on 2009-08-23
Thought I would add a little more to the post since there haven't been any replies lately.  I installed 9.10 netbook remix to dual boot on the toshiba nb205 with windows xp.  No problem with xp being listed in grub2.  In grub.cfg there are the entries for xp and the recovery partition listed twice.  One from, I assume, grub and the other says from a debian based system.  

Here is where i differ from the others trying to boot into windows.  I get the windows screen saying that windows wasn't shutdown properly the last time and gives the options on booting back into xp.  As an other has stated above when trying to boot xp about 3 to 5 seconds into the boot process it fails.  If choosing to boot in safemode it appears from the scrolling on the screen that files are missing from xp to allow booting.

Has anyone else saw this?

Later today, I hope to hook the external dvd up to the machine and with the recovery disks i made, see if fixing xp may help.

I check back later, before I do this, to see if this gives anyone another idea.  This is my first time with grub2, so it is just experimentation for me at this point.

---

