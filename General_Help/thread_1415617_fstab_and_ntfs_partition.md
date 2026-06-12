---
title: "fstab and ntfs partition"
date: 2010-02-25
forum: General Help
---

### Post by Prust on 2010-02-25
Hi,
I saw/read tutorials and solved forum entries about "editing fstab", "mounting ntfs partition" etc. as many as i could. I used every possibility ((of course not all of it)) for mounting my second hdd ntfs partition. My problems is i cant make it fully writable.

I can create folders in partition but i cant share them or change their ownership
And here my fstab and fdisk list.
About my hdds, on first hdd i have win installation as 3 partition  and on second hdd, my lovely ubuntu and ntfs partition to use as shared in my LAN

```
harun@ubuntu03:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=5b2e2e5a-0d8d-45e6-a0ea-0503ed3e2741 /               ext3    errors=remount-ro 0       1
/dev/sdb1       none            swap    sw              0       0
/dev/sdb3 	/media/hdd2 	ntfs 	defaults 	0 	0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```
harun@ubuntu03:/$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50a750a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        6378    51123200    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            6378       16905    84558536    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          27      216846   82  Linux swap / Solaris
/dev/sdb2              28        7322    58597087+   5  Extended
/dev/sdb3            7323      121601   917946067+   7  HPFS/NTFS
/dev/sdb5              28        7322    58597056   83  Linux

```

---

### Post by amsterdamharu on 2010-02-25
Should be something like this?

```
/dev/sdb3     /media/hdd2     ntfs    user,auto,noexec,rw    0    0
```I took out the execute (noexec), it will auto mount and user can unmount remount (user,auto) and user can read write (rw).

If you want to mount the drive when you click on it in nautilus then leave out the line in the fstab.

---

### Post by Prust on 2010-02-25
> **amsterdamharu said:**
> Should be something like this?

```
/dev/sdb3     /media/hdd2     ntfs    user,auto,noexec,rw    0    0
```I took out the execute (noexec), it will auto mount and user can unmount remount (user,auto) and user can read write (rw).



Actually it worked to mount to partition but not for the ownership.
I've tried chown commands but cant change a thing, even i tried in nautilus (i've opened from terminal as "sudo nautilus"), on file properties popup menu, when i changed from root to harun, it was suddenly changed back to root again.

in any case i send my chown command...
```

sudo chown harun /media/hdd2/shared
sudo chown harun:users /media/hdd2/shared

```

maybe *gid* and *umask* entries work in fstab, but i couldn't figure it out yet:neutral:

---

### Post by Morbius1 on 2010-02-25
If your using the nautilus method to share the partition then you need something like this:

```
/dev/sdb3     /media/hdd2      ntfs    defaults,nls=utf8,umask=000,uid=1000   0    0
```uid=1000 will make you the owner
umask=000 will make it accessable to everyone
( The umask entry is redundant really because it's in the defaults but I like to keep it there just so I remember how I set permissions )

To make sure that you are uid=1000, go to a terminal and type: [B]id

[/B]BTW: you can't chown or chmod a windows filesystem.

---

### Post by Prust on 2010-02-26
> **Morbius1 said:**
> If your using the nautilus method to share the partition then you need something like this:

```
/dev/sdb3     /media/hdd2      ntfs    defaults,nls=utf8,umask=000,uid=1000   0    0
```uid=1000 will make you the owner
umask=000 will make it accessable to everyone
( The umask entry is redundant really because it's in the defaults but I like to keep it there just so I remember how I set permissions )

To make sure that you are uid=1000, go to a terminal and type: [B]id

[/B]BTW: you can't chown or chmod a windows filesystem.


thanks to both of you, rest of it are "samba" settings as well. and thanks for the tip *Morbius1*, i've skipped that detail some how #-o

---

