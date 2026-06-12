---
title: "How to format hdd through Ubuntu 9.1 to install Windows98 on it."
date: 2010-02-10
forum: General Help
---

### Post by mfgamer on 2010-02-10
Hey there,
Currently, I am running Ubuntu 9.1 off of the LiveCD. I am fairly clumsy in Linux as until a day or two ago, I'd only used Windows XP.

I was attempting to set up a multiboot system with XP,98, and Ubuntu when, through a series of mistakes, I formated my entire XP hdd and hid my second hdd(the one with Ubuntu installed) from my bios. Therefore, I can no longer load any OS through Grub.

I have the install disks for Windows XP SP3 and Win98SE, but everything I've read says that it's much easier to set up a multiboot if you install 98 first.

This leads to my main problem:
My main hdd is 150GB. Whenever I try to install Win98 on to it, it gives me an error about enabling LBA because it's too large. I tried enabling it through the bios, but Win98 setup still said that it had a ton of bad sectors. Is there a size/format of partition that I can create to install 98 without these problems?

Thanks for any help you can provide.

---

### Post by Richard1979 on 2010-02-10
If you need Win98 for legacy reasons (and I hope to god you aren't using this a proper OS), why not try using VirtualBox?

---

### Post by mwcrowley on 2010-02-10
ditto on the VirtualBox suggestion.  
Otherwise, use gparted, you can partition the hard drive into 4 partitions.
One for 98SE, one for winXP, one for Ubuntu and a fourth for linux swap partition.  Make sure you format them for the correct file system.

---

### Post by lukeiamyourfather on 2010-02-10
VirtualBox for sure.

---

### Post by oshunluvr on 2010-02-10
Ok, now to address some of your questions;

> **mfgamer said:**
> 
I was attempting to set up a multiboot system with XP,98, and Ubuntu when, through a series of mistakes, I formated my entire XP hdd and hid my second hdd(the one with Ubuntu installed) from my bios. Therefore, I can no longer load any OS through Grub.

I've never heard of an O/S that can "hide" a hard drive from bios. Your O/S may not see a hard drive, but the bios will UNLESS it's bad. Go into your bios and change the boot order if that option is available. It's more likely that you installed Ubuntu to your second hard drive, when you wiped and then installed Win98 it wiped the master boot sectors on your first hard, thus effectively removing GRUB. 

Another possibility is you actually have ONE hard drive that was partitioned under windows (leading you to believe you had two) and when you reformatted you combined it all into one partition.

> **mfgamer said:**
> 
My main hdd is 150GB. Whenever I try to install Win98 on to it, it gives me an error about enabling LBA because it's too large. I tried enabling it through the bios, but Win98 setup still said that it had a ton of bad sectors. Is there a size/format of partition that I can create to install 98 without these problems?

If you actually have a "ton" of bad sectors you've got no business trying to install anything. Assuming Win98 is causing your problems and the hard drive is OK, why start with the least capable and most out-of-date O/S you have??? The answer to your question here is 137gb is the partition limit for Win98SE (Win98 was 64gb).

> **mfgamer said:**
> 
I have the install disks for Windows XP SP3 and Win98SE, but everything I've read says that it's much easier to set up a multiboot if you install 98 first.

This is partially true, but XP will install easier and more reliably than Win98 any day.

Clearly - you're a novice. That's OK and I'm not saying that as any kind of insult. I just think you've jumped a bit farther ahead of your current knowledge and you need to slow down a little bit. This is not an easy task you've set for yourself and you will have some learning to do. I have no doubts you will be able to get it done - just take your time.

I suggest you try the following steps:
1. Determine your actual set-up and verify it's function - 1 or 2 drives and are they correctly set in bios?
2. Verify your hard drives are free of bad sectors. There are numerous tools available for free download that can do this for you. Your bootable Ubuntu CD has the tools you need on it.
3. Re-visit the thought that you actually need Win98 for anything that you can't do with XP instead. If you're just used to using 98, there's no time like now to let it go. If you *have* to keep it, OK but don't keep it for nostalgic reasons.
4. IF you indeed have 2 physical hard drives AND need to keep both 98 and XP - I suggest this:
a. Plan your install *in advance on paper* based on size needs. Ubuntu needs 16gb give or take for a full install (with plenty of room for programs) and not much more. XP at least 20gb plus programs and 98 15gb plus programs.
b. Boot to your Ubuntu LiveCD and use "gparted" to correctly partition and verify your drives. Make the first primary partition on each drive for windows and leave them unformatted. Make your 98 partition less than 137gb to avoid the bug you encountered before. Make a second primary partition on each drive of 1gb (why will come later) and the rest on both drives extended/logical and divide up the way you want. I suggest one logical partition of 16gb for Ubuntu, and divide the remaining into two partitions for your data - one for linux **/home** and one for windows **drive E:**. Format the drive E: partition as vfat (keep it small - like 10gb) and the linux one as ext3 or reiserfs. Format the two 1gb partitions (one on each drive) as linux swap.
c. Install Win98 to the first primary partition on one drive and 98 to the first primary partition on the other drive. The install program for both versions of windows allow you to select a partition to install to - take the time to do it. If your bios allows you to change your boot order - great! Just install XP, change drive order and install 98. If not, you may find it easier to open the case and do some manual re-arranging to do this. 
d. Once these both are installed and working and bootable - Install Ubuntu to the logical partition you have made for it. Again - take the time to make sure you're using the correct partitions - set the second ext3 partition you made for /home and the two 1gb partitions as swap.
e. When you install the GRUB bootloader from the Ubuntu install - it should see both windows installs and set them up for booting.

If you do all these steps correctly you should end up with:

A GRUB menu with Ubuntu, WinXP, and Win98 in it.

When you boot to either windows install, all the linux partitions will be "invisible" to windows. The other (not booted) windows install should be D: and vfat partition you made will be E:. This could be reversed depending on locations of the partitions.

Ubuntu will see all the partitions and allow read and write access to them all. The two swap partitions should be automatically used by the Ubuntu installer and the reason to use a separate partition for /home is to preserve your personal settings and data if you "break" your Ubuntu install and want to re-install it.

An easier way - if you are willing to give up Win98 and you do have two drives - Let WinXP have one whole drive and Ubuntu the other.

---

### Post by meouy on 2010-02-10
> **mfgamer said:**
> Is there a size/format of partition that I can create to install 98 without these problems?

The max partition size for Win98 is 127.53 GB. See _[Microsoft Technet: Table 3.11 FAT32 Size Limits]("http://technet.microsoft.com/en-us/library/cc938432.aspx")_ and [_Wikipedia File Allocation Table: FAT32_.]("http://en.wikipedia.org/wiki/File_Allocation_Table#FAT32") Also, some original versions of Win98 had an FDISK that reported wrong sizes for hard drives over 64GB (see the _[MS knowledge base article]("http://support.microsoft.com/kb/263044")_ for how to spot if you have this problem with your Win98 FDISK). Also, if your drive is over 137 GB then Win98's own FDISK program can't partition it properly anyway (see [48bitlba.com]("http://www.48bitlba.com/win98.htm"))

This is what you could do to put all three OS's on the drive. It will lose all partitions and data on the drive (from your question it seems like you're OK with that because you think you already have)

[LIST]
[*]create a 5 GB FAT32 partition for Win98 (the size depends on what you want to use it for; create whatever size you think you need), reboot and then format the partition and install Win98. Don't do this with Win98's own FDISK program though, as it can't partition your drive because it's over 137GB. Use the Linux live CD's fdisk (or gparted as oshunluvr suggests), set it active and bootable, reboot and format it with Win98's format. Alternatively, use the XP setup CD to create and format a FAT32 partition during XP's setup, but then reboot it when it's done creating and formating the partition and install the Win98 on it - i.e. effectively use XP setup's fdisk/format instead of Win98's  (I *think* both those methods will work but I've not actually done them with Win98 and a drive over 137GB)
[/LIST]

[LIST]
[*]then install XP. Install it to a new partition of whatever size you want (i.e. create a new partition during XP setup). You *could* install XP to the same partition you installed 98 to but I personally wouldn't (there's probably no real solid reason not to, I just prefer not to). If you do want to though, obviously you need to have made your 98 partition bigger i.e. up 127GB
[/LIST]

[LIST]
[*]Then install Ubuntu. Tell it to use the rest of the hard drive space (or however much you want). It will install grub when it's finished and allow you to boot each OS individually.
[/LIST]
edit: Note that, because of the Win98 48bit LBA issue it would be a lot easier to install XP, then Linux and dump the Win98.

---

