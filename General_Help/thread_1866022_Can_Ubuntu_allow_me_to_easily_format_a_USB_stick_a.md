---
title: "Can Ubuntu allow me to easily format a USB stick and copy a file onto it?"
date: 2011-10-20
forum: General Help
---

### Post by simpleblue on 2011-10-20
I'm using another distro at the moment and I've been going through hell trying to copy one file onto my USB stick. I have a headache from the frustration I've caused myself. Sorry, just venting, but I feel like crap right now and I'm kinda having a breakdown. :(

With Ubuntu should I be able to plug my USB stick in and copy files? Or do I need to manually look up its device name, partition it, format it, mount and unmount it to the harddrive, change to proper file permissions...?

Are there instructions on how to do this? Not just instructions on how to mount it, or how to partition it, but instructions for the entire process from the very start where I plug the USB stick into the machine to the very end where the file is copied and verified that it is on the USB stick correctly then unplugged it and plugged it back in again to verify. I've tried Googling and I've yet to find a solid tutorial on copying files to a USB stick with Linux.

---

### Post by Foxheadz on 2011-10-20
Lemme guess some barebones linux like arch? 

And yes from what i know, unless you have some weird USB stick, Ubuntu should automatically mount a FAT32 Partitioned usb stick. If its partitioned to something else like NTFS or EXT4 (which it shouldnt be) you might have slight problems either opening it up in Ubuntu, or in an other non-linux operating system.

---

### Post by simpleblue on 2011-10-20
> **Foxheadz said:**
> Lemme guess some barebones linux like arch? 

And yes from what i know, unless you have some weird USB stick, Ubuntu should automatically mount a FAT32 Partitioned usb stick. If its partitioned to something else like NTFS or EXT4 (which it shouldnt be) you might have slight problems either opening it up in Ubuntu, or in an other non-linux operating system.
You've just saved my day Fox. :)

The issue was that I had formatted it to ext4. It was my best guess as to what it should be. All I had to do was:

```
mkdosfs -F 32 -I /dev/sdb
```Works fine now. I don't even have to manually mount/unmount... I just pop it in and it works!

Thanks!

* edit *

Okay, got it working a much better way:

Partition with Gparted. MSDOS with sdb1 partition as ext4.

```
[root@localhost user]# mkfs.ext4 -L myusbkey /dev/sdb1
mke2fs 1.41.14 (22-Dec-2010) Filesystem label=myusbkey OS type: Linux Block size=4096 (log=2) Fragment size=4096 (log=2) Stride=0 blocks, Stripe width=0 blocks 488640 inodes, 1952768 blocks 97638 blocks (5.00%) reserved for the super user First data block=0 Maximum filesystem blocks=2000683008 60 block groups 32768 blocks per group, 32768 fragments per group 8144 inodes per group Superblock backups stored on blocks:      32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632  Writing inode tables: done                             Creating journal (32768 blocks): done Writing superblocks and filesystem accounting information: done  This filesystem will be automatically checked every 37 mounts or 180 days, whichever comes first.  Use tune2fs -c or -i to override.
[root@localhost user]# mkdir /media/myusbkey
[root@localhost user]# mount /dev/sdb1 /media/myusbkey
[root@localhost user]# chown -R user:user /media/myusbkey
[root@localhost user]#
```[FONT=monospace]

Works perfectly now.[/FONT]

---

### Post by dcstar on 2011-10-21
Or simply use the Disk Manager or the **gparted** package to format whatever you like without resorting to a myriad of command line typing.

---

### Post by simpleblue on 2011-10-21
> **dcstar said:**
> Or simply use the Disk Manager or the **gparted** package to format whatever you like without resorting to a myriad of command line typing.
I've used both disk-utility and gparted and have found them both to not work. When I plug the USB into my other Debian computer it says:

Unable to mount 8.0 GB Filesystem

Error mounting: mount exited with code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1, missing codepage or helper program, or other error. In some casses useful info is found in syslog - try dmesg | tail or so

[http://pastie.org/2736332](http://pastie.org/2736332)

* EDIT *

I'm just going to leave this as is for now.

---

