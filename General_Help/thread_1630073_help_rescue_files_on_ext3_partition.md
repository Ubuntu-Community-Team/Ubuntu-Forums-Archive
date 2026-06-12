---
title: "help rescue files on ext3 partition"
date: 2010-11-24
forum: General Help
---

### Post by coffebrk on 2010-11-24
I recently installed a new 1 terabyte drive and reinstalled Maverick 64bit. I also copied all my video and music files from the old drive before it quit. Today I had the bright idea to create a new partition on the drive to dual boot Windows as I use some windows only apps for my business. After running Paragon partition manager and reducing the size of the existing Linux partition to 500Mb, creating a new NTSF partition, and formating the new NTSF partition to accept windows, I can no longer access my Ubuntu system. 
I have tried both the Rescatus and Supergrub 2 discs to fix the problem but neither finds an operating system. As a relative newbie I am stuck. How can I view and copy the files I need from the Linux partition before re-installing Ubuntu 10.10?

---

### Post by mikewhatever on 2010-11-24
How about you boot from the live cd/usb and post the output of 
**sudo fdisk -l** from Applications->Accessories->Terminal.
The output should show if the ext partition is still present.

---

### Post by coffebrk on 2010-11-24
The extension is definitely there.
 Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       63742   512006591   83  Linux
/dev/sde2   *       63743      120899   459113602+   7  HPFS/NTFS
/dev/sde3          120900      121601     5637345+   f  W95 Ext'd (LBA)
/dev/sde5          120900      121602     5639168   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
I can't figure out how to make it work though.

---

### Post by mikewhatever on 2010-11-25
It looks like the Linux partition is there. You can try accessing it with the file browser while running from the cd. That should allow to copy files, but you could also try fixing the bootloader using the commands below:
```
sudo mount /dev/sde1 /mnt
sudo grub-install --root-directory=/mnt /dev/sde
```

Then try booting from /dev/sde.

---

### Post by coffebrk on 2010-11-25
No Luck mounting. Here's the Error:

mount: wrong fs type, bad option, bad superblock on /dev/sde1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
and here's the Error code from dmesg:

ubuntu@ubuntu:~$ dmesg | tail
[  717.022452] EXT4-fs (sde1): ext4_check_descriptors: Checksum for group 0 failed (14669!=58474)
[  717.022464] EXT4-fs (sde1): group descriptors corrupted!
[  760.647235] EXT4-fs (sde1): ext4_check_descriptors: Checksum for group 0 failed (14669!=58474)
[  760.647246] EXT4-fs (sde1): group descriptors corrupted!
[  791.487839] EXT4-fs (sde1): ext4_check_descriptors: Checksum for group 0 failed (14669!=58474)
[  791.487852] EXT4-fs (sde1): group descriptors corrupted!
[ 2696.987230] [drm] nouveau 0000:00:0d.0: Setting dpms mode 3 on vga encoder (output 0)
[32970.563524] [drm] nouveau 0000:00:0d.0: Setting dpms mode 0 on vga encoder (output 0)
[33132.687400] EXT4-fs (sde1): ext4_check_descriptors: Checksum for group 0 failed (14669!=58474)
[33132.687412] EXT4-fs (sde1): group descriptors corrupted!

This looks BAD !!

---

### Post by mikewhatever on 2010-11-28
Yea. Try testdisk to recover some files.
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

