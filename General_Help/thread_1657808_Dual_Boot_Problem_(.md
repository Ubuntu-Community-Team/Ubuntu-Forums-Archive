---
title: "Dual Boot Problem :("
date: 2011-01-01
forum: General Help
---

### Post by AlekFx on 2011-01-01
Here is what happened :popcorn:
I installed ubuntu to a free space which i shrunk in vista, in the installation i chose "update from files" or something along those lines, anyways, after installing i start using it and it works fine, when i reboot my computer i get a bootscreen i i chose vista (because i wanted to boot into vista) and somthing happened, anyways when i reboot i get "grub rescue" and cant boot from a recovery disk that i downloaded of a torrent, im so mad because when i reboot but insert the linux CD it stars succesfully but it asks me if i want to "install" or try" even though i already installed tqice to try to fix the problem please help:( and thanks :)
i think its my bootmanager or grub is not getting installed :?
*can i fix my boot thingy from linux so i can boot to vista then delete the linux partition then fix the bmr to only one OS not dual boot.:?

edit
_
i can only boot to Ubuntu but only to try  or install, i tried to change stuff in the bios right now but i dont know how to ?
2] when i go to the bootmanager [ubuntu] and slect to boot from 1st harddisk it says [error no such.......]

---

### Post by AlekFx on 2011-01-01
:bump:
summary 
i installed ubuntu, when i rebooted and remove the disk i get an error [something about] GRUB, when i put the disc and reboot it asks if i want to install or try, when i get this screen i choose [boot from first hard disk] it says it doesn't exist:mad: also, in the first installation installed bootloader in the windows partition :O is that the problem? i reinstalled however and same result :(



i appreciate all your help thanks your saving another user :)

---

### Post by Bucky Ball on 2011-01-01
Try installing 10.04 LTS, the current long term support release with support until April 2013. Support for 9.04 finishes April, 2011. Not sure why you're attempting to install this older release. ;)

Torrent version available here:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

Make sure you are downloading the correct version: i386 for ALL 32bit machines, AMD64 for ALL 64bit.

---

### Post by AlekFx on 2011-01-01
> **Bucky Ball said:**
> Try installing 10.04 LTS, the current long term support release with support until April 2013. Support for 9.04 finishes April, 2011. Not sure why you're attempting to install this older release. ;)

Torrent version available here:

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#bt)

Make sure you are downloading the correct version: i386 for ALL 32bit machines, AMD64 for ALL 64bit.
an how does this help ?xD

---

### Post by drs305 on 2011-01-01
AlekFx,

Welcome to the Ubuntu forums!

Can you boot the LiveCD to a working Desktop? I couldn't be sure.

If so, go to the following site and download and run the boot info script. Post the contents of the RESULTS.txt here and we can see the status of your boot files.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by Ceiber Boy on 2011-01-01
> **AlekFx said:**
> Here is what happened :popcorn:
I installed ubuntu to a free space which i shrunk in vista, in the installation i chose "update from files" or something along those lines, anyways, after installing i start using it and it works fine, when i reboot my computer i get a bootscreen i i chose vista (because i wanted to boot into vista) and somthing happened, anyways when i reboot i get "grub rescue" and cant boot from a recovery disk that i downloaded of a torrent, im so mad because when i reboot but insert the linux CD it stars succesfully but it asks me if i want to "install" or try" even though i already installed tqice to try to fix the problem please help:( and thanks :)
i think its my bootmanager or grub is not getting installed :?
*can i fix my boot thingy from linux so i can boot to vista then delete the linux partition then fix the bmr to only one OS not dual boot.:?
 
edit
_
i can only boot to Ubuntu but only to try or install, i tried to change stuff in the bios right now but i dont know how to ?
2] when i go to the bootmanager [ubuntu] and slect to boot from 1st harddisk it says [error no such.......]
 
the only thing i thing could of caused thing to have gone wrong for you was to use windows to to resize the partition, the ubuntu installation disk contains a utility to do this for you.
 
Can i just ask for clarfication:
is it XP or Vista that was already on the HDD, as the image of the boot screen had XP on it but your text talks about Vista?
 
is it ubuntu or windows that will not boot?
 
have you done any re-installation thus far?

---

### Post by wilee-nilee on 2011-01-01
What Ubuntu is that, which distro?

Post 5 is really the answer here really.

---

### Post by Bucky Ball on 2011-01-01
> **AlekFx said:**
> an how does this help ?xD

The Ubuntu kernel improves continually to cover more hardware and machines. You might find it installs issue free. And as I say, you have four months of support with 9.04 then you are on your own. No security updates, no package updates. Zip. ;)

ps: Willee - check the screenshot. 9.04 ... Have you just got up again? ;)

---

### Post by AlekFx on 2011-01-01
> **Ceiber Boy said:**
> the only thing i thing could of caused thing to have gone wrong for you was to use windows to to resize the partition, the ubuntu installation disk contains a utility to do this for you.
 
Can i just ask for clarfication:
is it XP or Vista that was already on the HDD, as the image of the boot screen had XP on it but your text talks about Vista?
 
is it ubuntu or windows that will not boot?
 
have you done any re-installation thus far?
i got the image from the internet :P and i was on vista and partitioned from vista to a free space so i guess is technically not "partitioning" becuase i formated and made it a drive in the installation from Ubuntu

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> What Ubuntu is that, which distro?

ubuntu 10.10 32bit for desktop

---

### Post by AlekFx on 2011-01-01
> **drs305 said:**
> AlekFx,

Welcome to the Ubuntu forums!

Can you boot the LiveCD to a working Desktop? I couldn't be sure.

If so, go to the following site and download and run the boot info script. Post the contents of the RESULTS.txt here and we can see the status of your boot files.
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

the only desktop i can get is from ubuntu "try" 
im reinstalling right now choosing to format the drive i allocated in the first place with the installation wizard,{should i do it with th other one?} and installing boot-manager or boot-loader or whatever in that same spot {the partition} ill see if that fixes things

---

### Post by AlekFx on 2011-01-01
> **drs305 said:**
> AlekFx,

Welcome to the Ubuntu forums!

Can you boot the LiveCD to a working Desktop? I couldn't be sure.

If so, go to the following site and download and run the boot info script. Post the contents of the RESULTS.txt here and we can see the status of your boot files.
[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)
im doing it right now thanks :]

edit

---

### Post by Ceiber Boy on 2011-01-01
> **AlekFx said:**
> i got the image from the internet :P and i was on vista and partitioned from vista to a free space so i guess is technically not "partitioning" becuase i formated and made it a drive in the installation from Ubuntu
 
ok ... so you partitioned (made free space) in vista, then inserted the ubuntu disk, the disk recognised the free space made by vista? and then installed into that space.
 
so ubuntu will boot but not vista!?
 
(sorry these are short posts but want to get facts right)

---

### Post by AlekFx on 2011-01-01
> **Ceiber Boy said:**
> ok ... so you partitioned (made free space) in vista, then inserted the ubuntu disk, the disk recognised the free space made by vista? and then installed into that space.
 
so ubuntu will boot but not vista!?
 
(sorry these are short posts but want to get facts right)
No problem i love your support type, i should be sorry :) ,,other forums are mean :P,
and yes your exaclty right ubuntu boots BUT not into "ubuntu" but into "Ubuntu Install or tRY"

---

### Post by wilee-nilee on 2011-01-01
> **Bucky Ball said:**
> The Ubuntu kernel improves continually to cover more hardware and machines. You might find it installs issue free. And as I say, you have four months of support with 9.04 then you are on your own. No security updates, no package updates. Zip. ;)

ps: Willee - check the screenshot. 9.04 ... Have you just got up again? ;)

lol been so long since I have seen a grub-legacy menu missed it.;)

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> lol been so long since I have seen a grub-legacy menu missed it.;)
very helpful post :P 
hers the results

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for (,msdos4)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 533531472 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,973,567    20,971,520  27 Hidden HPFS/NTFS
/dev/sda2    *     20,973,568   491,317,071   470,343,504   7 HPFS/NTFS
/dev/sda3         491,317,248   614,195,199   122,877,952  83 Linux
/dev/sda4         614,197,141   625,137,344    10,940,204   f W95 Ext d (LBA)
/dev/sda5         614,197,143   625,137,344    10,940,202   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        A20AB2D80AB2A925                       ntfs       PQSERVICE                     
/dev/sda2        FAC8A4E2C8A49E7F                       ntfs       OS                            
/dev/sda3        0f4d4a5e-903a-406c-ae66-65df55f3efd7   ext2                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        01CB9EE98C659FF0                       ntfs       Backup                        
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde

```

---

### Post by Bucky Ball on 2011-01-01
> **AlekFx said:**
> ubuntu 10.10 32bit for desktop

'Fraid not. Your screenshot clearly shows 9.04. Not sure why others haven't noticed this. Trying to help is going to be difficult if people are giving advice for 10.10. It and 9.04 are different beasts in many respects.

---

### Post by AlekFx on 2011-01-01
> **Bucky Ball said:**
> 'Fraid not. Your screenshot clearly shows 9.04. Not sure why others haven't noticed this. Trying to help is going to be difficult if people are giving advice for 10.10. It and 9.04 are different beasts in many respects.
Screenshot taken from the internet as an example

---

### Post by Ceiber Boy on 2011-01-01
> **Bucky Ball said:**
> 'Fraid not. Your screenshot clearly shows 9.04. Not sure why others haven't noticed this. Trying to help is going to be difficult if people are giving advice for 10.10. It and 9.04 are different beasts in many respects.
 
 
It might be a good idea (keeping in mind the above quote) to go to the ubuntu website, download 10.04 LTS (to be ultra safe) burn the .iso to disk, boot from that disk, delete the partition where you have installed ubuntu, so that only remaining partition is where vista is located and then install ubuntu where the previous ubuntu was installed.

---

### Post by AlekFx on 2011-01-01
How about the boot thingy?

im downloading 



[ubuntu-10.04.1-desktop-i386.iso.torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-desktop-i386.iso.torrent") 


is it ok ? 
thanks
an im burning it in ubuntu ok

---

### Post by Ceiber Boy on 2011-01-01
> **AlekFx said:**
> How about the boot thingy?
 
im downloading 
 
 
 
[ubuntu-10.04.1-desktop-i386.iso.torrent]("http://releases.ubuntu.com/lucid/ubuntu-10.04.1-desktop-i386.iso.torrent") 
 
 
is it ok ? 
thanks
an im burning it in ubuntu ok
 
 
this is for a 32-bit machine, if you have a 32-bit machine thats fine:P

---

### Post by Ceiber Boy on 2011-01-01
> **AlekFx said:**
> How about the boot thingy?
 
an im burning it in ubuntu ok
 if thats your only option!

---

### Post by Bucky Ball on 2011-01-01
As above. If you have a dual-core processor it is 64bit and you should be using the Desktop 10.04 LTS AMD64 version.

---

### Post by wilee-nilee on 2011-01-01
sda3: _________________________________________________________________________

    File system:      ** ext2**
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 533531472 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

So you got Ubuntu into one partition but it didn't install, but loaded the grub bootloader. It is also a ext2 should be ext4, you must have used gparted to make that partition it defaults to grub2 you need to click on the drop down and choose ext4

If you want to quickly get back Vista for now, here is a recovery disc link if you don't have one. Here is the instructions to getting to the command line with a W7 forum visual map of the instructions just run the one command and you will be back in Vista.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> sda3: _________________________________________________________________________

    File system:      ** ext2**
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 533531472 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.

So you got Ubuntu into one partition but it didn't install, but loaded the grub bootloader. It is also a ext2 should be ext4, you must have used gparted to make that partition it defaults to grub2 you need to click on the drop down and choose ext4

If you want to quickly get back Vista for now, here is a recovery disc link if you don't have one. Here is the instructions to getting to the command line with a W7 forum visual map of the instructions just run the one command and you will be back in Vista.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr**

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
bedore....it installed succesfully in the partition made from gparted you are right, i made a recovery disk but it only makes it freeze it says "booting from disc" and stays there if i remove it it says No such disk or somehting like that

MAJOR EDIT: 
when i chose the option install along side  OS i used to see somehintg about windows now i see "Files" :(
edit_
Im reinstalling right now
Step by step isntallation on how its going;

1)i chose English and hit Forward
2)i dont check anybox for the updates, i hit forward
3)in [Allocate DRive Space] i chose Specify Partitions manually (advanced), then click forward
4)i double click SDa3 10gb) i use as EXT4 and format
5)I click forward and get "No file system is defined" ,for mount point i chose " / "{In the first installation i chose /}
6) i want to click Install :P

---

### Post by wilee-nilee on 2011-01-01
> **AlekFx said:**
> bedore....it installed succesfully in the partition made from gparted you are right, i made a recovery disk but it only makes it freeze it says "booting from disc" and stays there if i remove it it says No such disk or somehting like that

So do you want to just delete the Ubuntu not installed and just put in another, or if you want the Vista back in the mean time there is a linux bootloader that will work to boot vista.

The only thing I'm also wondering about is this 
/dev/sda4         614,197,141   625,137,344    10,940,204   f W95 Ext d (LBA)
/dev/sda5         614,197,143   625,137,344    10,940,202   7 HPFS/NTFS

sda4 is a windows extended I think dynamic, not sure if this messed up the install, or is involved somehow, others will know the answer to this.

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> So do you want to just delete the Ubuntu not installed and just put in another, or if you want the Vista back in the mean time there is a linux bootloader that will work to boot vista.

The only thing I'm also wondering about is this 
/dev/sda4         614,197,141   625,137,344    10,940,204   f W95 Ext d (LBA)
/dev/sda5         614,197,143   625,137,344    10,940,202   7 HPFS/NTFS

sda4 is a windows extended I think dynamic, not sure if this messed up the install, or is involved somehow, others will know the answer to this.

 I want vista back :`( 

and my machine is Emachines and it came with some recovery drive thingy which mught be sda4
orsda5 it also has a card reader so....


edit_
SHould i reinstalling right now
or
**wait for a bootloader fix i haven't found any.**:(

Step by step isntallation on how its going;

1)i chose English and hit Forward
2)i dont check anybox for the updates, i hit forward
3)in [Allocate DRive Space] i chose Specify Partitions manually (advanced), then click forward
4)i double click SDa3 10gb) i use as EXT4 and format
5)I click forward and get "No file system is defined" ,for mount point i chose " / "{In the first installation i chose /}
6) i want to click Install :razz:

---

### Post by wilee-nilee on 2011-01-01
Boot a live Ubuntu cd and run these two commands to get lilo in the mbr and vista should boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Here is a picture of where universe is located software source in menu-system-admin.
[ATTACH]179902[/ATTACH]

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> Boot a live Ubuntu cd and run these two commands to get lilo in the mbr and vista should boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR


Thanks :))

here are the results

ubuntu@ubuntu:~$ Restore basic windows boot loader - universe enabled
No command 'Restore' found, did you mean:
 Command 'restore' from package 'dump' (universe)
Restore: command not found
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up man-db (2.5.7-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up mbr (1.1.10-2) ...
Setting up lilo (1:22.8-8ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing lilo (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 lilo
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
Backup copy of /dev/sda in /boot/boot.0800
The Master Boot Record of  /dev/sda  has been updated.
ubuntu@ubuntu:~$

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> Boot a live Ubuntu cd and run these two commands to get lilo in the mbr and vista should boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

Here is a picture of where universe is located software source in menu-system-admin.
[ATTACH]179902[/ATTACH]
[N00b question]

Where can i find that window?

[/N00b question]

---

### Post by wilee-nilee on 2011-01-01
You ran the instructions first, did you actually enable the universe repository it sort of looks like it worked hard to tell look closer at that post I was putting a screen shot together for you now there.

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> You ran the instructions first, did you actually enable the universe repository it sort of looks like it worked hard to tell look closer at that post I was putting a screen shot together for you now there.
yes sorry :(
i cant enable universe because i cant find that Software resources shortcut

---

### Post by wilee-nilee on 2011-01-01
> **AlekFx said:**
> [N00b question]

Where can i find that window?

[/N00b question]

Okay you need to slow down and read what is being given you, take a breath we are just about there. As posted already software sources is here.:)
menu-system-admin-software sources

You may have to right click the menu then edit to tick this software sources program on, and have it show in the menu dropdown.

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> Okay you need to slow down and read what is being given you, take a breath we are just about there. As posted already software sources is here.:)
menu-system-admin-software sources

You may have to right click the menu then edit to tick this software sources program on, and have it show in the menu dropdown.
ok thanks
*takes deep breath*

---

### Post by AlekFx on 2011-01-01
I get


The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.


should i reload?
i am :P

---

### Post by wilee-nilee on 2011-01-01
> **AlekFx said:**
> I get


The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.


should i reload?
i am :P

from post 28.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
**May show error messages about the rest of lilo missing, ignore, we just want MBR**

Is the error on closing the software sources just close it and let it do its thing then run the two commands.

I think you may have it already anyway it was hard to tell from the original command line readout the first try.

---

### Post by AlekFx on 2011-01-01
ubuntu@ubuntu:~$ Restore basic windows boot loader - universe enabled
No command 'Restore' found, did you mean:
 Command 'restore' from package 'dump' (universe)
Restore: command not found
ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lilo is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 213 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up man-db (2.5.7-4) ...
Updating database of manual pages ...
Setting up lilo (1:22.8-8ubuntu1) ...

WARNING: kernel & initrd not found in the root directory (/vmlinuz & /initrd.img)
WARNING: Do NOT reboot or LILO may fail to boot if your kernel+initrd is large.
WARNING: Please read /usr/share/doc/lilo/README.Debian

ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
/boot/boot.0800 exists - no /dev/sda backup copy made.
The Master Boot Record of  /dev/sda  has been updated.
ubuntu@ubuntu:~$


Edit Im rebooting Now.

---

### Post by AlekFx on 2011-01-01
> **wilee-nilee said:**
> from post 28.
Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
**May show error messages about the rest of lilo missing, ignore, we just want MBR**

Is the error on closing the software sources just close it and let it do its thing then run the two commands.

I think you may have it already anyway it was hard to tell from the original command line readout the first try.
thank you sooooooooooooo much man you :lolflag:):P
thanks  solved!

---

### Post by wilee-nilee on 2011-01-01
> **AlekFx said:**
> thank you sooooooooooooo much man you :lolflag:):P
thanks  solved!

Nothing like bricking the computer then fixing it to get you going now.:)

---

### Post by Bucky Ball on 2011-01-02
Legend wilee. Have fun with the OS AlekFx. ;)

---

