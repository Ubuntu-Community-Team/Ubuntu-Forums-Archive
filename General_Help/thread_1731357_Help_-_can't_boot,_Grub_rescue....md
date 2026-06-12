---
title: "Help - can't boot, Grub rescue..."
date: 2011-04-17
forum: General Help
---

### Post by staeit on 2011-04-17
So I got myself into a nice little mess. I have a laptop with Windows 7, and about a week ago I installed Ubuntu 10.10 64-bit via LiLi USB creator. Worked beautifully, but I was having some issues with the brightness controls so I decided to get cute and upgrade to 11.04. So I downloaded the beta2 and used LiLi to make the USB (unsupported for that version of course) which used the same parameters as 10.10. I then tried to do a fresh install over the partition I had set aside for Ubuntu and had 10.10 installed on (~80 GB). 

So in the installation itself, something got majorly screwed, and the entire system froze. Next thing I knew, I was rebooting and got the Grub Rescue prompt and no ability to load into either my old Ubuntu 10.10 or my new failed 11.04, or of course my Windows 7 partition either. The partition is obviously there, and as I only have one PC in my house, with no Windows 7 recovery discs, I currently cannot fix the mbr to just get my Windows back. I can of course get this in a couple days, but I'd like to be able to fix this without going to my parents. 

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2            1658        1671      102400    7  HPFS/NTFS
/dev/sda3   *        1671       68010   532867945+   7  HPFS/NTFS
/dev/sda4           68010       77826    78848001    5  Extended
/dev/sda5           77420       77826     3256320   82  Linux swap / Solaris
/dev/sda6           68010       76941    71737344   83  Linux
/dev/sda7           76941       77419     3846144   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 15.7 GB, 15703474176 bytes
255 heads, 63 sectors/track, 1909 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x03f70d8b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1910    15335392+   c  W95 FAT32 (LBA)

```
Those are my partitions. /dev/sda3 is my Windows Partition, which I want to boot from. Only problem is, I'm not really sure where the computer is looking to find the boot record. I think it's from my fubarred /dev/sda4 partition which means it's basically looking nowhere. So I can't modify it to point to my Windows so I can just get back there. Help!

---

### Post by vivek.pandey on 2011-04-17
you can reinstall grub using a live cd of ubuntu.... just follow this lnk
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by coffeecat on 2011-04-17
> **staeit said:**
> I think it's from my fubarred /dev/sda4 partition which means it's basically looking nowhere.

I agree - except it's sda6 (your Ubuntu root partition) that is the problem; sda4 is the extended partition. So I don't believe re-installing grub is going to help.

Three solutions.

Without a Windows 7 recovery disc, you could download a Win7 repair disc from here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

... and run 'bootrec /FixMbr' from the command prompt of the repair CD. More here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

That will get you booting into Windows.

Alternatively, and slightly surprisingly, you can repair the Windows mbr to be able to boot into Windows with an Ubuntu live CD. Three methods in this post:

[http://ubuntuforums.org/showpost.php?p=8950739&postcount=7](http://ubuntuforums.org/showpost.php?p=8950739&postcount=7)

The first one, lilo, seems to work reliably.

The third option would simply be to re-install Ubuntu 10.10 to sda6, which would give you a fresh dual-boot grub menu.

**EDIT**: one little oddity that won't affect booting is that you have two swap partitions, possibly as a result of carrying out two installs. You might want to tidy this up when you come to re-install Ubuntu.

---

### Post by staeit on 2011-04-17
Yes, I reinstalled grub, this doesn't help me though. Once I get grub installed, how do I tell grub to start Windows? Keep in mind my Ubuntu partition is fubarred and wouldn't load, even if I knew how to make grub try it.

---

### Post by staeit on 2011-04-17
> **coffeecat said:**
> I agree - except it's sda6 (your Ubuntu root partition) that is the problem; sda4 is the extended partition. So I don't believe re-installing grub is going to help.

Three solutions.
SNIP
Thanks for the suggestions. I came across ms-sys option but when I tried to do a sudo apt-get install from the live USB it failed. It gave me an error every time I tried to do a sudo apt-get - something about a missing file. (I'll post back here later) Anyways since sudo apt-get didn't work, what did I do? Well, I manually made my own grub.cfg file. Found a sample one for Windows 7 online, edited the partition to hd(0,3) and my UUID, and it magically loaded lol. Anyways it's like 4am but now I can at least make my own windows usb image from my computer as I have successfully booted into Windows - I'll repair the MBR and probably ditch Ubuntu for now. No brightness control = deal breaker for me unfortunately. I'll post here what I did in case anybody else comes into the same unfortunate mess.

---

### Post by thecamelcoder on 2011-04-17
Hey mate, been in this situation before myself and its a bit daunting, but dont worry, were there is a tux there is a way :P

Check this how to recover MBR using LiveCD post out. 

[http://wp.me/p1um9K-oK](http://wp.me/p1um9K-oK)

Let me know if you need any more help.

---

### Post by staeit on 2011-04-17
> **thecamelcoder said:**
> Hey mate, been in this situation before myself and its a bit daunting, but dont worry, were there is a tux there is a way :P

Check this how to recover MBR using LiveCD post out. 

[http://wp.me/p1um9K-oK](http://wp.me/p1um9K-oK)

Let me know if you need any more help.Again, this method doesn't work if aptitude isn't functioning from the Live CD. Thanks though, it works otherwise. 

As I mentioned I was able to manually set the grub.conf to point to the windows partition.

---

### Post by staeit on 2011-04-17
Beauty. Grub was still the active bootloader which obviously required the existence of the Ubuntu partition. So since I was able to load into Windows, I grabbed a public download link (digital river) of Windows 7 to use the recovery console, and loaded it to my USB drive. Did a bootrec.exe /fixmbr from the recovery console and restarted, and at that point Grub was no longer being used and Windows successfully loaded. Deleted all the Linux partitions including swap, and resized my Windows partition to reclaim the space, and rebooted and it was successful.

The key here was that aptitude wasn't working from the livecd/USB (probably because of the persistence file), so the conventional method of restoring the MBR wasn't working. In addition, after reinstalling grub onto the hard disk from the USB stick, there was no grub.conf file present. I had to generate one myself to boot from Windows by determining the UUID and partition number of the Windows Partition. Just figured I'd post this in case someone else comes across this specific situation.

---

