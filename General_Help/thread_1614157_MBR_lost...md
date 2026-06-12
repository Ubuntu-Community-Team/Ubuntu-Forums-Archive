---
title: "MBR lost.."
date: 2010-11-05
forum: General Help
---

### Post by sojukrishna on 2010-11-05
hi everyone...
i have a problem. My HP notebook came with windows 7 os. Later i tried to install ubuntu netbook , but could not. It has two drives c:/ with 140gb and d: with 15gb<which was recovery drive>. The problem whwn creating a new disk drive was some sort of dynamic disk...so i installed partition magic, was had a compatibilty issue with win 7. the d: recovery drive was completely lost.After this incident, i tried to start my notebook, it was a blank screen(BSOD). After trying out LiveCD 10.04 in usb, i found that partition table has gone..but data are intact.
So i need to get my windows back, by editing the mbr. I don hv any recovery disk..but only the diff ubuntu version..pls help me further and tell me how to get back windows n install ubuntu.:)

---

### Post by oldefoxx on 2010-11-05
The MBR is of course the Master Boot Record, an add-in that Microsoft came up with back when viruses were coming out that actually attacked the boot record so that each time you rebooted, the virus was on board.  Then they used the MBR as a clone to be copied over the boot record to restore it.

Since those early times, people only talk of the MBR as being essential, which does not square with my memory, but things have a way of changing on you. so I won't stamd by my statement in this regard.

So now you have a problem. wjich is to junk what you had and just go with some distro of Linux. try to dump Linux and get back to what you had before with Windows 7,  or somehow save your data and then make your decision about windows 7 and/or Linux.

Losing the Recover Disk, while not good. is not as terrible as it might seem to be.  If you fell back on it, it would scratch all your data and just put you back on a from-the-OEM configuration anyway. meaning all data lost.  You seem to want to avoid that anyway.

Actuslly, what you seem to have lost is Windows 7, or at least a way to boot right into it.  But it might still be accessable as an alternate drive.  That could mean that you can boot up using s CD/DVD/USB mounted image and access the original drive from there.  With the right range of applications under Linux, you might find that an immediate benefit.

Before OEMs adopted the model of a hidden D: drive with all the original software on it. they offered a set of CDs to reinstall the original software.  Some still sell sets of CDs in case the whole drive fails and you have to start from scratch.  Microsoft even provides alternate ways of restoring the system files and leaving the data intact, all from the same set of CDs.  In other words, the vender you bought from may be your best choice for immediate fixes.  Best Buy has its Geek Squad, and there may be a shop at hand that knows the best methods for getting your data back.  I'm not saying you can't do it, but your range of options has been drastically reduced.

Fact is, it works out in my head that you may have made a few initial decisions that are working against you now.  It can be risky to jump ahead to adding Ubuntu to your stable without performing a full backup before starting, and trusting a program to make the best choices for you means that you entrust the programmer to have known in advance exactly what your requirements might be/  It takes more effort, but I don't like settling for default settings when attempting something so impactive on my PC.  I need a place to get back to in case trouble crops up.  In fact,
my first choice for a backup is the same install on another partition so
that I have an alternate boot path from the word go.

---

### Post by wilee-nilee on 2010-11-05
Post the text from running the bootscript in my signature. Post it in code tags by clicking on the # in the reply window. You will see this [ code] [ /code] put the text between.

In the mean time download this W7 recovery disc and burn a cd.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Personally I don't care what OS you use but am more towards just getting you back what you want.

I would agree with oldefox on the backup schema except I put my HD images on a external HD.

---

### Post by Mark Phelps on 2010-11-05
> **sojukrishna said:**
> pls help me further and tell me how to get back windows n install ubuntu.:)

BEFORE you installed Ubuntu, you should have used the Win7 Backup feature to create a burn a Win7 Repair CD.  That does NOT reformat your drive, but instead, allows you to repair boot problems -- like you have right now.

Since you probably did not do that, go to the link below, download and burn the proper Win7 repair CD, boot into it, and run Startup Repair three times -- that's right, three times.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

That SHOULD get you back into booting into Win7.

When you have that working, you will need to reinstall GRUB -- but that is later.

---

### Post by alphaamanitin on 2010-11-05
> **Mark Phelps said:**
>  run Startup Repair three times -- that's right, three times..

Why is three times necessary?  

AlphaA

---

### Post by GnomeShaman on 2010-11-05
> **sojukrishna said:**
> hi everyone...
i have a problem. My HP notebook came with windows 7 os. Later i tried to install ubuntu netbook , but could not. It has two drives c:/ with 140gb and d: with 15gb<which was recovery drive>. The problem whwn creating a new disk drive was some sort of dynamic disk...so i installed partition magic, was had a compatibilty issue with win 7. the d: recovery drive was completely lost.After this incident, i tried to start my notebook, it was a blank screen(BSOD). After trying out LiveCD 10.04 in usb, i found that partition table has gone..but data are intact.
So i need to get my windows back, by editing the mbr. I don hv any recovery disk..but only the diff ubuntu version..pls help me further and tell me how to get back windows n install ubuntu.:)


See **Partitionwizard** as an alternative to magic. You can recover you partition table with this (Bootable USB or CD)

I'm not quite sure how far you got with the ubuntu installation or if it installed grub. However, the MBR is located on a hidden 100MB partition created during windows 7 install.

If you look here: [http://www.mydigitallife.info/2010/04/28/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/2010/04/28/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)    you will find a list of windows 7 .iso ; read the information and download the version applicable your license ..

Boot from the 7 media and repair. Go to an elevated command prompt and type

[B]bootrec.exe /fixmbr
bootrec.exe /fixboot
bootrec.exe /rebuildbcd[/B]

Exit and restart.

---

### Post by garvinrick4 on 2010-11-05
Windows 7 in HP gives you a chance to burn 3 dvds of the original 7 operating system and you can make recovery disks at any time but only one chance at the operating system disks. It is in your applications list just hit windows key and look for. Takes just a jiffy to make a recovery disk. You will have to run the boot script willee-nillee asked for because you might have and independent boot partition. Probably so and that has to be mounted when installing grub2 to system. Give the boot script and you will be up and running.
If you flat cannot get a windows repair disk. Run this in terminal: IN UBUNTU install cd and 
choose try Ubuntu.(called a live cd) Open a terminal: Applications to Accessories to terminal.
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```will show a few errors ignore just need mbr portion
Now boot into hard drive of Windows.
Now boot off of Ubuntu cd and follow below: Sorry to be redundant but if you want to get straighted out this is essential for these guys.
To run boot script COPY this file to DESKTOP and then run this code below and will put a file called RESULTS on desktop copy and paste in this thread with code tags.refer willee-nillee
 
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/")

```
sudo bash ~/Desktop/boot_info_script*.sh 
```

---

### Post by wilee-nilee on 2010-11-05
> **alphaamanitin said:**
> Why is three times necessary?  

AlphaA

This might help.
[http://www.sevenforums.com/tutorials/105541-startup-repair-run-3-separate-times.html](http://www.sevenforums.com/tutorials/105541-startup-repair-run-3-separate-times.html)

---

### Post by nl4m on 2010-11-05
I'll walk you through reinstalling Grub the MBR.

1. Boot into the CD.
2. Launch the Terminal
3. Find the partition that Ubuntu is on (sda5, was it?) type in small letters: SUDO CAT /PROC/PARTITIONS 
4. To mount the Ubuntu partition from the HDD, type in small letters:  SUDO MOUNT /DEV/SDA5 (or whatever the partition is) /HOME/(user  name)/Desktop (<capital "D" in "Desktop")
5. Make sure you are connected to the internet and type in small  letters: SUDO GRUB-INSTALL --ROOT-DIRECTORY=/HOME/(user name)/Desktop  (<capital "D" in "Desktop") /DEV/SDA (only "sda" without the number  "5" at the end)
6. Check device map: CAT /BOOT/GRUB/DEVICE.MAP
7. To unmount type in small letters: SUDO UMOUNT /HOME/(user name)/Desktop (< Capital "D" in "Desktop")
8. Reboot 
I think the "(username)" is "Ubuntu". In case I'm wrong you can change  "/home/(user name)/Desktop" to "/home/$(whoami)/Desktop" < That will  fill in the user name for you.

---

### Post by garvinrick4 on 2010-11-06
n14m,
Please put your code in code tags highlight and hit # sign in upper right of message box 
Please use lower case for lower case and upper case for uppercase there are a lot of
code that use both in linux. example:
```
sudo mkdir /media/root
``````
sudo mount /dev/sda5 /media/root
``````
sudo grub-install --root-directory=/media/root /dev/sda
``````
sudo umount /media/root
```Made a directory
mounted sda5
installed grub in sda looking in sda5 for grub
unmounted sda5 (umount in code right.
Thanks n14m

---

### Post by srs5694 on 2010-11-06
> **sojukrishna said:**
> hi everyone...
i have a problem. My HP notebook came with windows 7 os. Later i tried to install ubuntu netbook , but could not. It has two drives c:/ with 140gb and d: with 15gb<which was recovery drive>. The problem whwn creating a new disk drive was some sort of dynamic disk...so i installed partition magic, was had a compatibilty issue with win 7. the d: recovery drive was completely lost.After this incident, i tried to start my notebook, it was a blank screen(BSOD). After trying out LiveCD 10.04 in usb, i found that partition table has gone..but data are intact.
So i need to get my windows back, by editing the mbr. I don hv any recovery disk..but only the diff ubuntu version..pls help me further and tell me how to get back windows n install ubuntu.:)

I recommend you begin by booting the Ubuntu CD in live CD mode, opening a Terminal (text-mode shell program), and typing the following command:

```

sudo fdisk -lu

```

Post the results here, between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string. This will tell us what your partition table looks like right now. (Your claim that the "partition table has gone" is vague and imprecise; several different observations could lead to that claim, each with a different cause. The fdisk output is much more precise.) The best approach to recovery depends on the precise nature of the problem. Others have posted some suggestions, but I'll refrain from doing so until I have firmer data.

[quote=oldefoxx]The MBR is of course the Master Boot Record, an add-in that Microsoft came up with back when viruses were coming out that actually attacked the boot record so that each time you rebooted, the virus was on board. Then they used the MBR as a clone to be copied over the boot record to restore it.

Since those early times, people only talk of the MBR as being essential, which does not square with my memory, but things have a way of changing on you. so I won't stamd by my statement in this regard.[/quote]

I'm afraid this is completely mixed up. The [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) is the first sector of a hard disk, which normally holds two critical items: The primary partition table (which defines up to four primary partitions) and the stage0 boot loader code. Many early viruses wrote themselves over the stage0 boot loader code, but the MBR was not a defensive response to viruses, as you claim, nor does it offer anything in the way of virus defenses; most viruses were written well after the MBR as we know it today came into being. (Details of MBR data structures have changed over the years, though.)

Other partitioning systems, such as the Apple Partition Map (APM), GUID Partition Table (GPT), and BSD disklabels, do exist and don't use the first sector of the disk in quite the same way as it's used on MBR disks. (GPT includes a "protective MBR" to keep MBR-only disk utilities from damaging the disk, though.) If you're using such a disk, MBR is not necessary; but for the vast majority of x86- or x86-64-based computers, an MBR is absolutely vital.

---

### Post by alphaamanitin on 2010-11-06
If your partition table is gone you can try TestDisk.  A great free utility that can rebuild partition tables, scan hard drives to find what kind of partitions and format was there before, and try to rebuild, or simply recover files.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

By the way, Super Grub can get you booted into drives that have a damaged boot loader.  I have been able to boot into linux, Windows XP, and Windows Vista using Super Grub after damaging the MBR.  

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)


AlphaA

---

