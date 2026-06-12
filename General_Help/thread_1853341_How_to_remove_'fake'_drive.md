---
title: "How to remove 'fake' drive?"
date: 2011-10-02
forum: General Help
---

### Post by sweetchuggagun on 2011-10-02
Hello dear community!

Recently I had a problem with a partition that I couldn't mount so I used TestDisk to recover my data. After this I formated the partition and mounted as a new one. But before this I tried to mount the volume by creating a folder into /media and tried to link the volume to this folder(I can't remember how i did this, it was written somewhere on the forum). 

I have removed the folder from media but now it appears to me in Computer what it looks like a partition and when I click on it I get this error: Unable to mount 50GB
ntfs-3g: Failed to access volume 'UUID=BC540E78540E35A4': No such file or directory

ntfs-3g 2010.8.8 external FUSE 28 - Third Generation NTFS Driver
		Configuration type 1, XATTRS are on, POSIX ACLS are off

Copyright (C) 2005-2007 Yura Pakhuchiy
Copyright (C) 2006-2009 Szabolcs Szakacsits
Copyright (C) 2007-2010 Jean-Pierre Andre
Copyright (C) 2009 Erik Larsson

Usage:    ntfs-3g [-o option[,...]] <device|image_file> <mount_point>

Options:  ro (read-only mount), remove_hiberfile, uid=, gid=,
          umask=, fmask=, dmask=, streams_interface=, syncio.
          Please see the details in the manual (type: man ntfs-3g).

Example: ntfs-3g /dev/sda1 /mnt/windows

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

Running sudo fdisk -l 
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71a28c9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1246    10000000    b  W95 FAT32
/dev/sda2            3106        9728    53192449    f  W95 Ext'd (LBA)
/dev/sda3            1246        3106    14945280   83  Linux
/dev/sda5            3200        9728    52444161    7  HPFS/NTFS
/dev/sda6            3106        3199      747520   82  Linux swap / Solaris

Partition table entries are not in disk order

So it doesn't appear here as well.

The question is - how do I remove this fake 50GB partition from computer?

---

### Post by dcstar on 2011-10-02
> **sweetchuggagun said:**
> Hello dear community!

Recently I had a problem with a partition that I couldn't mount so I used TestDisk to recover my data. After this I formated the partition and mounted as a new one. But before this I tried to mount the volume by creating a folder into /media and tried to link the volume to this folder(I can't remember how i did this, it was written somewhere on the forum). 

I have removed the folder from media but now it appears to me in Computer what it looks like a partition and when I click on it I get this error: Unable to mount 50GB
ntfs-3g: Failed to access volume '**UUID=BC540E78540E35A4**': No such file or directory
.......
The question is - how do I remove this fake 50GB partition from computer?

Look in your /etc/fstab file and delete any relevant entry.

---

### Post by coffeecat on 2011-10-02
> **sweetchuggagun said:**
> So it doesn't appear here as well.

Your sda5 is 53.6GB (base 10) or 50GiB (base 2 - gibibytes). I should imagine that is what is showing.

Post the terminal output of these commands:

```
sudo blkid
sudo fdisk -lu
cat /etc/fstab
mount
ls -l /media
```

Please enclose the output between [noparse]```
 and 
```[/noparse] tags. I've asked for "fdisk -lu" because "fdisk -l" gives output in cylinders, which is pointless.

(Footnote - the version of fdisk that comes with Oneiric will give output in sectors with the -l option, and not before time!)

---

### Post by sweetchuggagun on 2011-10-02
Output for:
```
sudo blkid
/dev/sda1: UUID="408D-FE3C" TYPE="vfat" 
/dev/sda3: UUID="f73768f8-389b-4e32-ac8a-0a437f87ec95" TYPE="ext4" 
/dev/sda5: LABEL="Mihai" UUID="5D9A8529486D0907" TYPE="ntfs" 
/dev/sda6: UUID="109ad29b-aa1d-4591-bf89-6dda19cae33a" TYPE="swap"
```

```
sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x71a28c9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20002047    10000000    b  W95 FAT32
/dev/sda2        49895422   156280319    53192449    f  W95 Ext'd (LBA)
/dev/sda3        20002816    49893375    14945280   83  Linux
/dev/sda5        51391998   156280319    52444161    7  HPFS/NTFS
/dev/sda6        49895424    51390463      747520   82  Linux swap / Solaris

Partition table entries are not in disk order

```
```

cat /etc/fstab
UUID=f73768f8-389b-4e32-ac8a-0a437f87ec95	/	ext4	defaults	01
UUID=408D-FE3C	/windows	vfat	umask=007	0	1
UUID=BC540E78540E35A4	/media/50GB	ntfs-3g	users	0	0
UUID=109ad29b-aa1d-4591-bf89-6dda19cae33a	swap	swap	sw	0	0

```
```

mount

dev/sda3 on / type ext4 (rw,commit=0)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /windows type vfat (rw,umask=007)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mihai/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mihai)

```
```

ls -l /media
total 0

```
PS I deleted what I previously added into /etc/fstab but no change so far.

---

### Post by coffeecat on 2011-10-02
Ahem. Cough, cough.

> **coffeecat said:**
> Please enclose the output between [noparse]```
 and 
```[/noparse] tags.

I've added them for you. While I'm reading your outputs now that the code tags make them readable, you might want to use the time reading this: :wink:

[http://ubuntuforums.org/misc.php?do=bbcode](http://ubuntuforums.org/misc.php?do=bbcode)

---

### Post by sweetchuggagun on 2011-10-02
Oh, sorry about that, I'm a newbie round here and I'll keep this in mind. Thank you!

---

### Post by coffeecat on 2011-10-02
The line I've highlighted in red:

> **sweetchuggagun said:**
> ```

cat /etc/fstab
UUID=f73768f8-389b-4e32-ac8a-0a437f87ec95	/	ext4	defaults	01
UUID=408D-FE3C	/windows	vfat	umask=007	0	1
[COLOR="Red"]UUID=BC540E78540E35A4	/media/50GB	ntfs-3g	users	0	0[/COLOR]
UUID=109ad29b-aa1d-4591-bf89-6dda19cae33a	swap	swap	sw	0	0

```

... needs removing. There is no partition UUID=BC540E78540E35A4 (I presume that was the UUID before you reformatted it). And you have no /media/50GB folder.

Do you see "Mihai", your sda5 partition, in the left Places pane of Nautilus? Does it automount when you click on it?

---

### Post by coffeecat on 2011-10-02
> **sweetchuggagun said:**
> Oh, sorry about that, I'm a newbie round here and I'll keep this in mind. Thank you!

No problem! It confuses a lot of people. But see how much easier it is to read the output, fdisk especially, now with code tags. That helps people to help you! :)

---

### Post by sweetchuggagun on 2011-10-02
Yes I see it and it mounts automatically

---

### Post by coffeecat on 2011-10-02
The "Unable to mount 50GB" is what dcstar said. You need to remove the fstab line I reddened.

**EDIT**: let us know what happens when you do that and reboot.

---

### Post by sweetchuggagun on 2011-10-02
Yes, it worked for me just fine! I deleted this line
```
UUID=BC540E78540E35A4	/media/50GB	ntfs-3g	users	0	0
``` 
I didn't even had to reboot. Now the computer is clean!
Thank for your time and patience - **Solved!**

---

### Post by coffeecat on 2011-10-02
Good luck with your Ubuntu-ing!

---

### Post by dcstar on 2011-10-03
Yet another reason why people should **NEVER EVER** use the /media **system folder** for manual mounts.

System folders are meant for the exclusive use of the Linux system, not for users to start playing with. So many problems are caused by people unnecessarily using system folders, if they would leave them alone these forums would be a lot quieter and Linux would have a far more reliable reputation.

Anyone posting a HOWTO telling naive users to use /media for their manual mounts should be shot - twice (just in case the first one misses)!    ;)

---

