---
title: "no init found, Try passing init=bootarg AND Live CD does not load"
date: 2011-02-13
forum: General Help
---

### Post by maurolust on 2011-02-13
Hello

First of all, my problem is pretty similar to what happened [here]("http://ubuntuforums.org/showthread.php?t=1594621"), but since my ubuntu 10.04 Live CD does not load ever (I left it running for hours and nothing), I decided to start a new thread, as suggested in the other thread. 

I did manage to load a Xubuntu live CD (from 2008 that I had lying around) that tells me I can't mount my two partitions (dev/sda1 is root and dev/sda2 is a logical partition with /home and swap.). The full message is: ```
mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error In some cases useful info is found in syslog - try dmesg |tail or so
```
When I try ```
dmesg|tail
``` I get
```
[125.073772] apm: disabled - APM is not SMP safe.
[219.958913] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240)
[228.628778] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240)
[281.502846] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240)
[281.617426] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240)
[281.737522] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240)
``` and so on.

I have tried 
```
fsck dev/sda1
fsck 1.40-WIP (14-Nov-2006)
```, which tells me nothing :(
I can only assume I have several damaged sections in my HDD, but no idea of a solution.

Obs: The 10.04 live cd does load on other PCs, but on this one it just shows a splash screen with the "loading" animation running on and on. I can't even check the disk for errors and get no error message. I did run a memory check, which is OK.

---

### Post by Rubi1200 on 2011-02-13
If you can boot the computer with the Xubuntu CD, please do the following:

Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by maurolust on 2011-02-13
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367  83 Linux
/dev/sda2          83,891,491   488,396,799   404,505,309   5 Extended
/dev/sda5          83,891,493   484,282,117   400,390,625  83 Linux
/dev/sda6         484,284,416   488,396,799     4,112,384  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5df18933-02f2-4629-b5d0-2f09bb4cdaee   ext3                                     
/dev/sda5        c4146ee5-87b1-4c00-a971-ee39d1ef195f   ext3                                     
/dev/sda6        bbe217f2-1163-4f8f-bd50-fc99345a2b7e   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2



=============================== StdErr Messages: ===============================

hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory

```
Thank you Rubi

---

### Post by Rubi1200 on 2011-02-13
There appear to be problems with both sda1 and sda5.

What is this referring to?
> couldn't mount because of unsupported optional features
I am not even sure where you should start, with the root file system or /home.

Have you tried Testdisk?

---

### Post by maurolust on 2011-02-13
> **Rubi1200 said:**
> There appear to be problems with both sda1 and sda5.

What is this referring to?

I am not even sure where you should start, with the root file system or /home.

Have you tried Testdisk?

I am learning about Testdisk for the first time now. I'll see what Parted Magic Live CD can do for me.

Here is the whole output when I tried dmesg |tail. It doesn't make much sense to me. 
```
ubuntu@ubuntu:~$ dmesg |tail 
[  281.737522] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  281.870583] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).
[  674.057034] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[  735.998943] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).
[ 1663.005157] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[ 3656.696942] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).
[ 3656.835343] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[ 3656.947771] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).
[ 4178.277420] EXT3-fs: sda1: couldn't mount because of unsupported optional features (240).
[ 4178.363233] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).

``` is what I got after running dmesg |tail.
I wonder, if both partitions are unmounted, then where is my desktop being saved?

/root , in my opinion, should have priority. /home only has documents, no applications.

---

### Post by maurolust on 2011-02-13
Well,

I tried testdisk, followed the instructions in [the step by step guide]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"), but forgot to backup the log file before restarting the computer (I shall remember not to turn my brain off when following step-by-step guides). 

Essentially what I did was mark the damaged partitions with D, the /root partition with * and the /home with L. I could not keep the structure unless I marked the swap with D as well, so the swap had to go.

Then I restarted and had the same old problem.

boot info now gives me this:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes


Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    83,891,429    83,891,367  83 Linux
/dev/sda2          83,891,430   488,408,129   404,516,700   f W95 Ext d (LBA)
/dev/sda5          83,891,493   484,295,489   400,403,997  83 Linux

/dev/sda2 ends after the last sector of /dev/sda

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        5df18933-02f2-4629-b5d0-2f09bb4cdaee   ext3                                     
/dev/sda5        c4146ee5-87b1-4c00-a971-ee39d1ef195f   ext3                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/bus/usb     /proc/bus/usb            none       (rw,bind)


```

The 'W95 Ext d (LBA)' in dev/sda2 looks odd. What should a Linux extended partition be labeled?

What recovery Live CD is most recommendable in this case, downloading testdisk to the desktop of a xubunTOS live CD is probably not the best way to do this.

---

### Post by maurolust on 2011-02-15
So, when testdisk doesn't work, what should I do? Try again and again, disk duplicate and format?
Is it best to use Parted Magic with the CD on or running on RAM?

---

### Post by maurolust on 2011-02-16
So, here is what I did:
[LIST=1]
[*]Used testdisk to fix all failed partitions
[*]Used fsck.ext4 (without the -p option) to recover the sda1 superblocks. This took a while and I had to hold the "y" key for a few seconds, which doesn't seem to be very sensible.
[*]tried to boot ubuntu, but got a message saying it couldn't mount the /home partition (/sda2).
[*]used fsck.ext4 on sda2 as well
[*]got back to square 1, now I get the same "no init found..." message I had in the beginning.
[/LIST]
I'm afraid the most logical thing to do now is try to backup all my files from /sda2, format the whole drive and reinstall ubuntu. Should I use photorec for this, or just copying will do?

Is there anyway I can check the "health" of my HDD after I format it. Am I to expect this to happen again and again if I don't get a new HDD?

---

### Post by Rubi1200 on 2011-02-16
> Should I use photorec for this, or just copying will do?
Whichever works best I suppose.

You can try and recover data with Photorec, but be aware that file names etc, can get messed up (from what I have read).

I think you may have little choice but to reinstall. Testdisk is usually a good choice for repairing damage, but whatever happened is apparently too much for the system.

Can you check the HDD status from the LiveCD?

Use the Disk Utility; it should give you an idea about the health of your drive e.g. bad sectors etc.

---

