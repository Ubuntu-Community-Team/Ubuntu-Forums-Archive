---
title: "Install Win 7 and Ubuntu 10.04.1"
date: 2010-12-29
forum: General Help
---

### Post by Strategist01 on 2010-12-29
Hi guys

I want to install Windows 7, as I did buy this PC to play games and I just can't in Linux - seems to be some issues with the graphics card and wine...

Anyway, I got a hold of a copy of Win 7 Ultimate 64 bit as I have a core i5 760 and 4GBs of RAM. I have a 2TB drive to install stuff onto.

Now, all I want to do is dual boot Ubuntu 10.04.1 (32 bit) which I have installed with the Win 7 Ultimate. I have read somewhere that windows should be installed first, but I didn't have a non-OEM copy of windows to install to this machine so I installed Ubuntu.

Should I create an NTFS partition for it and let it install there or what should I do? I don't want to wipe my whole drive.

Thanks.

---

### Post by Strategist01 on 2010-12-29
Ok, I booted up from a USB live CD that I had and used Gparted successfully to resize my Ubuntu partition down and make a new NTFS partition for windows to install onto.

I've attached a pic of my current partition table using GParted.[ATTACH]179594[/ATTACH]

Now I just have to see if windows will recognize it...

---

### Post by rvchari on 2010-12-29
if i am not moistaken, win7 or for that matter any windows will prefer to be installed on primary partition thats c:. if u have ubuntu installed then you might have problems.

if you have win7 handy with you then its always better to use g-parted, alllocate sda1 for windows and sda5 onwards for ubuntu / , home / swap etc. i have always heard that woindows has to be installed first and then install ubuntu....

i ve been following what i ve been taught and i have always followed that as a safe method !

---

### Post by wilee-nilee on 2010-12-29
> **Strategist01 said:**
> Ok, I booted up from a USB live CD that I had and used Gparted successfully to resize my Ubuntu partition down and make a new NTFS partition for windows to install onto.

I've attached a pic of my current partition table using GParted.[ATTACH]179594[/ATTACH]

Now I just have to see if windows will recognize it...

Not sure what the sda1 tiny bios grub partition is, but you need a bootflag on the ntfs for the disc to recognise it.

---

### Post by Strategist01 on 2010-12-29
Hi guys.

I booted up windows using the DVD and after selecting the language and reading the EULA, it asks me where to install windows to. It sees the partition table that I made and I selected number 3, the NTFS partition. I tried to continue, but it said that Windows could not be installed because it is of the GPI partition style. What does that mean and how can I resolve it?

I've also posted in the Microsoft forums, incase that might help [http://social.answers.microsoft.com/Forums/en-US/w7install/thread/a19f5354-1f29-4891-b7b3-edf2896577bf](http://social.answers.microsoft.com/Forums/en-US/w7install/thread/a19f5354-1f29-4891-b7b3-edf2896577bf)

---

### Post by Strategist01 on 2010-12-29
> **wilee-nilee said:**
> Not sure what the sda1 tiny bios grub partition is, but you need a bootflag on the ntfs for the disc to recognise it.

Ok, I put a bootflag onto the NTFS partition. The tiny grub partition is for well...grub I assume.

I know I should have installed it onto an sda1 partiton, however I only had Ubuntu to get it working, so I could only install Ubuntu.

---

### Post by Strategist01 on 2010-12-29
Ok, I tried for the second time. I got the following error messages:
"Windows cannot be installed to this disk. The selected disk is of the GPT partition style"
"Windows cannot be installed onto this hard disk space. The partition is and EFI system partiton (ESP)."

I've had a look about the GPT type of disk, and unfortunately you can only change is to the other type of disk which allows only 4 partitions if you erase the whole HDD and start over :(

---

### Post by Mark Phelps on 2010-12-29
> **Strategist01 said:**
> Ok, I tried for the second time. I got the following error messages:
"Windows cannot be installed to this disk. The selected disk is of the GPT partition style"

Means basically that you have "too many" partitions.  MS Windows PCs limit the number of Primary partitions to 4 -- or -- three Primary partitions and an Extended partition.

With older Windows OSs, if you tried to add more partitions, it just wouldn't work.  But with Win7, it appears to change the partitioning to GPT -- to allow the extra partitions.

To get around the limit, you would need to create an Extended partition and move your Ubuntu partitions inside there.  Once you have done that, you should be able to wipe the other partitions and install Win7.

---

### Post by Strategist01 on 2010-12-29
> **Mark Phelps said:**
> Means basically that you have "too many" partitions.  MS Windows PCs limit the number of Primary partitions to 4 -- or -- three Primary partitions and an Extended partition.

With older Windows OSs, if you tried to add more partitions, it just wouldn't work.  But with Win7, it appears to change the partitioning to GPT -- to allow the extra partitions.

To get around the limit, you would need to create an Extended partition and move your Ubuntu partitions inside there.  Once you have done that, you should be able to wipe the other partitions and install Win7.

Hi.

How would I go about doing this extended partition? and then moving the other partitions into there? I was really just thinking of backing up my important files, maybe /var/cache/apt/ wiping the drive so that it has no partition tables and then installing win 7 and ubuntu afterwards so that they play nicely. Out of interest, I can't just copy the files form the CD into the NTFS partition and expect it to work, yes?

---

### Post by srs5694 on 2010-12-29
I'm afraid Mark is a bit off base. Windows will not install to a GPT disk on BIOS-based computers; Windows does not switch to GPT when you use more than four partitions. Furthermore, given that the disk is already in GPT format, you can't create an extended partition on the disk, at least not without abandoning GPT; GPT doesn't use the primary/extended/logical partition distinction.

I see four options:


[list=1]
[*]Forget about Windows. Just keep using Linux the way it is.
[*]Wipe everything and start over. Do not do this using the Windows installer, since I suspect it won't completely wipe the GPT data. (I've not tested this myself, though.) Use GParted in Linux to create a fresh MBR partition table. (I believe GParted refers to it as an MSDOS partition table.) If you've not spent a lot of time customizing Linux, this is the way forward that requires the least learning -- but not the least effort.
[*]Convert GPT to MBR. You can use my [GPT fdisk (gdisk or sgdisk)](http://www.rodsbooks.com/gdisk/) program to convert from GPT to MBR without destroying your Linux installation. (Do not use the version of GPT fdisk that ships with Ubuntu; it's hopelessly out of date. Download the latest version from [its Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/)) See my [Converting to or from GPT](http://www.rodsbooks.com/gdisk/mbr2gpt.html) page, and in particular the "Converting from GPT to MBR" section. Ensure that your NTFS partition is primary, and try to make at least one of the others a logical partition. You can omit /dev/sda1 (it's useless in an MBR scheme). After you do this conversion, chances are your system won't boot; you'll need to use [Super GRUB Disk](http://www.supergrubdisk.org/) to boot again, then re-install GRUB. Despite the learning required to do it properly, this is probably the best and quickest approach, unless your current Ubuntu install is still very generic, in which case option #2 might be quicker, once you take into account the learning required to do this option.
[*]Create a [hybrid MBR.](http://www.rodsbooks.com/gdisk/hybrid.html) These are ugly and dangerous, but they're very convenient. A hybrid MBR is probably the easiest way forward in your position; you probably won't have to re-install a boot loader or mess with your Ubuntu installation, and the rules are simpler than those for converting to a conventional MBR. You can create one with GPT fdisk; just be sure it includes the NTFS partition and nothing else, and be sure that Windows doesn't modify the partition table. Despite being an easy way forward, hybrid MBRs are, as I said, ugly and dangerous, as detailed on the hybrid MBR page to which I linked.
[/list]


One other comment: If you take options #2, #3, or #4, I recommend you move the Linux swap partition so that it's adjacent to the Linux root (/) partition; this will minimize head movements when accessing swap. (You can move the swap partition using GParted. Delete the NTFS partition, move swap, and create new partitions for Windows at the free space at the end of the disk.) Also, it's wise to include a separate NTFS data-exchange partition between the Linux partitions and the Windows boot partition. (Include this partition in the hybrid MBR if you go with option #4.) This way, you won't need to access the Windows boot partition from Linux; such accesses are always at least a bit risky. If you start over from scratch (option #2), make Windows the first partition. If not, leave Linux where it is; that's simpler and safer than trying to move it.

---

### Post by srs5694 on 2010-12-29
> **Strategist01 said:**
> How would I go about doing this extended partition? and then moving the other partitions into there?

You've got a GUID Partition Table (GPT) disk, which doesn't use extended partitions, so you *can't* create an extended partition -- at least, not without first converting the disk to use the older Master Boot Record (MBR) form, as described in my previous post. If you convert the disk by starting from scratch, you can create an extended partition (and logical partitions within it) as new partitions. If you convert using GPT fdisk, the conversion process will give you options, depending on the number of partitions and what's possible. (There are technical restrictions on the placement of logical partitions that can limit the possibilities.)

> I was really just thinking of backing up my important files, maybe /var/cache/apt/ wiping the drive so that it has no partition tables and then installing win 7 and ubuntu afterwards so that they play nicely.

There's no point in backing up /var/cache/apt if you'll be re-installing Ubuntu again from scratch; that directory holds information on the installed packages, so restoring it to a new installation will just make for hopeless confusion and a need to re-install *again*. If you want to re-create the packages you've installed, there are ways to do this, but I don't recall the exact commands required offhand. Basically you need to export a list of installed packages to a file and then, after re-installing, feed that file into apt-get to have it re-install all the packages it hasn't already installed.

> Out of interest, I can't just copy the files form the CD into the NTFS partition and expect it to work, yes?

Correct; that will yield a completely unbootable partition. To get a bootable copy of Windows, you've got to install from the Windows CD or DVD, or restore a backup of a working system using a backup utility.

---

### Post by Strategist01 on 2010-12-29
> **srs5694 said:**
> I'm afraid Mark is a bit off base. Windows will not install to a GPT disk on BIOS-based computers; Windows does not switch to GPT when you use more than four partitions. Furthermore, given that the disk is already in GPT format, you can't create an extended partition on the disk, at least not without abandoning GPT; GPT doesn't use the primary/extended/logical partition distinction.

I see four options:


[LIST=1]
[*]Forget about Windows. Just keep using Linux the way it is.
[*]Wipe everything and start over. Do not do this using the Windows installer, since I suspect it won't completely wipe the GPT data. (I've not tested this myself, though.) Use GParted in Linux to create a fresh MBR partition table. (I believe GParted refers to it as an MSDOS partition table.) If you've not spent a lot of time customizing Linux, this is the way forward that requires the least learning -- but not the least effort.
[*]Convert GPT to MBR. You can use my [GPT fdisk (gdisk or sgdisk)]("http://www.rodsbooks.com/gdisk/") program to convert from GPT to MBR without destroying your Linux installation. (Do not use the version of GPT fdisk that ships with Ubuntu; it's hopelessly out of date. Download the latest version from [its Sourceforge download page.]("http://sourceforge.net/projects/gptfdisk/files/")) See my [Converting to or from GPT]("http://www.rodsbooks.com/gdisk/mbr2gpt.html") page, and in particular the "Converting from GPT to MBR" section. Ensure that your NTFS partition is primary, and try to make at least one of the others a logical partition. You can omit /dev/sda1 (it's useless in an MBR scheme). After you do this conversion, chances are your system won't boot; you'll need to use [Super GRUB Disk]("http://www.supergrubdisk.org/") to boot again, then re-install GRUB. Despite the learning required to do it properly, this is probably the best and quickest approach, unless your current Ubuntu install is still very generic, in which case option #2 might be quicker, once you take into account the learning required to do this option.
[*]Create a [hybrid MBR.]("http://www.rodsbooks.com/gdisk/hybrid.html") These are ugly and dangerous, but they're very convenient. A hybrid MBR is probably the easiest way forward in your position; you probably won't have to re-install a boot loader or mess with your Ubuntu installation, and the rules are simpler than those for converting to a conventional MBR. You can create one with GPT fdisk; just be sure it includes the NTFS partition and nothing else, and be sure that Windows doesn't modify the partition table. Despite being an easy way forward, hybrid MBRs are, as I said, ugly and dangerous, as detailed on the hybrid MBR page to which I linked.
[/LIST]


One other comment: If you take options #2, #3, or #4, I recommend you move the Linux swap partition so that it's adjacent to the Linux root (/) partition; this will minimize head movements when accessing swap. (You can move the swap partition using GParted. Delete the NTFS partition, move swap, and create new partitions for Windows at the free space at the end of the disk.) Also, it's wise to include a separate NTFS data-exchange partition between the Linux partitions and the Windows boot partition. (Include this partition in the hybrid MBR if you go with option #4.) This way, you won't need to access the Windows boot partition from Linux; such accesses are always at least a bit risky. If you start over from scratch (option #2), make Windows the first partition. If not, leave Linux where it is; that's simpler and safer than trying to move it.

Ok, I think I will go for number 3, as I don't have to wipe the drive as a I feared. Of course, as I have backed up my important stuff, it won't be a tragedy if I lose data. 1 is not an option and I don't want to do number 4 as it sounds well...a bit too risky. I make the NTFS partition primary by adding a boot flag, yes?

EDIT: I've had a look through your pages of the gdisk utility, and it seems like I won't need to create a logical partition as I only have 4 partitions?

---

### Post by srs5694 on 2010-12-29
> **Strategist01 said:**
> I make the NTFS partition primary by adding a boot flag, yes?

No. The boot/active flag is independent of primary/extended/logical status, at least in terms of the data structures. (The data structures permit flagging extended and logical partitions as boot/active, but doing so is rather pointless; boot loaders that use this feature typically only look for such flags on primary partitions.)

A primary partition is one of the four partitions defined in the main MBR data structures. This contrasts with a logical partition, which is defined as part of an extended partition's data structures (an extended partition being a special type of primary partition). When you use gdisk to convert from GPT to MBR, it will assign partitions as either primary or logical. You can sometimes change at least some of these assignments, but this depends on the exact disk layout.

> EDIT: I've had a look through your pages of the gdisk utility, and it seems like I won't need to create a logical partition as I only have 4 partitions?

An MBR disk can have up to four primary partitions, so if you want to convert four or fewer partitions and no more, you don't *need* to use logical partitions; however, because of that limit on primaries and the fact that an extended partition to house logical partitions is itself a primary partition, my general recommendation is to make as many partitions logical as possible. If you've got four partitions precisely, try as hard as possible to make at least one of them logical; that way you'll have the extended partition should you need it for future adjustments. Windows must boot from a primary partition and primary partitions cannot reside between logical partitions, though, and these facts combine with your current layout to impose limits on what may and may not be primary vs. logical.

---

### Post by Strategist01 on 2010-12-29
Ok, Here's the output of the gdisk program after going r and then g:
Number    Boot    Size       Status   Logical   Code   GPT Name
   1             1024.0 KiB  primary     Y       EF    
   2             878.9 GiB   primary     -       07    
   3             974.0 GiB   primary     Y       EF    Basic data partition
   4             10.1 GiB    primary     -       82    

Also, how would I use the super grub file? Must I convert it to an .iso before burning? It seems like it's a bootable thing, but I'm not sure. Also, I had a look and it seems that the NTFS partition is primary.

---

### Post by Strategist01 on 2010-12-29
Ok, so I have proceeded with number 3 and I made it into an MBR disk, succesfully installed windows 7 onto the 3 partition, /dev/sda3/ and Windows 7 boots up. However, of course, I have no grub to boot linux up. Now I need to re-install it. I am looking on the grub disk wiki and I might have found a solution, Auto super grub disk? However I can't find the DL link :/

---

### Post by Norcalli on 2010-12-29
The way I did it yesterday that works fully is to do the following so that we could have GRUB and dual boot:
1. Set up your partitions (e.g. /dev/sda1 = linux, /dev/sda2 = windows )
2. Install ubuntu on /dev/sda1.
3. Boot into ubuntu and do all you want, then make a backup of your mbr using the following ( you don't have to worry about dd-ing from the partition you are running from since you are just reading):
```
sudo dd if=/dev/sda of=./mbr.bin bs=446 count=1
```
Put that somewhere where you can reach it on your live cd, i.e. email it to yourself...
4. Now install windows onto the partition /dev/sdb (or w/e you made) and wait for the install to finish.
5. Reboot into you live cd and do the following to restore your mbr:
```
sudo dd if=./mbr.bin of=/dev/sda bs=446 count=1
```
6. Reboot into your ubuntu and run
```
sudo update-grub
```
so that the grub can read the windows into the menu.
7. Enjoy!

---

### Post by srs5694 on 2010-12-29
> **Strategist01 said:**
> Ok, so I have proceeded with number 3 and I made it into an MBR disk, succesfully installed windows 7 onto the 3 partition, /dev/sda3/ and Windows 7 boots up. However, of course, I have no grub to boot linux up. Now I need to re-install it. I am looking on the grub disk wiki and I might have found a solution, Auto super grub disk? However I can't find the DL link :/

My original post laying out the options includes a link to the Super GRUB Disk site. Download the appropriate disc image (probably Super GRUB 2 Disk) and use it to boot Ubuntu. You can then re-install GRUB by typing "sudo grub-install /dev/sda" at a shell prompt.

---

### Post by Strategist01 on 2010-12-30
> **srs5694 said:**
> My original post laying out the options includes a link to the Super GRUB Disk site. Download the appropriate disc image (probably Super GRUB 2 Disk) and use it to boot Ubuntu. You can then re-install GRUB by typing "sudo grub-install /dev/sda" at a shell prompt.

I did try to use it, but it was an .img file and when I burned it onto a CD it just gave me a file, not the contents. I don't know how to deal with this .img file. I know that it works, but must I use Pendrive linux to install it onto a USB or something?

---

### Post by srs5694 on 2010-12-30
I don't know what you're trying to download; the download links on [this page](http://www.supergrubdisk.org/category/download/supergrub2diskdownload/) are to .iso files. I haven't burned a new copy in a while, but I just used cdrecord:

```

cdrecord filename.iso

```

Change "filename.iso" to the filename you want to burn, of course.

---

### Post by srs5694 on 2010-12-30
Oh, of course if you're doing this from Windows you'd need to use Windows CD-R-creation software. Most such programs have options to burn from an image file, so use that option.

---

### Post by Strategist01 on 2010-12-30
I Downloaded super grub disk 1, which came to me as an .img. The file at that link is an .iso which should be easy enough to burn :)

---

### Post by srs5694 on 2010-12-30
The last two or three releases of Ubuntu have used GRUB 2 as the default boot loader, so you'd need the GRUB 2 version of Super GRUB Disk. If you know for a fact that you're using GRUB Legacy, then you'd need the GRUB Legacy version of Super GRUB Disk.

---

### Post by Strategist01 on 2011-01-17
Sorry for the late reply. I was stuck in Windows and was exploring it and getting it set up the way I want it :D.

I burned the .iso to a disk, and then booted into Ubuntu. When in Ubuntu I ran:
```
sudo update-grub
```

And it updated grub and now I am able to boot into Win 7 and Ubuntu. Thanks so much everyone!

---

### Post by Strategist01 on 2011-01-17
Actually, that didn't work for me. It was because I had used super grub  disc to bot into Ubuntu that I thought it was working. What I actually  had to do was boot into Ubuntu and then put

```
sudo install-grub /dev/sda
```

into the terminal. It did that w/o any problems and I was able to boot into both with out the CD. Thanks!

---

