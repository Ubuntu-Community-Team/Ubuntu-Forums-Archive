---
title: "floppy doesnt work"
date: 2012-08-19
forum: General Help
---

### Post by chevyiron420 on 2012-08-19
When I put a floppy in the drive it doesnt do anything. If I go to places and click on floppy0 I get a message that it cant mount because floppy0 doent exist. This is a fresh install of 9.1 and upgraded to 10.04. I have been through this before but i just cant remember what to do. Please help.

---

### Post by llamabr on 2012-08-19
Man, you still have a floppy drive?  That deserves a LOL.

Put the disk in, count to ten, and post the outputs of:

```
dmesg | tail 
```

and 

```
df
```

---

### Post by chevyiron420 on 2012-08-20
> **llamabr said:**
> Man, you still have a floppy drive?  That deserves a LOL.

Put the disk in, count to ten, and post the outputs of:

```
dmesg | tail 
```and 

```
df
```
A lot of my model airplane plans are on floppys. Ok I dont know how to do this, but here goes.
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76201792   4615564  67715368   7% /
none                    104896       260    104636   1% /dev
none                    109136       120    109016   1% /dev/shm
none                    109136        84    109052   1% /var/run
none                    109136         0    109136   0% /var/lock
none                    109136         0    109136   0% /lib/init/rw

---

### Post by chevyiron420 on 2012-08-20
> **llamabr said:**
> Man, you still have a floppy drive?  That deserves a LOL.

Put the disk in, count to ten, and post the outputs of:

```
dmesg | tail 
```and 

```
df
```
I found, on a different forum where i had this problem back in 2009 and i tried to do what i did then. It tries to work now but it says there is no media in drive. I thought i better re-do what you asked for.
philip@philip-desktop:~$ dmesg | tail
[   12.249368] type=1505 audit(1345442803.511:9):  operation="profile_replace" pid=581 name="/sbin/dhclient3"
[   12.250547] type=1505 audit(1345442803.511:10):  operation="profile_replace" pid=581 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.252158] type=1505 audit(1345442803.515:11):  operation="profile_replace" pid=581 name="/usr/lib/connman/scripts/dhclient-script"
[   14.474733] ppdev: user-space parallel port driver
[   16.246198] [drm] Initialized drm 1.1.0 20060810
[   16.279888] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   16.288400] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   16.288446] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   16.288520] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   22.358797] eth1: no IPv6 routers present
philip@philip-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76201792   4621344  67709588   7% /
none                    104896       264    104632   1% /dev
none                    109136       120    109016   1% /dev/shm
none                    109136        84    109052   1% /var/run
none                    109136         0    109136   0% /var/lock
none                    109136         0    109136   0% /lib/init/rw



[   16.288446] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   16.288520] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   22.358797] eth1: no IPv6 routers present
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76201792   4621128  67709804   7% /
none                    104896       264    104632   1% /dev
none                    109136       120    109016   1% /dev/shm
none                    109136        84    109052   1% /var/run
none                    109136         0    109136   0% /var/lock
none                    109136         0    109136   0% /lib/init/rw
p

---

### Post by plucky on 2012-08-20
From a terminal ```
udisks --mount /dev/fd0
``` and you should be able to see the floppy on the Desktop or the File Manager.


Good Luck

---

### Post by chevyiron420 on 2012-08-20
> **plucky said:**
> From a terminal ```
udisks --mount /dev/fd0
``` and you should be able to see the floppy on the Desktop or the File Manager.


Good Luck
Didnt seem to do anything. It wont mount and says there is no media. When i try my floppy formatter it says the device is not defined.

---

### Post by sakamoto on 2012-08-20
> **llamabr said:**
> Man, you still have a floppy drive?  That deserves a LOL.


why? almost all old pc's still have floppy drives...

---

### Post by plucky on 2012-08-20
> **chevyiron420 said:**
> Didnt seem to do anything. It wont mount and says there is no media. When i try my floppy formatter it says the device is not defined.

Post output for ```
cat /etc/fstab
```

Can you see it in the BIOS?

Can you boot from the floppy drive?

---

### Post by chevyiron420 on 2012-08-20
> **plucky said:**
> Post output for ```
cat /etc/fstab
```Can you see it in the BIOS?

Can you boot from the floppy drive?
philip@philip-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6ba81ee3-9898-4584-b81c-da5d758adf9c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=17802ae8-34b8-4d3c-aff7-97ea4c605730 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
Yes its in the bios and it did try to boot from a old dos disk but the disk was bad. In the past wen i put a floppy in the light came on for a second, then it appeared on the desktop. It doesn't do that now.

---

### Post by plucky on 2012-08-20
Go [Here](http://www.plop.at/en/bootmanager/plpbt.bin.html#runflp) and download the Plop Boot Loader for the floppy.

Then cd to the Download directory and run ```
dd if=plpbt.img of=/dev/fd0
``` and see if it writes to the floppy.

p.s. Use a blank floppy as it will overwrite it.

---

### Post by llamabr on 2012-08-20
> **chevyiron420 said:**
> A lot of my model airplane plans are on floppys. Ok I dont know how to do this, but here goes.
Usage: dmesg [-c] [-n level] [-r] [-s bufsize]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76201792   4615564  67715368   7% /
none                    104896       260    104636   1% /dev
none                    109136       120    109016   1% /dev/shm
none                    109136        84    109052   1% /var/run
none                    109136         0    109136   0% /var/lock
none                    109136         0    109136   0% /lib/init/rw

You didn't do dmesg right.  Just type it in, and copy/paste the whole thing.  Use the little hash tags above to seperate code.

---

### Post by chevyiron420 on 2012-08-20
> **plucky said:**
> Go [Here]("http://www.plop.at/en/bootmanager/plpbt.bin.html#runflp") and download the Plop Boot Loader for the floppy.

Then cd to the Download directory and run ```
dd if=plpbt.img of=/dev/fd0
``` and see if it writes to the floppy.

p.s. Use a blank floppy as it will overwrite it.
Ok I went there and downloaded it, but I dont understand what to do with it. I dont know what cd to the Download directory means or where I could run code there. Please explain, i,m a real dummy with this.

---

### Post by chevyiron420 on 2012-08-20
> **llamabr said:**
> You didn't do dmesg right.  Just type it in, and copy/paste the whole thing.  Use the little hash tags above to seperate code. I have to copy and past everything cause this computer has no pipe symbol, plus I dont know what im doing. So here is another try. I think I left a DVD in the drive, i hope it doesnt matter.
philip@philip-desktop:~$ dmesg | tail
[   13.917619] eth1: link up, 100Mbps, full-duplex, lpa 0x45E1
[   16.253722] ppdev: user-space parallel port driver
[   18.402846] [drm] Initialized drm 1.1.0 20060810
[   18.429535] [drm] Initialized via 2.11.1 20070202 for 0000:01:00.0 on minor 0
[   18.434038] agpgart-via 0000:00:00.0: AGP 2.0 bridge
[   18.434085] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   18.434160] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   24.300346] eth1: no IPv6 routers present
[   35.689685] UDF-fs: Partition marked readonly; forcing readonly mount
[   35.722427] UDF-fs INFO UDF: Mounting volume 'WDOA_S1D1', timestamp 2009/09/23 09:32 (1f10)
philip@philip-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             76201792   4733640  67597292   7% /
none                    104896       264    104632   1% /dev
none                    109136       120    109016   1% /dev/shm
none                    109136        84    109052   1% /var/run
none                    109136         0    109136   0% /var/lock
none                    109136         0    109136   0% /lib/init/rw
/dev/sr0               7999314   7999314         0 100% /media/cdrom0

---

### Post by llamabr on 2012-08-20
This was a dmesg right after you put the floppy in?

You don't have a | symbol?

---

### Post by chevyiron420 on 2012-08-20
> **llamabr said:**
> This was a dmesg right after you put the floppy in?

You don't have a | symbol?
Yes, I put a floppy i, waited about 10 seconds and started terminal. I think I forgot there was a DVD in the drive from last night. Hope it doesnt matter. No, the system im working on has no pipe symbol. In the past, with the system running, wen I put a floppy in the light would come on, the drive would run for a second or two. It doesn't do that anymore. I thought the drive might be bad so I tried four more of them last night and they all act the same. This drive worked fine until I re-installed ubuntu.

---

### Post by chevyiron420 on 2012-08-20
> **llamabr said:**
> This was a dmesg right after you put the floppy in?

You don't have a | symbol?
 Also, now if I put a floppy in and go to places and click on floppy the light comes on and the drive runs and then says it cant mount cause there is no media in the drive.

---

### Post by chevyiron420 on 2012-08-21
Any ideas? I'm getting desperate.

---

### Post by plucky on 2012-08-21
> Ok I went there and downloaded it, but I dont understand what to do with it. I dont know what cd to the Download directory means or where I could run code there. Please explain, i,m a real dummy with this. 

From a terminal ```
cd Downloads
``` will take you to the /Downloads directory.

Then type ```
ls
``` and it will give you a list of folders and files in the directory.You should see the file plpbt.img if it is in the /Downloads directory.

Insert a blank floppy into the drive,then run the "dd" command and see if it is able to copy the image to the floppy.

You might have to use sudo in front of the command if it gives you a "permission denied" message.

If it completes,try to boot the floppy.

Good luck

---

### Post by redmk2 on 2012-08-21
> **chevyiron420 said:**
> Any ideas? I'm getting desperate.

I believe [**_[COLOR="Blue"]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1725057&page=2") has all that you will need.

---

### Post by chevyiron420 on 2012-08-21
> **plucky said:**
> From a terminal ```
cd Downloads
``` will take you to the /Downloads directory.

Then type ```
ls
``` and it will give you a list of folders and files in the directory.You should see the file plpbt.img if it is in the /Downloads directory.

Insert a blank floppy into the drive,then run the "dd" command and see if it is able to copy the image to the floppy.

You might have to use sudo in front of the command if it gives you a "permission denied" message.

If it completes,try to boot the floppy.

Good luck
  When I type in dd or sudo dd it doesnt do anything. I probably didnt download it right. I see the plpbt there but it is in blue and off to the right???

---

### Post by chevyiron420 on 2012-08-21
> **redmk2 said:**
> I believe [**_[COLOR=Blue]this thread[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1725057&page=2") has all that you will need.
  This seemed to fix it, thank you very much!!!! One thing though, the drive used to light up and put up a icon when I inserted a disk. Now I have to go to places and click on floppy. Is there anything I can do? If not its ok the way it is.:p

---

