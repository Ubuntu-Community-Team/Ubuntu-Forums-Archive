---
title: "Trouble mounting vfat partition"
date: 2006-03-23
forum: General Help
---

### Post by deavik on 2006-03-23
Hello all, this might be slightly long so please bear with me!

I have an old Samsung HD which is, to put it mildly, not in the prime of health. Each time I have the every-30-boots filesystem check, fsck finds errors and I have to manually do 'fsck /' ... things usually work normally after that. Yesterday while mounting the root fs Ubuntu found that the drive wan't 'clean', and after running fsck  I got a *lot* of errors (to which I just said 'fix').

**1.** After that Ubuntu boots and runs OK, but I can't mount the FAT partition which I use to share file between Ubuntu and Windows. I tried a few things as follows:
```

avik@sprite:~$ sudo mount /dev/hda5
Password:
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

avik@sprite:~$ dmesg | tail
... network messages ...
[4294820.554000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[4294820.592000] Unable to load NLS charset cp437
[4294820.592000] FAT: codepage cp437 not found

avik@sprite:~$ sudo fsck /dev/hda5
fsck 1.38 (30-Jun-2005)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/hda5: 139 files, 19295/974041 clusters

```
So fsck tells me there aren't any errors on the disk, and I also checked from Windows, the FAT partitition is fine. I haven't made any changes to /etc/fstab in the meantime.

**2.** Also, after I received all those errors on my filesystem, I get two errors during Ubuntu's bootup. "Calculating module dependencies..." and "Mounting local filesystems..." show up as [failed].

Apart from this Ubuntu is running OK, what do I do to mount the FAT partition. I've tried mounting it to another loaction but it hasn't worked (same error).

Thanks!

---

### Post by NewWithoutClue on 2006-03-23
```
mount -t vfat /dev/hda5 /path/to/mount/point
```

Edit:
You ahve to tell linux what type it is unless it's a linux native filesystem. This is done with the "-t" option to the 'mount' command followed by a valid filesystem type ( vfat for fat16 or fat32 .)

---

### Post by deavik on 2006-03-23
Hi, thanks for the reply, but as I said /dev/hda5 is already in /etc/fstab so I don't need to tell mount where to mount it.

Anyhow I tried it explicitly as you wrote, it's the same :(

---

### Post by trent dillman on 2006-03-23
What's your fstab config? That might give us a better idea what's going wrong. For example, I see mention of utf8...

---

### Post by deavik on 2006-03-23
Hello trent, thanks for replying! :)

My fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5		/media/windows 	ntfs 	umask=0222 	0 	0
/dev/hda5       /media/osshare  vfat    iocharset=utf8,umask=000   0       0

```
The utf8 I think I got from the Ubuntu starter Guide. I tried removing it and sudo mount -a but I got the same message.

Are there any other log files you want the output of?

---

### Post by trent dillman on 2006-03-24
try 
/dev/hda5       /media/osshare     vfat    noexec,rw,umask=000        0       0

this is basically what I use

---

### Post by deavik on 2006-03-24
Hello,

I tried it exactly as you said, but no luck. Do you think the HD errors did something to my kernel so that it can't load all the modules (including the nls charset cp437 for the vfat)?

I saythis because the "Calculating module dependencies" fails during boot-up as I said.

---

### Post by trent dillman on 2006-03-24
Hmm...if you're not using a laptop, disable acpi on bootup and see if that helps.

---

### Post by deavik on 2006-03-25
Thanks for all the help and your patience, trent but I think the recent HD errors messed something up bad. I'm going to do a clean install of Dapper later and continue with this for the time being.

Thanks again!

---

