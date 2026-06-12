---
title: "Can't boot: One or more of the mounts listed in /etc/fstab cannot yet be mounted"
date: 2010-01-06
forum: General Help
---

### Post by Endolith on 2010-01-06
I "upgraded" to Karmic and now my computer won't start.  It shows the grub menu, I select the first Ubuntu option, and it shows the white logo.  Underneath the logo these words appear, and it does nothing:

> One or more of the mounts listed in /etc/fstab cannot yet be mounted: /boot: waiting for UUID=338c820e...
Press ESC to enter a recovery shell

---

### Post by EricAllenGA on 2010-01-06
I am having the same problem.  My problem started when my hard drive failed and I got a new one to replace it.  I was running a dual boot Windows XP and Ubuntu 9.10.  These are the steps I did to try and get back.
 
I had a ghost image backup of the entire drive with all windows and linux partitions from a few months ago, so I restored that.  Back then I was at version 9.04 Ubuntu.  I had upgraded to 9.10 recently.  My LATEST image backups were done using image for windows and image for linux.
 
I restored my latest image for windows backup and then I restored my latest image for linux backup (which was 9.10 ubuntu).
 
Windows worked fine, but linux wouldn't boot up.  I don't remeber the error.
 
So what I did was deleted the linux partitions using windows.  Then I reinstalled linux 9.04 fresh from CD.  Then I reran my latest image for linux restore.  After that linux came up just fine.  Everything seemed to be fine.  All updates were current.  The next time I tried to bring it up, I got the same error as you.
 
I am new to linux so I don't know what to look for but I believe my problem is the UUID number for the swap file partition.  Maybe the grub menu startup needs to be changed.  I guess when I reinstalled ubuntu or re-created the partitions, it assigned a different UUID number to the swap partition.  Sometimes I can enter a debug screen and it will say something like it is waiting for UUID=f2e97f71-51b4-41dd-8645-4f4c31643b18.  I was able to see the UUID of the swap file as it is now and it is a different number than that.
 
I also wonder if I should have manually upgraded from 9.04 to 9.10 after my original restore and then restored my latest image backup.
 
I hope this information helps.
 
Thanks,
Eric Allen

---

### Post by Endolith on 2010-01-07
The UUID hasn't changed, the partition is mountable and I can change the files (I tried changing menu.lst but it didn't act any different), and I've run disk checks lately with no problems. I don't know why it's doing this.

---

### Post by EricAllenGA on 2010-01-07
I have finally fixed mine.  This is what I think happened.  When I recreated my partitions and reinstalled ubuntu 9.04.  The swap partition UUID # was changed.  I then restored my latest image backup and the /etc/fstab had the old UUID # for the swap.

This is what I did to fix.  I booted up with the live CD and opened a terminal window.  Typed "sudo blkid".  This showed me the current UUID # for the swap partition.  Then I typed "sudo gedit".  In gedit screen, I opened the /etc/fstab file and changed the swap partition UUID # to the one listed from the blkid command.  Saved the file and rebooted.  Everything seems fine now.

Hope this helps,
Eric Allen

---

### Post by Endolith on 2010-01-08
I left mine on that page for hours and it just sat there and did nothing.  I don't know what the message means or why it's there.  I've given up on Ubuntu and gone back to XP for now.

---

### Post by drpiotrowski on 2010-01-08
Bump

---

### Post by Leppie on 2010-01-08
> **Endolith said:**
> I left mine on that page for hours and it just sat there and did nothing.  I don't know what the message means or why it's there.  I've given up on Ubuntu and gone back to XP for now.
which version of grub do you have installed, grub legacy or grub2?
what filesystem type is your /boot partition?

---

### Post by Endolith on 2010-01-08
I installed grub 2 while still using jaunty.  It worked fine until the upgrade.

---

### Post by Leppie on 2010-01-08
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?
you will have to make it executable:
```
chmod +x boot_info_script*.download && sudo bash ./boot_info_script*.download
```

---

### Post by Endolith on 2010-01-08
Here it is

Thanks for the help

---

### Post by Leppie on 2010-01-09
booting from a livecd, try the following:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda7 /mnt/temp/
mount /dev/sda5 /mnt/temp/boot
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub
apt-get purge grub-pc grub-common
apt-get install grub-pc grub-common
exit
```
this process should completely remove grub legacy and grub2 including configuration files. if the command "apt-get purge grub" returns a message like grub isn't installed, then don't worry about that.
dpkg will come up with some screens while installing grub2, choose the correct options (like where to install grub2, this should be /dev/sda).
after this you should have grub v1.97 installed on your system, this is the current version of grub2
reboot to check if it's working correctly.

---

### Post by Endolith on 2010-01-09
apt-get can't see any servers, so it won't install  "Could not resolve"

---

### Post by Leppie on 2010-01-09
are you able to connect to the internet using the livecd?

---

### Post by Endolith on 2010-01-09
yes, but not with apt-get.

```
ubuntu@ubuntu:~$ ping canonical.com
PING canonical.com (91.189.94.253) 56(84) bytes of data.
64 bytes from vostok.canonical.com (91.189.94.253): icmp_seq=1 ttl=44 time=97.3 ms
64 bytes from vostok.canonical.com (91.189.94.253): icmp_seq=2 ttl=44 time=96.8 ms
64 bytes from vostok.canonical.com (91.189.94.253): icmp_seq=3 ttl=44 time=96.7 ms
^C
--- canonical.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2010ms
rtt min/avg/max/mdev = 96.749/96.954/97.309/0.438 ms
ubuntu@ubuntu:~$ sudo chroot /mnt/temp/
root@ubuntu:/# ping canonical.com
ping: unknown host canonical.com
root@ubuntu:/# 




```

---

### Post by Leppie on 2010-01-09
you can download the packages here:
grub-pc: [http://packages.ubunut.com/karmic/grub-pc](http://packages.ubunut.com/karmic/grub-pc)
grub-common: [http://packages.ubunut.com/karmic/grub-common](http://packages.ubunut.com/karmic/grub-common)

first install grub-common with either gdebi or dpkg and then install grub-pc.

---

### Post by Endolith on 2010-01-09
Done, but it still does the same thing.

---

### Post by Leppie on 2010-01-09
could you run that script again and post the results?

---

### Post by Endolith on 2010-01-10
yep

---

### Post by Endolith on 2010-01-11
No one has any ideas?

---

### Post by Endolith on 2010-01-13
No one can help with this?

---

### Post by Leppie on 2010-01-14
> **Endolith said:**
> Done, but it still does the same thing.
did you amend the commands as well?
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda7 /mnt/temp/
mount /dev/sda5 /mnt/temp/boot
cp ~/Desktop/grub* /mnt/temp/home/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub
apt-get purge grub-pc grub-common
cd home
dpkg -i grub-pc_1.97~beta4-1ubuntu4.1_i386.deb
dpkg -i grub-common_1.97~beta4-1ubuntu4.1_i386.deb
rm *.deb
exit
```
i don't know where you put the downloaded .deb packages, so i assumed the desktop. change this to whichever location you downloaded the packages.
i used the i386 packages as example, if you have ax x64 system you need to amend the names of those packages (you could use tab completion for this).

---

### Post by Endolith on 2010-01-14
> **Leppie said:**
> did you amend the commands as well?
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda7 /mnt/temp/
mount /dev/sda5 /mnt/temp/boot
cp ~/Desktop/grub* /mnt/temp/home/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub
apt-get purge grub-pc grub-common
cd home
dpkg -i grub-pc_1.97~beta4-1ubuntu4.1_i386.deb
dpkg -i grub-common_1.97~beta4-1ubuntu4.1_i386.deb
rm *.deb
exit
```i don't know where you put the downloaded .deb packages, so i assumed the desktop. change this to whichever location you downloaded the packages.
i used the i386 packages as example, if you have ax x64 system you need to amend the names of those packages (you could use tab completion for this).

I'm not sure what you mean by "amend the commands", but I did all of the things listed here.  GRUB 1.97 is successfully installed, as it shows in RESULTS1.txt  

> Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /grub.It then shows the white Ubuntu logo in the middle of the screen, which I don't think is part of GRUB.  So, both before and after this change, it would seem GRUB was working and passing execution onto Ubuntu Karmic, which is the part that's not working.  It also boots into Windows fine from GRUB, so I don't think it's the problem.

To clarify: I upgraded GRUB following these directions a few days ago.  RESULTS.txt is the boot info script before the upgrade, and RESULTS1.txt (inside RESULTS1.zip) is the boot info script after the upgrade.  The behavior is the same both before and after the upgrade.  It gets to the white Ubuntu logo, displays the "cannot yet be mounted" message, and does nothing.

---

### Post by Endolith on 2010-01-15
.

---

### Post by Endolith on 2010-01-16
Actually, I found the old fstab and it's not any different.  /dev/sda5, which is the boot partition, is not visible:

```
 ~> la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 140 2010-01-16 02:55 ./
drwxr-xr-x 6 root root 120 2010-01-15 18:04 ../
lrwxrwxrwx 1 root root  10 2010-01-16 02:55 07D4-0918 -> ../../sda1
lrwxrwxrwx 1 root root  10 2010-01-16 02:55 5497-3D7E -> ../../sda6
lrwxrwxrwx 1 root root  10 2010-01-15 18:04 57882a85-8d4c-4adc-84eb-a47e191b3007 -> ../../sda7
lrwxrwxrwx 1 root root  10 2010-01-15 18:04 709CF04A9CF00C7A -> ../../sda2
lrwxrwxrwx 1 root root  10 2010-01-15 18:04 7422e7a6-03a3-4fb6-8666-968989e2f935 -> ../../sda8

``````
~> sudo mount /boot
mount: special device UUID=338c820e-d3b1-42bc-8966-b89e212547b2 does not exist
``````
~> sudo mount /dev/sda5 /boot
mount: /dev/sda5: can't read superblock
```

---

### Post by Leppie on 2010-01-16
try checking the partition for errors with fsck:
```
sudo fsck /dev/sda5
```

also try to see what fdisk says:
```
sudo fdisk /dev/sda
```

---

### Post by Endolith on 2010-01-16
```
~> sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Boot was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

Boot: ***** FILE SYSTEM WAS MODIFIED *****
Boot: 185/144576 files (9.2% non-contiguous), 59928/289138 blocks
``````
~> sudo fsck /dev/sda5
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
Boot: clean, 185/144576 files, 59928/289138 blocks
```

```
~> sudo fdisk /dev/sda

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3921    31455270    7  HPFS/NTFS
/dev/sda3            3922        4379     3678885   db  CP/M / CTOS / ...
/dev/sda4            4380       19457   121114035    f  W95 Ext'd (LBA)
/dev/sda5            4380        4415      289138+  83  Linux
/dev/sda6            4416        4510      763056    c  W95 FAT32 (LBA)
/dev/sda7            4511       19092   117129883+  83  Linux
/dev/sda8           19093       19457     2931831   82  Linux swap / Solaris

```

---

### Post by Leppie on 2010-01-16
have you tried to reboot already?
seems like your boot partition should now be ok

---

### Post by Endolith on 2010-01-16
No it still gives the same error.  It can't mount the boot partition for some reason.  Windows can mount it using Ext2IFS, but Ubuntu can't.

---

### Post by Leppie on 2010-01-16
> **Endolith said:**
> No it still gives the same error.  It can't mount the boot partition for some reason.  Windows can mount it using Ext2IFS, but Ubuntu can't.
do you often go into the boot partition from windows? what kind of access do you have in windows (read-only, read/write)?

---

### Post by Endolith on 2010-01-16
> **Leppie said:**
> do you often go into the boot partition from windows? what kind of access do you have in windows (read-only, read/write)?

Only since it stopped booting.  It is read-write access, but it was working fine until the upgrade to Karmic, and I didn't access it from Windows until after that.  It boots, using the boot partition, but then Linux can't see the boot partition.  I don't get it.

---

### Post by Endolith on 2010-01-16
I changed

```
UUID=338c820e-d3b1-42bc-8966-b89e212547b2 /boot ext2 relatime 0 2
```to 

```
/dev/sda5 /boot ext2 relatime 0 2
```and it booted and /boot has the boot partition's files in it, instead of the root partition's.  So the boot partition no longer has a UUID or something?

---

### Post by dcstar on 2010-01-16
> **Endolith said:**
> 
...........
```
~> sudo fdisk /dev/sda

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        3921    31455270    7  HPFS/NTFS
/dev/sda3            3922        4379     3678885   db  CP/M / CTOS / ...
**/dev/sda4            4380       19457   121114035    f  W95 Ext'd (LBA)**
/dev/sda5            4380        4415      289138+  83  Linux
/dev/sda6            4416        4510      763056    c  W95 FAT32 (LBA)
/dev/sda7            4511       19092   117129883+  83  Linux
/dev/sda8           19093       19457     2931831   82  Linux swap / Solaris

```

How is an Extended Partition type "**f**"?, it should be type 5.

This could confuse the system.

---

### Post by Endolith on 2010-01-16
**05  DOS 3.3+ Extended Partition**
Supports at most 8.4 GB disks: with type **05** DOS/Windows will not use the extended BIOS call, even if it is available. See type **0f** below. Using type **05** for extended partitions beyond 8 GB may lead to data corruption with MSDOS.
[B]
0e  WIN95: DOS 16-bit FAT, LBA-mapped[/B]  
**0f  WIN95: Extended partition, LBA-mapped**
Windows 95 uses **0e** and **0f** as the extended-INT13 equivalents of **06** and **05**. For the problems this causes, see [Possible data loss with LBA and INT13 extensions]("http://support.microsoft.com/support/kb/peropsys/win95/q148821.asp"). (Especially when going back and forth between MSDOS and Windows 95, strange things may happen with a type **0e** or **0f** partition.) Windows NT does not recognize the four W95 types **0b**, **0c**, **0e**, **0f** ( [Win95 Partition Types Not Recognized by Windows NT]("http://support.microsoft.com/support/kb/articles/q151/4/14.asp")). DRDOS 7.03 does not support this type (but DRDOS 7.04 does).

This partition was created with GParted, so I don't think it's the cause of any problems.  It worked fine with Jaunty.

"This is because W95 Ext'd is the most common form - and is generally recognized by every OS / partition tool. The other [5 Extended] is less common and might not be universally recognized." [http://forums.fedoraforum.org/showthread.php?t=29534](http://forums.fedoraforum.org/showthread.php?t=29534)

"**Here are the most important identifiers**:
[LIST]
[*]...
[*]**5**: Extended partition (contains logical partitions)
[*]**f**: Extended LBA partition (contains logical partitions)"
[/LIST]
[http://www.sysresccd.org/Sysresccd-Partitioning-EN-Partitions-attributes](http://www.sysresccd.org/Sysresccd-Partitioning-EN-Partitions-attributes)

---

### Post by dcstar on 2010-01-21
> **Endolith said:**
> **0e  WIN95: DOS 16-bit FAT, LBA-mapped**  
**0f  WIN95: Extended partition, LBA-mapped**
Windows 95 uses **0e** and **0f** as the extended-INT13 equivalents of **06** and **05**. For the problems this causes, see [Possible data loss with LBA and INT13 extensions]("http://support.microsoft.com/support/kb/peropsys/win95/q148821.asp"). (Especially when going back and forth between MSDOS and Windows 95, strange things may happen with a type **0e** or **0f** partition.) Windows NT does not recognize the four W95 types **0b**, **0c**, **0e**, **0f** ( [Win95 Partition Types Not Recognized by Windows NT]("http://support.microsoft.com/support/kb/articles/q151/4/14.asp")). DRDOS 7.03 does not support this type (but DRDOS 7.04 does).

And has anyone checked to see if Grub2 actually supports these ancient Windows Extended Partition types?

Legacy Grub may well have, but Grub2 may actually turn its nose up at this old rubbish.

---

### Post by Endolith on 2010-01-21
> **dcstar said:**
> And has anyone checked to see if Grub2 actually supports these ancient Windows Extended Partition types?

Legacy Grub may well have, but Grub2 may actually turn its nose up at this old rubbish.

What does GRUB have to do with it?

---

### Post by Leppie on 2010-01-21
> **Endolith said:**
> What does GRUB have to do with it?
grub has to load modules to support the filesystems onto which grub.cfg or menu.lst is installed.
i found a fat.mod in my grub folder, i think it does support as from fat12 (though the official grub2 documentation doesn't seem to be very helpful).

---

### Post by Endolith on 2010-01-21
> **Leppie said:**
> grub has to load modules to support the filesystems onto which grub.cfg or menu.lst is installed.
i found a fat.mod in my grub folder, i think it does support as from fat12 (though the official grub2 documentation doesn't seem to be very helpful).

GRUB reads the /etc/fstab file?

---

### Post by Leppie on 2010-01-21
> **Endolith said:**
> GRUB reads the /etc/fstab file?
i don't get how you could've understood that from my post...

---

### Post by Endolith on 2010-01-21
I don't understand why anyone is talking about GRUB when my problem occurs after GRUB has handed off execution to the kernel.  GRUB is working fine, as far as I know.  If you know better than I, please explain what you're talking about.

---

### Post by nomnex on 2010-01-24
Endolith, I had a different problem but that might be related? I fixed it replacing the /dev UUIDs by the labels, see [1].

Not sure if it can help?

[1] [https://bugs.launchpad.net/ubuntu/+bug/511963](https://bugs.launchpad.net/ubuntu/+bug/511963)

---

### Post by Endolith on 2010-01-24
Yes, I changed the UUID to /dev/sda5 and it works.  I don't understand why the UUID isn't working anymore though.

---

### Post by nomnex on 2010-01-25
They should work [the very same UUID's] if you update fstab with the output of the command blkid after logging-in. i.e. /dev/sd... back to its UUID.

---

### Post by Endolith on 2010-01-25
> **nomnex said:**
> They should work [the very same UUID's] if you update fstab with the output of the command blkid after logging-in. i.e. /dev/sd... back to its UUID.

So

1. Edit fstab, change UUID to /dev/sda5
2. Boot and login
3. Edit fstab, change /dev/sda5 back to UUID

?

---

### Post by nomnex on 2010-01-27
Correct,

UUIDs are better than labels or dev names, to avoid conflict, in the event you mount several dev.

Side note: /home UUID broke for the second time yest. Since I am on a notebook with only one HD (Karmic fresh install) I might keep the dev name till the next LTS in April, and open a new bug if the problem is still recurrent.

---

### Post by Endolith on 2010-02-01
Yeah, that doesn't work.  The UUID doesn't exist in /dev/disk/by-uuid either

---

### Post by nomnex on 2010-02-02
They are, on a fresh install

```
me@it:/dev/disk/by-uuid$ ls -lh
total 0
lrwxrwxrwx 1 root root 10 2010-02-03 09:44 1a7f69cc-43d3-4f21-a32e-23d9f41f4fc4 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-02-03 10:50 8c0db18d-de9d-4d44-bc0b-fe96c0edfb8d -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-02-03 09:44 a0638e4f-b9ab-4a0c-b379-ae326c588270 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-02-03 09:44 e2cca39c-70bb-46be-a5d1-2fdafe1dd2a1 -> ../../sda5

```What's the output of the command
```
sudo blkid
```

---

### Post by Endolith on 2010-02-02
```
~> sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DELLUTILITY" UUID="07D4-0918" TYPE="vfat" 
/dev/sda2: UUID="709CF04A9CF00C7A" LABEL="Windows XP" TYPE="ntfs" 
/dev/sda3: LABEL="DELLPCRESTO" TYPE="vfat" 
/dev/sda6: LABEL="PHAT RIDE" UUID="5497-3D7E" TYPE="vfat" 
/dev/sda7: LABEL="Jaunty" UUID="57882a85-8d4c-4adc-84eb-a47e191b3007" TYPE="ext3" 
/dev/sda8: UUID="7422e7a6-03a3-4fb6-8666-968989e2f935" TYPE="swap" 

```

sda5's not in the list

---

### Post by nomnex on 2010-02-03
I used the tty console at boot time, since I could not log-in. dev/sda5 was missing when I ran "blkid". I changed the UUID to label in the fstab, to be able to log-in and restarted. The command "blkid" returned all the dev/ and their correct UUID this time.

If that does not work, my best bet would be to mount the vol manually and to modify the fstab.

---

