---
title: "Cdrom"
date: 2010-05-31
forum: General Help
---

### Post by lvleph on 2010-05-31
Well, yet another superfluous change in Ubuntu that is giving me a headache.

Where the heck is a cdrom mounted now? There is no entry in fstab, but it is certainly mounted, since I can see it on my desktop.

---

### Post by WorMzy on 2010-05-31
Everything is mounted in /media by default.

---

### Post by lvleph on 2010-05-31
Not on my machine, apparently.

**ls /media/**
```

Backup  Media

```

EDIT:
**cat /etc/fstab**
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=63eb2fb8-8e1b-47ea-9069-eca62950b890 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=1bdf2482-ade3-43a3-ac5c-a7d39d482536 /home           ext4    defaults        0       2
# /media/Backup was on /dev/sda2 during installation
UUID=dc5b2597-c57e-4e14-8029-245b04df6957 /media/Backup   ext3    defaults        0       2
# /media/Media was on /dev/sdb1 during installation
UUID=f14a38d3-7c74-453a-ae95-06f18bf87c8b /media/Media    ext4    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=572b5ea4-269e-4b8a-9960-f77f294c17b8 none            swap    sw              0       0

```

But like I said it is certainly mounted.

---

### Post by muaythaimaster74 on 2010-05-31
They're mounted in /media.

ie.. mine is /media/cdname from /dev/sr0

---

### Post by lvleph on 2010-05-31
Again, apparently not on my computer.

---

### Post by muaythaimaster74 on 2010-05-31
is Backup Media the name of the cd in the drive?  ls /media/ should come up empty if nothing is mounted in /media/

---

### Post by lvleph on 2010-05-31
Backup and Media are two different partitions mounted through fstab on startup.

---

### Post by muaythaimaster74 on 2010-05-31
what does mount -l tell you?

---

### Post by lvleph on 2010-05-31
**mount -l**
```
/dev/sda3 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdb1 on /media/Media type ext4 (rw) [Media]
/dev/sda1 on /home type ext4 (rw)
/dev/sda2 on /media/Backup type ext3 (rw) [Backup]
gvfs-fuse-daemon on /home/media/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=media)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```
Not there.

---

### Post by muaythaimaster74 on 2010-05-31
hmmm.. strange... that should have shown all mounted volumes and cd's...

what does ls -al /dev/cd* show?

---

### Post by lvleph on 2010-05-31
**ls -al /dev/cd***
```

lrwxrwxrwx 1 root root 3 2010-05-31 10:37 /dev/cdrom -> sr0
lrwxrwxrwx 1 root root 3 2010-05-31 10:37 /dev/cdrw -> sr0

```

---

### Post by muaythaimaster74 on 2010-05-31
at least we know your cdrom drive is detected...
ya could force it to use a specific location in fstab by adding something like this...
then on next boot it will use /media/cdrom for your device

/dev/sr0             /media/cdrom     udf,iso9660   ro,user,noauto,unhide   0      0[FONT=Verdana]

[/FONT]

---

### Post by lvleph on 2010-05-31
Using **sudo mount -a** I get no error and nothing is mounting at /media/cdrom. The cdrom is mounted though, because again it shows up on the desktop.

---

### Post by muaythaimaster74 on 2010-05-31
might just need to create the directory...
mkdir /media/cdrom
unmount from desktop...
then mount /dev/sr0 /media/cdrom

---

### Post by lvleph on 2010-05-31
I created the directory. If I hadn't I would have gotten an error.

Here is something

**sudo mount -t udf,iso9660 /dev/sr0 /media/cdrom/**
```

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

**dmesg | tail**
```

[91988.876512] end_request: I/O error, dev sr0, sector 2496
[91988.876539] UDF-fs: No anchor found
[91988.876543] UDF-fs: No partition found (1)
[91988.993605] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[91988.993617] sr 1:0:0:0: [sr0] Sense Key : Illegal Request [current] 
[91988.993629] Info fld=0x10, ILI
[91988.993633] sr 1:0:0:0: [sr0] Add. Sense: Illegal mode for this track
[91988.993647] sr 1:0:0:0: [sr0] CDB: Read(10): 28 00 00 00 00 10 00 00 01 00
[91988.993669] end_request: I/O error, dev sr0, sector 64
[91988.993722] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

---

### Post by muaythaimaster74 on 2010-05-31
what happens if you remove udf from the string and just specify iso9660?

---

### Post by lvleph on 2010-05-31
Exact same error.

EDIT:
Just tried a different cd and everything worked. So now I have to figure out why that other cd is not mounting in /media/cdrom, but still is showing up on the desktop.

---

### Post by muaythaimaster74 on 2010-05-31
When the cd comes up on the desktop are you actually able to access the contents of the cd?  The error you are receiving tends to indicate that the filesystem used on the cd can not be read.

---

### Post by WorMzy on 2010-05-31
Since it appears on your desktop, what happens when you double click it? Does it open a location in nautilus or give an error?

---

### Post by lvleph on 2010-05-31
Yes, I am able to see everything. It is quite strange.

---

### Post by WorMzy on 2010-05-31
What location does it open?

---

### Post by lvleph on 2010-05-31
I can double click it and see everything, but need to access it through terminal.

EDIT: The location is hard to figure out, but I right click on a file and check properties. The location is listed as cdda://sr0/

---

### Post by WorMzy on 2010-05-31
Oh wow, that's different.

Is this an audio CD?

---

### Post by lvleph on 2010-05-31
Yes, it is.

---

### Post by WorMzy on 2010-05-31
[http://superuser.com/questions/49358/ubuntu-9-04-ripping-cds-with-grip](http://superuser.com/questions/49358/ubuntu-9-04-ripping-cds-with-grip)

This SuperUser thread suggests that this is normal behaviour for audio disks; since there isn't actually any files, just tracks.

---

### Post by lvleph on 2010-05-31
Well, I guess I had two problems then. Thank you for you help.

---

### Post by Ginsu543 on 2010-05-31
Just to give you something to compare, on my machine it appears that sr0 is mounted in /dev. When I insert a CD, the volume is then mounted in /media which allows me to access it either in Nautilus or in Terminal.

---

