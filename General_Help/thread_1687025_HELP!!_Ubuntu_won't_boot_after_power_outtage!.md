---
title: "HELP!! Ubuntu won't boot after power outtage!"
date: 2011-02-13
forum: General Help
---

### Post by lordjj on 2011-02-13
A few days ago, when I booted my Ubuntu 10.04 system, it froze. Instead of forcing a power-off I left it until Laptop Battery depleted hoping it'd safely shutdown -as I have it set to shutdown when battery is low. After a while I plugged it in and tried to boot, but I got a black screen with:

                  GNU GRUB version 1.98-1ubuntu6
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

<grub> _


 What can I do to repair my system??
I tried booting from live Ubuntu 10.04 CD opening terminal and entering:

sudo fdisk -l

which showed me a star next to /dev/sda1

then:
sudo fsck -f -c -p /dev/sda1

but all I got was:
fsck from util-linux-ng 2.17.2
fsck: fsck.ntfs: not found
fsck: Error 2 while executing fsck.nts for /dev/sda1

Please HELP!!!:(

---

### Post by Rubi1200 on 2011-02-13
Hi and welcome to the forums :)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by ajgreeny on 2011-02-13
Is this a dual boot system?  It looks as if the partition sda1 is ntfs.

Can you run ```
sudo fdisk -l
``` from live CD and report the output back here again.  If it shows what I expect, it will probably be worth trying ```
sudo e2fsck /dev/sda#
```for whatever is your Ubuntu root partition.  I would not worry about any options to run the e2fsck at this stage, just see what happens by default.

Also click on **boot-info-script** in signature and carry out all it says; it may help us further.

---

### Post by lordjj on 2011-02-13
Hey guys, thank you for the replies. It is dual boot -it's a Wubi installation through Windows XP.
 I did both things you said:
-This is the content of RESULTS.txt:
 
```
 
                Boot Info Script 0.55    dated February 15th, 2010                    
============================= Boot Info Summary: ==============================
 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/swap.disk
sda2: _________________________________________________________________________
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
sdb1: _________________________________________________________________________
    File system:       vfat
    Boot sector type:  Windows XP: Fat32
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
/dev/sda1    *             63   307,194,929   307,194,867   7 HPFS/NTFS
/dev/sda2         307,194,930   625,121,279   317,926,350   f W95 Ext d (LBA)
/dev/sda5         307,194,993   625,121,279   317,926,287   7 HPFS/NTFS

Drive: sdb ___________________ _____________________________________________________
Disk /dev/sdb: 261 MB, 261750784 bytes
16 heads, 32 sectors/track, 998 cylinders, total 511232 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot         Start           End          Size  Id System
/dev/sdb1    *             32       510,974       510,943   b W95 FAT32

blkid -c /dev/null: ____________________________________________________________
Device           UUID                                   TYPE       LABEL                         
/dev/loop0                                              squashfs                                 
/dev/sda1        B6C4B300C4B2C243                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        E04C983D4C981080                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4CA4-E352                              vfat                                     
/dev/sdb: PTTYPE="dos" 
============================ "mount | grep ^/dev  output: ===========================
Device           Mount_Point              Type       Options
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/4CA4-E352         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)

================================ sda1/boot.ini: ================================
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"


```
 
-and this's the output of
```
 
sudo fdisk -l

```
 
```
 
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x09fb7a2d
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19122   153597433+   7  HPFS/NTFS
/dev/sda2           19123       38912   158963175    f  W95 Ext'd (LBA)
/dev/sda5           19123       38912   158963143+   7  HPFS/NTFS
Disk /dev/sdb: 261 MB, 261750784 bytes
16 heads, 32 sectors/track, 998 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         998      255471+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(996, 15, 32) logical=(997, 15, 31)

```

---

### Post by Rubi1200 on 2011-02-13
It is not possible to repair a Wubi install in the same way as a regular install to the hard-drive.

Therefore, running fsck as you did failed.

You seem to be missing the C:\ubuntu\disks\root.disk and C:\ubuntu\disks\boot files and this is probably the source of the problem.

Had you recently run a chkdsk in Windows?

Try looking for a hidden folder named C:\found.000 (you need to enable the hidden files and folders feature in Windows).

If the files are there just copy them back to the Ubuntu folder on C.

---

### Post by lordjj on 2011-02-13
By booting Windows XP, I can see that:
C:\ubuntu\disks\root.disk exists and is of file size 7.56 GB (8,120,172,544 bytes)
but C:\ubuntu\disks\boot which only contains the folder "grub" is of size 0 bytes
 
No, I had not run a chkdsk in Windows.
And C:\found.000 doesn't seem to exist (even after enabling "show hidden files and folders" and deselecting "hide protected operating system files")

---

### Post by Rubi1200 on 2011-02-13
Where did you find the 2 files?

I still think all you need to do is copy them back to the Ubuntu folder in C and then reboot to see if you are back in Ubuntu again.

You may also need to refer to the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem #2, solution #1 should help.

Then apply the Permanent Fix to prevent this happening again.

---

### Post by lordjj on 2011-02-13
I found them in C:\ubuntu
(C:\ubuntu\disks\root.disk  <--file
and C:\ubuntu\disks\boot\ <--folder )
 
I'll try to boot the Live CD and perform Proble#2, Solution#1.
But is it possible to locate these any of these files on the CD & copy them from their?

---

### Post by Rubi1200 on 2011-02-13
Not as far as I know. 

I will ask someone else to take a look and offer some perspectives on this.

---

### Post by lordjj on 2011-02-13
Hey. I tried Problem#2, Sloution#1 from the Wubi Megathread but here's what I got:
 
```
 
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
/media/win/ubuntu/disks/root.disk: Input/output error
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
cp: cannot stat `/mnt/boot/grub/grub.cfg': No such file or directory
sudo chmod +w /mnt/boot/grub/grub.cfg
chmod: cannot access `/mnt/boot/grub/grub.cfg': No such file or directory
gksu gedit /mnt/boot/grub/grub.cfg

```
 
And then grub.cfg displayed in gedit but it was completely empty.

---

### Post by bcbc on 2011-02-13
> /media/win/ubuntu/disks/root.disk: Input/output error

Try this:
```
sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

If that fixes it, then try booting Wubi again. I don't think the other fix is required unless you also have updated grub since installing 10.04.

PS: in general, when following a series of instructions, if you get an error/exception message on any line you should stop and figure out the problem or ask for help before continuing.

PPS: if you're still booted from the live CD you will probably get an error that /media/win already exists on the first command. You might still have /dev/sda1 mounted as well. Check first by running command:
```
mount | grep 'sda1'
```
If you see nothing do all the commands, if you see /media/win, then just run the third command. Otherwise run all three

---

### Post by lordjj on 2011-02-14
Hello. Thank you for the reply. I did the following:

```
ubuntu@ubuntu:~$ mount | grep 'sda1'
ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/win
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /media/win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

But I think this is due to the fact that the Hard Disk wasn't mounted -as it is not mounted by default when I boot from Live CD. I will try again after mounting the drive containing the ubuntu folder.

---

### Post by lordjj on 2011-02-14
So, this time I mounted the Hard disk before running the commands & skipped the 2nd step, here's what I got:

```
ubuntu@ubuntu:~$ sudo mkdir /media/win
mkdir: cannot create directory `/media/win': File exists
ubuntu@ubuntu:~$ mount | grep 'sda1'
/dev/sda1 on /media/win type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /media/win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```Am I doing something wrong? :(

---

### Post by bcbc on 2011-02-14
> **lordjj said:**
> So, this time I mounted the Hard disk before running the commands & skipped the 2nd step, here's what I got:

```
ubuntu@ubuntu:~$ sudo mkdir /media/win
mkdir: cannot create directory `/media/win': File exists
ubuntu@ubuntu:~$ mount | grep 'sda1'
/dev/sda1 on /media/win type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /media/win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```Am I doing something wrong? :(
Try the following (ls = lower case LS, -l = lower case -L)
```
ls -l /media/win/ubuntu/disks
```

---

### Post by bcbc on 2011-02-14
I suspect that you are going to have to run chkdsk - the file is probably corrupted. (And then just hope it survives.)

Normally Wubi syncs file changes immediately to avoid ntfs corruption, however, if the power outage happened at the wrong time this can't always be avoided.

---

### Post by lordjj on 2011-02-14
```
ubuntu@ubuntu:~$ ls -l /media/win/ubuntu/disks
total 262144
drwxrwxrwx 1 root root         0 2010-10-06 12:03 boot
-rwxrwxrwx 2 root root 268435456 2010-10-06 15:16 swap.disk
```

I then rebooted; things are still the same...

---

### Post by lordjj on 2011-02-14
Just a question guys; does this happen in a normal installation of Ubuntu (not through Wubi)? 
Because I think I've heard of cases where it does. & if it does, is it at least easier to fix?

---

### Post by bcbc on 2011-02-14
> **lordjj said:**
> ```
ubuntu@ubuntu:~$ ls -l /media/win/ubuntu/disks
total 262144
drwxrwxrwx 1 root root         0 2010-10-06 12:03 boot
-rwxrwxrwx 2 root root 268435456 2010-10-06 15:16 swap.disk
```

I then rebooted; things are still the same...

Your root.disk is missing. 

This won't happen on a normal install of Ubuntu. While it's possible that a file or two may be corrupted - this is easier to recover from (or at least recover the uncorrupted files manually if you can't boot normally) - whereas with Wubi everything is on a single file (root.disk) and if you lose it, you lose everything.

You may still be able to recover. If XP thinks the file is still there, then try the check disk thing, and see if that makes the root.disk show up.

---

### Post by lordjj on 2011-02-14
The strange thing is that root.disk was there before; then it disappeared, I think either after running commands from Ubuntu Live CD (perhaps the Wubi Megathread solution) or after WIndows performed a chkdsk upon booting.

Well anyway I ran chkdsk again, and root.dosk didn't appear...

---

### Post by bcbc on 2011-02-14
Last gasp: check again in the c:\FOUND.000

---

### Post by lordjj on 2011-02-14
sigh... I guess I'll just remove the Wubi installation and Install Ubuntu regularly, and keep in mind the limitations of Wubi. For the future, I understand that if Ubuntu freezes and won't shutdown I should hold cntrl + alt + prtscrn and press R,E,I,S,U,B, to attempt a safe shutdown and not corrupt files, correct? And if that doesn't work, what's the worst thing that can happen from a sudden power off on a normal Ubuntu installation?

---

### Post by lordjj on 2011-02-14
FOUND.000 doesn't exist either...

---

### Post by bcbc on 2011-02-14
Bear in mind that FOUND.xxx directories are hidden. But it sounds like you know this.

The worst thing that can happen - when you get a power outage with a normal install - is that you can corrupt the files you are working on, or render the OS unbootable if it happens during an upgrade. If it's a normal update, you might have to rely on an older kernel (always keep two working kernels). I suppose you might get unlucky and have it become unbootable wihtout doing something exceptional:
BUT in all these cases, you can either repair everything or at least recover the rest of your data.

As opposed to Wubi. If you use Wubi it's a good idea to keep a complete root.disk backup (periodically) and make sure all personal data is regularly backed up.

PS Wubi does mitigate the risk somewhat with instant synching but - that's cold comfort when you've lost everything.

---

### Post by lordjj on 2011-02-14
Well thanks everyone for the help :p. I guess a normal install will be safer anyway. Btw, bcbc, what do you mean by:
> (always keep two working kernels)

---

### Post by bcbc on 2011-02-15
When there is a new kernel released you'll see it added to your grub menu. These can grow over time, but you can uninstall the older ones to save space and unclutter your grub menu. However, it's always a good idea to have two bootable kernels. (On an initial install you'll only have the single kernel). Lately there've been some kernel updates on the same patch level that have not been properly applied (maybe due to errors in the postinst procedures that update the initial ram disk) and this has caused booting problems. So it's a good idea to be cautious when updating kernels if you only have one available.

---

