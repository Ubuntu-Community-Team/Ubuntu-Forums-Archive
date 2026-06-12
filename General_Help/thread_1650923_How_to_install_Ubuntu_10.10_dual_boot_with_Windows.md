---
title: "How to install Ubuntu 10.10 dual boot with Windows 7"
date: 2010-12-22
forum: General Help
---

### Post by soltero5965 on 2010-12-22
Hello i've tried this once but it made my desktop inoperable maybe along the installation some things went wrong.
I have this MSi all in one touchscreen desktop model AIO 2010 with  windows 7 home premium installed on it and i want to dual boot with  ubuntu 7 
Is there any step by step guide on how to do it properly?
    
MSi All in one model AIO 2010

AMD Athlon(tm) X2 Dual core Processor 3250e
Hard disk is sata 320 g
ATI Radeon HD 3200 Graphics

any help on how to properly install Maverick Meerkat
Thank you!

---

### Post by tajiknomi on 2010-12-22
[SIZE=2]You should install windows before installing Ubuntu, because once you had install Ubuntu and after that, you want to install Wndows, it will **overwrite** your MBR and then you had to install  your **Grub** again...

For more info > [/SIZE][https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[SIZE=2]Edit:- Maverick Step-by-Step installation[/SIZE] > [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)


[SIZE=2]Good Luck :p
[/SIZE]

---

### Post by sikander3786 on 2010-12-22
There have been some guides listed in the above post.

In addition to that, we can try to guide you step by step. No problem. Just keep us providing the information we need and keep on asking the queries step-by-step.

Firstly, in order to see you current partition setup, boot an Ubuntu Live CD/USB, choose the Try mode and from Applications > Accessories > Terminal, post the output of this command.

```
sudo fdisk -lu
```

You don't need to have Dynamic Discs in Windows. Partitions need to be basic if you want to install Linux. That output would tell us.

And also once booted Ubuntu Live, test all your hardware with it ;-)

---

### Post by Kirboosy on 2010-12-22
There is always Wubi install. The only limitation is you max out Ubuntu at 30 Gb. But if you are just messing with it and you don't know if you want to give it more space its perfect. And it doesn't require Grub so it reduces the risk of breaking Windows.

The other nice thing is if you decide Ubuntu isn't what you want you can always uninstall it via the control pannel --> Programs and Features. Its like a normal windows program. (You still have to reboot to use Ubuntu normally though)

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

If the computer is powerful enough you can always run Ubuntu in Virtualbox... which then gives you the capability to run them simultaneously :)

[http://www.virtualbox.org](http://www.virtualbox.org)

---

### Post by soltero5965 on 2010-12-22
> **tajiknomi said:**
> [SIZE=2]You should install windows before installing Ubuntu, because once you had install Ubuntu and after that, you want to install Wndows, it will **overwrite** your MBR and then you had to install  your **Grub** again...

For more info > [/SIZE][https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[SIZE=2]Edit:- Maverick Step-by-Step installation[/SIZE] > [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)


[SIZE=2]Good Luck :p
[/SIZE]

Well as i said i already have windows 7 pre installed what i need is a step by step guide on dual boot installation of Ubuntu 10.10 not like when i have vista on my laptop and have dual boot install Ubuntu 10.04 i did not have any problem because Ubuntu did it all for me less some basic info input on the installation but with windows 7 and installing Ubuntu 10.10 it is not the same..i am no techno guy here i already mess with one of this machine so i would ask and listen and/or read first before i do it..thanks!

---

### Post by soltero5965 on 2010-12-22
> **Caboose885 said:**
> There is always Wubi install. The only limitation is you max out Ubuntu at 30 Gb. But if you are just messing with it and you don't know if you want to give it more space its perfect. And it doesn't require Grub so it reduces the risk of breaking Windows.

The other nice thing is if you decide Ubuntu isn't what you want you can always uninstall it via the control pannel --> Programs and Features. Its like a normal windows program. (You still have to reboot to use Ubuntu normally though)

[http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

If the computer is powerful enough you can always run Ubuntu in Virtualbox... which then gives you the capability to run them simultaneously :)

[http://www.virtualbox.org](http://www.virtualbox.org)
Well i have 320 g of hdd half for windows and half for ubuntu 10.10 i guess is fine for me and i really want ubuntu on every system i have  also i would like to see my touchscreen working in ubuntu 10.10  thanks

---

### Post by tajiknomi on 2010-12-22
> **soltero5965 said:**
> Well as i said i already have windows 7 pre installed what i need is a step by step guide on dual boot installation of Ubuntu 10.10 not like when i have vista on my laptop and have dual boot install Ubuntu 10.04 i did not have any problem because Ubuntu did it all for me less some basic info input on the installation **but with windows 7 and installing Ubuntu 10.10 it is not the same**..i am no techno guy here i already mess with one of this machine so i would ask and listen and/or read first before i do it..thanks!

[SIZE=2]i didn't get the words >which i had Mentioned in the Quote above, 

Have you did it before..? What kind a problem you face while installing or after Dual-booted Win 7 & Maverick ....?
[/SIZE]

---

### Post by Kirboosy on 2010-12-22
If the touchscreen doesn't work out of the box there are drivers you probably need to install in Ubuntu. I'm not sure what the actual screen is so I can't tell you the exact drivers....

It might even come up in the Restricted Drivers section (don't hold me to that though)

---

### Post by tajiknomi on 2010-12-22
!

---

### Post by wilee-nilee on 2010-12-22
> **sikander3786 said:**
> There have been some guides listed in the above post.

In addition to that, we can try to guide you step by step. No problem. Just keep us providing the information we need and keep on asking the queries step-by-step.

Firstly, in order to see you current partition setup, boot an Ubuntu Live CD/USB, choose the Try mode and from Applications > Accessories > Terminal, post the output of this command.

```
sudo fdisk -lu
```

You don't need to have Dynamic Discs in Windows. Partitions need to be basic if you want to install Linux. That output would tell us.

And also once booted Ubuntu Live, test all your hardware with it ;-)

OP this is the post you should take seriously it is trying to actually find what is on the computer. There are 2 HD's I believe, but there are limitations in the amount of partitions per a single HD.

---

### Post by soltero5965 on 2010-12-22
> **wilee-nilee said:**
> OP this is the post you should take seriously it is trying to actually find what is on the computer. There are 2 HD's I believe, but there are limitations in the amount of partitions per a single HD.

  **[SIZE=2][COLOR=Black]Here is it    wilee-nilee also i only have 1 HDD 320 gb and the live cd that i have got no choice of installing Ubuntu alongside with other operating system but only two, the first one is erase entire drive and the second one is advance  partition that is why i need help on this advance partitioning of my hard drive:             [/COLOR][/SIZE]**

To run a command as administrator (user "root"), use "sudo <command>". 
 See "man sudo_root" for details. 
  
 

ubuntu@ubuntu:~$ sudo fdisk -lu 
  
 Disk /dev/sda: 320.1 GB, 320072933376 bytes 
 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x35c425cc 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1            2048    30722047    15360000   27  Unknown 
 /dev/sda2   *    30722048    30926847      102400   27  Unknown 
 /dev/sda3        30926848   174286847    71680000    7  HPFS/NTFS 
 /dev/sda4       174286848   625139711   225426432    7  HPFS/NTFS 
 ubuntu@ubuntu:~$  
 
[IMG]file:///home/ubuntu/Desktop/Screenshot.png[/IMG][IMG]file:///home/ubuntu/Documents/Screenshot.png[/IMG]

---

### Post by wilee-nilee on 2010-12-22
So lets see the bootscript. The reason being is that if you want to do a dual boot with partitioning from a live cd, you have the maximum of primary type of partitions one will have to go, unless you just go Wubi, which is inside of Windows. The script will tell us what is where and where the boot info is so don't remove anything or resize yet unless you know whats up.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

This will help the others help you.

---

### Post by soltero5965 on 2010-12-22
> **tajiknomi said:**
> [SIZE=2]i didn't get the words >which i had Mentioned in the Quote above, 

Have you did it before..? What kind a problem you face while installing or after Dual-booted Win 7 & Maverick ....?
[/SIZE]
What happened on my first attempt  to install Ubuntu 10.10 dual boot with windows 7 is that it erased the entire windows 7 and left me with "Missing Bootmgr" that is why i want to install it step by step..thanks

---

### Post by wilee-nilee on 2010-12-22
> **soltero5965 said:**
> What happened on my first attempt  to install Ubuntu 10.10 dual boot with windows 7 is that it erased the entire windows 7 and left me with "Missing Bootmgr" that is why i want to install it step by step..thanks

This happened because you have the maximum amount of partitions already all Ubuntu could do was overwrite the HD.

---

### Post by soltero5965 on 2010-12-22
> **wilee-nilee said:**
> This happened because you have the maximum amount of partitions already all Ubuntu could do was overwrite the HD.
[B]
wilee-nilee[/B] is there any way to download Ubuntu 10.10 iso with that three choice to install it dual boot with Windows 7
  
1. Install alongside other operating system
  2. Erase and use entire disk
  3. Specify partitions manually(advanced)

the live cd that i download do not have this, if i have only this live cd it would be easy for a guy like me  who don't really have that technical know how on this stuff.
Thanks

---

### Post by sikander3786 on 2010-12-22
> **soltero5965 said:**
> [B]
wilee-nilee[/B] is there any way to download Ubuntu 10.10 iso with that three choice to install it dual boot with Windows 7
  
1. Install alongside other operating system
  2. Erase and use entire disk
  3. Specify partitions manually(advanced)

the live cd that i download do not have this, if i have only this live cd it would be easy for a guy like me  who don't really have that technical know how on this stuff.
Thanks
That doesn't give you all those options because you already have 4 primary partitions on your HDD. You need to delete one of them and create an extended partition there and then you'll be able to create Logical partitions inside that thus resulting in successful dual-boot between Windows and Ubuntu.

Those options would pop up in the same Live CD once you fix partitioning problems. Thats why we were asking for fdisk -lu output.

I guess you are trying to install Ubuntu at the moment but I wouldn't recommend that until you fix the partition problems otherwise, you'd once again lose Windows.

As *wilee-nilee* suggested earlier, we need to see the output of bootinfoscript in order to proceed. By not following the directions, you are making it harder for us as we have to just blindly guess your setup and answer. Let us know what is there by providing us the information we need.

---

### Post by soltero5965 on 2010-12-22
> **sikander3786 said:**
> That doesn't give you all those options because you already have 4 primary partitions on your HDD. You need to delete one of them and create an extended partition there and then you'll be able to create Logical partitions inside that thus resulting in successful dual-boot between Windows and Ubuntu.

Those options would pop up in the same Live CD once you fix partitioning problems. Thats why we were asking for fdisk -lu output.

I guess you are trying to install Ubuntu at the moment but I wouldn't recommend that until you fix the partition problems otherwise, you'd once again lose Windows.

As *wilee-nilee* suggested earlier, we need to see the output of bootinfoscript in order to proceed. By not following the directions, you are making it harder for us as we have to just blindly guess your setup and answer. Let us know what is there by providing us the information we need.
**sikander3786**
Hello i have already posted my fdisk-lu output above but just the same here it is:

To run a command as administrator (user "root"), use "sudo <command>". 
 See "man sudo_root" for details. 
```
  ubuntu@ubuntu:~$ sudo fdisk -lu 
  Disk /dev/sda: 320.1 GB, 320072933376 bytes 
 255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors 
 Units = sectors of 1 * 512 = 512 bytes 
 Sector size (logical/physical): 512 bytes / 512 bytes 
 I/O size (minimum/optimal): 512 bytes / 512 bytes 
 Disk identifier: 0x35c425cc 
  
    Device Boot      Start         End      Blocks   Id  System 
 /dev/sda1            2048    30722047    15360000   27  Unknown 
 /dev/sda2   *    30722048    30926847      102400   27  Unknown 
 /dev/sda3        30926848   174286847    71680000    7  HPFS/NTFS 
 /dev/sda4       174286848   625139711   225426432    7  HPFS/NTFS 
 ubuntu@ubuntu:~$
```

---

### Post by sikander3786 on 2010-12-22
I was talking about the boot script mentioned by *wilee-nilee* in post # 12.

Download boot script here. Instructions included.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Run it and post the output from generated Results.txt.

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read. [/code] at the end, [code] at the beginning of your text.

---

### Post by soltero5965 on 2010-12-22
> **sikander3786 said:**
> I was talking about the boot script mentioned by *wilee-nilee* in post # 12.

Download boot script here. Instructions included.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Run it and post the output from generated Results.txt.

While posting, click the # icon in post menu and paste your text in between the generated code tags to make it easy to read. [/code] at the end, ```
 at the beginning of your text.
[SIZE=2]**Hope this it:**[/SIZE]

[code]               Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    30,722,047    30,720,000  27 Hidden HPFS/NTFS
/dev/sda2    *     30,722,048    30,926,847       204,800  27 Hidden HPFS/NTFS
/dev/sda3          30,926,848   174,286,847   143,360,000   7 HPFS/NTFS
/dev/sda4         174,286,848   625,139,711   450,852,864   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        74645E90645E5548                       ntfs       BIOS_RVY                      
/dev/sda2        4C2460C82460B69C                       ntfs       System                        
/dev/sda3        901AD8491AD82E4A                       ntfs       OS_Install                    
/dev/sda4        D8D8656CD86549B8                       ntfs       Data                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda4        /media/Data              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

---

### Post by wilee-nilee on 2010-12-22
So you will need to loose a partition the sda3 which is C is set to boot by itself. sda1 is the recovery sda2 is the boot partition. sda4 looks to be D.

How full is the computer?

Chances are with a dual boot and partition removal you will probably loose the recovery partition applicability, you never know but this should be said. The reason you would loose it is we are installing another bootloader in the MBR=master boot record in a partitioned install.

Do you have the HD=C imaged and any other other stuff at this point. A image is made by using the backup utility. Best if just put on a external HD. It can be reloaded activated and all.

---

### Post by soltero5965 on 2010-12-22
> **wilee-nilee said:**
> So you will need to loose a partition the sda3 which is C is set to boot by itself. sda1 is the recovery sda2 is the boot partition. sda4 looks to be D.

How full is the computer?

Chances are with a dual boot and partition removal you will probably loose the recovery partition applicability, you never know but this should be said. The reason you would loose it is we are installing another bootloader in the MBR=master boot record in a partitioned install.

Do you have the HD=C imaged and any other other stuff at this point. A image is made by using the backup utility. Best if just put on a external HD. It can be reloaded activated and all.
The HD is not full at least it got more than 200 g more

---

### Post by wilee-nilee on 2010-12-22
> **soltero5965 said:**
> The HD is not full at least it got more than 200 g more

Okay for this to work you will need to carefully read and answer questions. This is an area where it could be damaged without correct communication. Please reread the questions and answer them to the best of your ability. 

Really I'm just trying to go methodically, we want everything in good order and no damage done. :)

Don't delete any partitions yet but answer the last questions above your last reply.

---

### Post by thefinalfrontier1701 on 2010-12-22
This is what I did for my vista machine. For 32 bit, download Ubuntu from this link: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer). Follow the instructions. As I remember, I had to mount the disc image to Alcohol 52 Percent Lite and run it. This allowed me to install Ubuntu 10.10 32 bit on my computer. At startup, I can select to load either vista or Ubuntu.

---

### Post by wilee-nilee on 2010-12-22
> **thefinalfrontier1701 said:**
> This is what I did for my vista machine. For 32 bit, download Ubuntu from this link: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer). Follow the instructions. As I remember, I had to mount the disc image to Alcohol 52 Percent Lite and run it. This allowed me to install Ubuntu 10.10 32 bit on my computer. At startup, I can select to load either vista or Ubuntu.

Read the thread wubi has been suggested at least twice, which have no problems with, just don't add to the confusion please.

---

### Post by soltero5965 on 2010-12-22
> **wilee-nilee said:**
> Okay for this to work you will need to carefully read and answer questions. This is an area where it could be damaged without correct communication. Please reread the questions and answer them to the best of your ability. 

Really I'm just trying to go methodically, we want everything in good order and no damage done. :)

Don't delete any partitions yet but answer the last questions above your last reply.

I made the recovery disk 2 disk total but i am afraid if the second would work and i have a one  Tb external hd i could backup my entire diskc  to it try to boot from that external hd if it what you are saying..

---

### Post by wilee-nilee on 2010-12-22
> **soltero5965 said:**
> I made the recovery disk 2 disk total but i am afraid if the second would work and i have a one  Tb external hd i could backup my entire diskc  to it try to boot from that external hd if it what you are saying..

Okay its your choice as far as backing up the C to the external, I would if there is room.

So you recognize that we have to remove a partition to install Ubuntu to a partition correct?

So this removable partition would have to be empty, backed up or expendable, do you see the conundrum here you will have to figure out how this works for you.

Maybe the D=sda4? **(confirm this please)** drive can have its contents transfered to the terrabyte external then removed leaving a big space for a extended partition that would have as many logical partitions as you want. These logicals are what the partitions are called inside a extended, and where the Linux install would go. 

You could also make a NTFS logical in the extended and get the D back if that is how it reads as of now. The NTFS in the logical would be a shared partition that Ubuntu and MS could read and write to.

Does this make sense.

If your computer was brand new and basically empty we could experiment seeing if we could just remove sda2 the booting partition and you could still trigger the recovery with the key prompt at boot up to see if it still worked. 

I'm not saying you should remove any partitions yet just laying out one method removing sda4 if emptied to the external for reloading a NTFS partition in a extended on the internal HD, along with the Ubuntu install in its own ext4 partition.

Really to be honest since this seems a bit beyond you, you might consider just doing a wubi install and practicing installs on another computer. No offense meant here but we are barely on the same page, if at all; I don't think so really. With the computer filled up, and having been used for awhile, I have no idea what is where exactly only you do as far as the operating system, are you up for this really?

Also you have at least 200 gigs on a 320 gog HD that is actually 298 gigs that is not to full but we generally advise on here that 70% is the most you want to fill for a workable system that is going to run efficiently and defragg properly.

---

### Post by baster8 on 2010-12-23
Hi, I almost have the exact same problem. I don't know if I should start a new thread or not, but I will try here first.

I have windows 7 64 bit installed. I used the universal-installer to put Ubuntu 10.10 (64bit version) on my USB. I have partitioned my hard drive into 4 partitions. First partition for windows 7 system reserve. Second partition C for the main part of windows 7. The third partition is logical and it is for random stuff. The fourth I intend to install Ubuntu on it. I tried to left this fourth partition unallocated, format it into ext3, format it into NTFS, but in any case, the Ubuntu installer can not detect that I already have another OS on my HD, and when I go into that "special partition option", Ubuntu installer only let me repartition anything. It can't see the existing partitions. Below is the result of the bootscript.

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   148,440,599   148,233,752   7 HPFS/NTFS
/dev/sda3         148,438,615   625,137,344   476,698,730   f W95 Ext d (LBA)
/dev/sda5         148,440,663   518,883,434   370,442,772   7 HPFS/NTFS
/dev/sda6         518,883,498   625,137,344   106,253,847   7 HPFS/NTFS

/dev/sda2 overlaps with /dev/sda3

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4047 MB, 4047502848 bytes
4 heads, 32 sectors/track, 61759 cylinders, total 7905279 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     7,905,278     7,905,247   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C6F4EFD9F4EFCA2F                       ntfs       System Reserved               
/dev/sda2        01CBA280DB2F12C0                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        01CBA2813BEED5A0                       ntfs       Data                          
/dev/sda6        01CBA290A0BBBE80                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8A76-EFC0                              vfat       PENDRIVE                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat        (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
    set gfxmode=auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  b8 e4 dd 55 55 55 55 55  55 55 55 55 55 55 55 55  |...UUUUUUUUUUUUU|
00000010  55 55 55 55 55 55 55 55  55 55 55 55 55 55 55 55  |UUUUUUUUUUUUUUUU|
*
00000030  55 55 55 55 55 55 55 55  55 55 55 55 55 55 00 02  |UUUUUUUUUUUUUU..|
00000040  00 1c c4 88 3d 8d 14 cc  80 fb a1 04 60 36 32 08  |....=.......`62.|
00000050  90 30 e0 34 1d 1b 0c 04  0c 8f 08 9e 4c 3e 2f cc  |.0.4........L>/.|
00000060  37 0e 4c 4c 10 8e 01 70  8d 3c 0b c1 44 79 89 c2  |7.LL...p.<..Dy..|
00000070  e1 b4 fc 41 cc 09 01 b2  4e 01 4f 0c 46 1c fb cd  |...A....N.O.F...|
00000080  cc 6d 10 8a c5 6c 9a f1  48 d0 fb 0f 69 c0 c1 04  |.m...l..H...i...|
00000090  ae 4f 75 1c 11 02 3d cd  5e 92 20 68 a6 a6 30 0e  |.Ou...=.^. h..0.|
000000a0  61 a0 04 04 26 7a 2c 69  66 a1 c4 06 24 36 6d 87  |a...&z,if...$6m.|
000000b0  81 02 8a fd ad 0a 18 16  07 0c b4 0c c5 08 cd 2b  |...............+|
000000c0  94 fb 57 cc 64 40 02 12  61 e1 23 cc d0 dd 22 db  |..W.d@..a.#...".|
000000d0  14 03 7b 5e cf a5 7b e2  9b 83 70 b5 51 3f 60 78  |..{^..{...p.Q?`x|
000000e0  1a fc ad 26 18 e6 d2 38  cc c8 cc 1c 0b 0b 4f e4  |...&...8......O.|
000000f0  46 08 99 83 69 21 a9 73  02 47 b5 87 8d a5 48 f1  |F...i!.s.G....H.|
00000100  24 71 6e 0c 81 99 30 93  e4 b8 5e 04 07 29 0b 4f  |$qn...0...^..).O|
00000110  93 d5 0f 3b ad 22 1b 42  08 e0 b0 0c 4e 2f 07 36  |...;.".B....N/.6|
00000120  b1 b0 b0 ca 83 3c 6f 21  00 5c e4 52 50 ac b2 f8  |.....<o!.\.RP...|
00000130  02 14 fb 2e 29 e9 54 06  f9 59 c7 3b 75 79 f4 dd  |....).T..Y.;uy..|
00000140  de 5b b5 6f 29 73 df 2e  c6 19 5c ad 8e e4 3e 9a  |.[.o)s....\...>.|
00000150  2d 7e 89 0d 0c 2c 01 5e  28 cc 3a b2 91 2e db 7f  |-~...,.^(.:.....|
00000160  3f 20 86 1b 35 b6 45 94  d5 78 62 92 82 d4 4e 8e  |? ..5.E..xb...N.|
00000170  d5 4a 98 67 13 ba fa cb  34 f3 48 a6 29 7d e5 45  |.J.g....4.H.)}.E|
00000180  ce eb d0 01 00 e6 95 c1  f6 18 5b 97 ed 61 d0 92  |..........[..a..|
00000190  94 51 f3 2c 5d 35 e5 2f  f1 8d 0c 1c f6 44 f8 05  |.Q.,]5./.....D..|
000001a0  d0 18 c1 05 ea b5 32 2c  50 21 a1 16 b0 24 c3 3a  |......2,P!...$.:|
000001b0  b1 53 29 a6 c7 c6 e2 e6  07 c2 00 78 16 8d 00 fe  |.S)........x....|
000001c0  ff ff 07 fe ff ff 00 08  00 00 14 82 14 16 00 fe  |................|
000001d0  ff ff 05 fe ff ff 14 8a  14 16 56 4e 55 06 00 00  |..........VNU...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 d0 03  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  df 9f 78 00 18 1e 00 00  00 00 00 00 02 00 00 00  |..x.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 c0 ef 76 8a 4e  4f 20 4e 41 4d 45 20 20  |..)..v.NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 08 40 00 00  66 ba 00 00 00 00 bb 00  |}.f..@..f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

So is this a special problem of 10.10 installer? Should I try 10.4? Also, as an aside, is it possible to not have Ubuntu install GRUB into the master boot record, and maybe just use window's boot manager instead?

Any help would be much appreciated.

---

### Post by soltero5965 on 2010-12-23
> **wilee-nilee said:**
> Okay its your choice as far as backing up the C to the external, I would if there is room.

So you recognize that we have to remove a partition to install Ubuntu to a partition correct?

So this removable partition would have to be empty, backed up or expendable, do you see the conundrum here you will have to figure out how this works for you.

Maybe the D=sda4? **(confirm this please)** drive can have its contents transfered to the terrabyte external then removed leaving a big space for a extended partition that would have as many logical partitions as you want. These logicals are what the partitions are called inside a extended, and where the Linux install would go. 

You could also make a NTFS logical in the extended and get the D back if that is how it reads as of now. The NTFS in the logical would be a shared partition that Ubuntu and MS could read and write to.

Does this make sense.

If your computer was brand new and basically empty we could experiment seeing if we could just remove sda2 the booting partition and you could still trigger the recovery with the key prompt at boot up to see if it still worked. 

I'm not saying you should remove any partitions yet just laying out one method removing sda4 if emptied to the external for reloading a NTFS partition in a extended on the internal HD, along with the Ubuntu install in its own ext4 partition.

Really to be honest since this seems a bit beyond you, you might consider just doing a wubi install and practicing installs on another computer. No offense meant here but we are barely on the same page, if at all; I don't think so really. With the computer filled up, and having been used for awhile, I have no idea what is where exactly only you do as far as the operating system, are you up for this really?

Also you have at least 200 gigs on a 320 gog HD that is actually 298 gigs that is not to full but we generally advise on here that 70% is the most you want to fill for a workable system that is going to run efficiently and defragg properly.

I have been thinking what my wife told me not to torture the small brain inside my small head she said  it is too much for me.She knows it because when we installed Ubuntu 9.10 dual boot with XP on her laptop everything went smooth, then we installed Ubuntu 10.04 alongside Vista on my laptop no issue at all it's only now that i am having nightmares with windows 7 alongside Ubuntu 10.10. Told her that with Windows 7 we can do without Ubuntu but i am now challenged and i like the learning curb and mostly the "torture" that brought me here.
Oh well i am done with  the back up tried to boot from that backup and everything is ready and in place  i need to move on, please walk me through  this I am ready..what do you want me to do..

---

### Post by sikander3786 on 2010-12-23
> > **soltero5965 said:**
> 
Oh well i am done with  the back up tried to boot from that backup and everything is ready and in place  i need to move on, please walk me through  this I am ready..what do you want me to do..


Thats nice. So you ready to delete sda4? Once again make sure that you've backed up all the data from sda4 then boot an Ubuntu Live CD and fire up Gparted. It should be under System > Administration > Gparted or might be under Applications > Accessories > Gparted.

Delete sda4 then create a new Extended partition inside that freed up space. Then for Ubuntu, you basically need 2 partitions. But, I would recommend using 3 partitions as a separted /home partition would preserve all your settings in case you decide to re-install. So, your partition setup,

1. Ubuntu '/' partition, filesystem ext4, size at least 10 GB. 20 GB would be enough for you any case.

2. /home partition, ext4, size at least 5 GB. Extend that to whatever you like in case you decide to store personal files on that partition.

3. Swap partition, size = RAM.

4. Optional Data partition for sharing data between Ubuntu and Windows. NTFS and custom sized.

So once you manage to create those partitions, fire up the installer and proceed to the partitioning page. Choose "_Manual Partitioning_" You'll need to define the mount points there. '/' for Ubuntu root partition, /home for /home and Swap. Let us know if you need any help then.

---

### Post by sikander3786 on 2010-12-23
> **baster8 said:**
> Hi, I almost have the exact same problem. I don't know if I should start a new thread or not, but I will try here first.

.....................................................
Welcome to the forums :-)

I would recommend to use manual partitioning as described in the above post. Feel free to post your queries but, start a new thread under Installation & Upgrades as dealing with 2 different people and setups will make it harder here in a single thread ;-)

---

### Post by Spyderkid on 2010-12-23
isntall it inside virtual box?

---

### Post by baster8 on 2010-12-23
To Sikander

Thanks for the welcome. I will start a new thread, but I think the main  problem is that neither Gparted nor the installer see the existing partitions, which  mostly likely also will be soltero's problem if I am correct. The partition saved for linux is already manually made in windows in any case.

---

### Post by sikander3786 on 2010-12-23
> **baster8 said:**
> To Sikander

Thanks for the welcome. I will start a new thread, but I think the main  problem is that neither Gparted nor the installer see the existing partitions, which  mostly likely also will be soltero's problem if I am correct. The partition saved for linux is already manually made in windows in any case.
boot scipt can see your partitions. I would still suggest to start a new thread and include a Gparted screenshot there. We would readily be there to help you. No problem :-)

We can work on all these issues there.

---

