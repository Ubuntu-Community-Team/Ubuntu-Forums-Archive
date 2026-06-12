---
title: "Newest update broke my Ubuntu 10.04"
date: 2011-04-25
forum: General Help
---

### Post by sandman88 on 2011-04-25
just ran the update on my existing Ubuntu system and now it will not boot. I am dual booting Windows Vista with Ubuntu 10.04, today it requested an update be ran, which I allowed it to do, after which it asked to reboot the computer, after the reboot, I got past the Grub screen, it took me past the Ubuntu 10.04 boot screen, and after which it took me to a screen that says "Loading, Please wait..." and has been stuck there for the last 3 hours. any thoughts on this would be terrific, I really dont want to re-install everything.

---

### Post by K_45 on 2011-04-25
Is it still loading? Completely frozen? Was this a kernel upgrade?

---

### Post by sandman88 on 2011-04-25
it's not frozen, but seems stuck. the underscore beneath it continues to blink. also this was not a kernel upgrade, I just had my laptop open, and when I came back to it, there was a note on the screen asking to upgrade, so I allowed it.

Edit: not upgrade, the note requested to run an update

---

### Post by K_45 on 2011-04-25
Can you type anything? Try Alt+PrtScn+m - ?

---

### Post by conradin on 2011-04-25
That happend to me too earlier tonite!
So, I upgraded to maverick.
So first, I pressed ctrl+alt+F5 to get out of the froze gdm session
then, I hit some code:
```

sudo -i
pkill gdm
pkill gnome
pkill X
pkill X11

apt-get upgrade

```
Then I had to reinstall my graphics driver, but I was find after that.

---

### Post by sandman88 on 2011-04-25
I tried the ctrl+alt+prntscrn, it brought up a message asking to check the memory I think (still had the "loading, please wait...") than I tried the ctrl+alt+f5, now all I have is the blinking cursor and it will not accept any further commands. also I did a hard restart last night and let it go all night, no change.

---

### Post by K_45 on 2011-04-25
Boot into a live CD and check your HDD for any corruption:

```
mount
```

Your HDD will be listed as /dev/sdaX - note the number

```
sudo umount /dev/sdaX
``` - replacing X with the number you noted earlier.

```
fsck -y /dev/sdaX
``` - replace X with the number you noted earlier.

Reboot.

---

### Post by wilee-nilee on 2011-04-25
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Now if this is a wubi install, which means you would normally see the MS bootscreen to choose from; you need to reload the ms bootloader to the mbr.

It is important to make sure we are on the same page so run the script if you can.

---

### Post by sandman88 on 2011-04-26
sorry, just got off work, I started this out simple enough...

```

#mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

so since that did not give me any partitions, I ran fdisk


```

# sudo fdisk -l
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18ec53ea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        9918    78125000    7  HPFS/NTFS
/dev/sda3           27852       30402    20480184    7  HPFS/NTFS
/dev/sda4            9918       27851   144051103    5  Extended
/dev/sda5            9918       12468    20487154+  83  Linux
/dev/sda6   *       12469       13744    10249438+  83  Linux
/dev/sda7           13745       14127     3076416   82  Linux swap / Solaris
/dev/sda8           15403       27851    99996561   83  Linux

Partition table entries are not in disk order

```

this turned out a bit better, so I continued with the fsck on the  3 linux partitions.

```

# sudo fsck -y /dev/sda5
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda5: clean, 196280/1281120 files, 1124819/5121788 blocks

```

```

# sudo fsck -y /dev/sda6
fsck from util-linux-ng 2.17.2
Reiserfs super block in block 16 on 0x806 of format 3.6 with standard journal
Blocks (total/free): 2562352/971649 by 4096 bytes
Filesystem is clean

```

```

# sudo fsck -y /dev/sda8
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda8: clean, 1883/6250496 files, 2844729/24999140 blocks

```

---

