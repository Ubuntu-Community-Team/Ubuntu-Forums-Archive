---
title: "I mucked up GRUB lol..."
date: 2010-09-17
forum: General Help
---

### Post by Cruuncher on 2010-09-17
Okay, i have windows and ubuntu 9.04 installed on my acer laptop.
 
Today i decided i wanted to reinstall windows (been over a year since the last time, and i like to start fresh every 6 months or so).
 
anyway, when i loaded windows recovery thing, it gave me a strange error about not being able to determine a drive letter for some partitions (the one's used for linux)
 
so me being the idiot that i am, went into disk manager in windows and deleted the 2 linux partitions (assumed i could get linux back afterwards anyway), and now i restart. 
 
I now found out that GRUB depended on information from those partitions to work.
 
so now i'm all scared and i run and find the actual windows recovery disk i made just in case something out of the ordinary happens(like this). I pop it in, only to learn that GRUB doesn't recognize it as an operating system (yes i changed my boot order to look in the dvd drive first) so now i have a computer that won't boot that gives me an error when loading grub, Error 22 i think it was.
 
SOO. is there any disk out there that grub can boot as maybe a temporary GRUB? lol, or anything that can help me would be SUPER,
 
Thanks, Cruuncher

---

### Post by garvinrick4 on 2010-09-17
> **Cruuncher said:**
> Okay, i have windows and ubuntu 9.04 installed on my acer laptop.
 
Today i decided i wanted to reinstall windows (been over a year since the last time, and i like to start fresh every 6 months or so).
 
anyway, when i loaded windows recovery thing, it gave me a strange error about not being able to determine a drive letter for some partitions (the one's used for linux)
 
so me being the idiot that i am, went into disk manager in windows and deleted the 2 linux partitions (assumed i could get linux back afterwards anyway), and now i restart. 
 
I now found out that GRUB depended on information from those partitions to work.
 
so now i'm all scared and i run and find the actual windows recovery disk i made just in case something out of the ordinary happens(like this). I pop it in, only to learn that GRUB doesn't recognize it as an operating system (yes i changed my boot order to look in the dvd drive first) so now i have a computer that won't boot that gives me an error when loading grub, Error 22 i think it was.
 
SOO. is there any disk out there that grub can boot as maybe a temporary GRUB? lol, or anything that can help me would be SUPER,
 
Thanks, CruuncherRun this in a Ubuntu live cd disk.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
ignrore any errors we just want the mbr.
If Windows does not boot with this installed in your mbr then
you have a bad Windows install most likely.

---

### Post by garvinrick4 on 2010-09-17
If that does not work their is another way to look at your installs.
go to this url and download to DESKTOP make sure to desktop 
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
then run this line of code and a text file will be on your desktop copy and paste it here.
 ```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by Cruuncher on 2010-09-17
Thanks garvin.
 
I have school right now and don't get back till late and i'll try this then,
 
but just so it doesn't take up too much of my time when it matters, what's the fastest way to make an ubuntu live cd? (links?, don't have much time to search SORRY)

---

### Post by garvinrick4 on 2010-09-17
Download the .osi file here and BURN at slowest possible speed to a disk.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by Cruuncher on 2010-09-17
Ok, live boot disk worked, i'm currently on the computer in question lol.

I ran the first set of commands you gave me and i get this:

ubuntu@ubuntu:~$ sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mbr
Suggested packages:
  lilo-doc
The following NEW packages will be installed:
  lilo mbr
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 413kB of archives.
After this operation, 1,315kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main mbr 1.1.10-2
  Could not resolve 'archive.ubuntu.com'
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main lilo 1:22.8-8ubuntu1
  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mbr/mbr_1.1.10-2_i386.deb)  Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/lilo/lilo_22.8-8ubuntu1_i386.deb)  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ sudo lilo -M /dev/sda mbr
sudo: lilo: command not found

---

### Post by Cruuncher on 2010-09-17
and results from the second suggestion you had:

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #4 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   488,394,743   467,912,696   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        62CA75D6CA75A747                       ntfs       ACER                          
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /media/ACER              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by wilee-nilee on 2010-09-17
If you ran the script after the lilo attempt it didn't install. Good advice though lilo works. If you want the MS bootloader though in the MBR here is a link to a recovery disc and instructions with a link to the W7 forums to show how to get to the command line in upon booting the recovery cd. Only run the highlighted command at this point.

Actually it looks like you have Vista here is the link for its recovery ISO.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
**BootRec.exe /fixmbr** (#updates MBR master boot record...do not run if you still want grub)
chkdsk /r
BootRec.exe /FixBoot (#updates PBR partition boot)
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by Slim Odds on 2010-09-17
> **garvinrick4 said:**
> Download the .osi file here and BURN at slowest possible speed to a disk.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

That is OLD and BAD advice.

Drive today are designed to burn at higher speeds and actually product POORER results when you burn at "the lowest possible speed". Not to mention the fact that you'll waste tons of time.

Almost all CD burning programs allow you to check the disk after it's burned. Use that feature.

---

### Post by Cruuncher on 2010-09-17
okay, in the mean time i got the windows recovery disk to start working, but after "Windows is loading files..." it just shuts down

---

### Post by Cruuncher on 2010-09-17
k willie i'll download that, gimme a few

---

### Post by wilee-nilee on 2010-09-17
> **Cruuncher said:**
> okay, in the mean time i got the windows recovery disk to start working, but after "Windows is loading files..." it just shuts down

I think maybe a thread at the W7 forums might be helpful here, as they are windows users and might have other ideas as well.
[http://www.sevenforums.com/](http://www.sevenforums.com/)

What you describe now leaves things in the air.

**The only thing I could do is have you run the boot script again and see what is on the HD.**

I see while I was typing this you posted, that you are downloading the recovery, from neosmart.

What is the recovery disc that you were trying to use? 

Lets be careful here before trying any more fixes as the attempted a recovery could have overwritten the W7 setup.

**Run the bootscript again with the live Ubuntu cd, so we can see if any damage was done.**

---

### Post by Cruuncher on 2010-09-17
i got it working, my computer is back to the way it was before this shinanigans but without grub or linux, which is fine. Reinstalling windows properly now.
 
Thanks a bunch everyone who tried to/did help me :)

---

### Post by wilee-nilee on 2010-09-17
> **Cruuncher said:**
> i got it working, my computer is back to the way it was before this shinanigans but without grub or linux, which is fine. Reinstalling windows properly now.
 
Thanks a bunch everyone who tried to/did help me :)

Yay I say I suspected that no damage was done with your recovery, I am just as cautious as I can be.

---

### Post by Cruuncher on 2010-09-18
Is there no rep system in this forum?

---

