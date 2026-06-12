---
title: "Azureus Problem."
date: 2006-01-28
forum: General Help
---

### Post by TheSource on 2006-01-28
I was downloading a bunch of torrents and part way through downloading Azureus spits out this error:

Error: /mnt/sda1/home/user/desktop/blahblah... (Read-only file system), open fails when processing fille blah.iso.

Anyone point me in the right direction?

---

### Post by drummer on 2006-01-28
Check the permissions/ownership of blah.iso ... something might have hiccoughed and messed that up somehow, not actually sure how though. And is that a removable drive or one you mounted yourself? If it was manually mounted, maybe you did it from a full root terminal and the ownership of the entire drive is 'root'. Just some ideas... that's all I can think that it could be atm.

---

### Post by TheSource on 2006-01-28
Yes its another partition that I mount. I tried mounting with sudo because I did mount it with root when this happened. But it still gives me the same error.

---

### Post by drummer on 2006-01-28
Check that the permissions of the ISO are correct and that it belongs to the user that you're logged in with. Or, failing that, give the file global permissions (chmod 777 file.iso) and see if that helps.

---

### Post by TheSource on 2006-01-28
I tried changing the folder to that and it spits this at me.

chmod: changing permissions of `Downloads/': Read-only file system

---

### Post by drummer on 2006-01-29
Even as root? that seems strange... not sure what's going on there, sorry.

---

### Post by TheSource on 2006-01-29
Yep. Thanks anyway.

user@ubuntu:/mnt/sda1/home/user/Desktop$ sudo chmod 777 Downloads/
Password:
chmod: changing permissions of `Downloads/': Read-only file system

---

### Post by ubuntujonez on 2006-01-29
dumb question:

is the filesystem mounted readonly? when I do:

```
$ mount
```

i get:

```
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sda1 on /mnt/sata/wd1 type ext3 (rw)
/dev/sdb1 on /mnt/sata/wd2 type ext3 (rw)
```

(rw) is read-write. you should see that. if not you should remount.

---

### Post by TheSource on 2006-01-29
Ya its read-write. :|

root@ubuntu:/# mount -t ext3 /dev/sda1 /mnt/sda1
root@ubuntu:/# mount
/dev/sda1 on /mnt/sda1 type ext3 (rw)

---

### Post by GTvulse on 2006-01-29
[QUOTE=TheSource]I was downloading a bunch of torrents and part way through downloading Azureus spits out this error:

Error: /mnt/sda1/home/user/desktop/blahblah... (Read-only file system), open fails when processing fille blah.iso.

Anyone point me in the right direction?[/QUOTE]
Hmm... An ext3 filesystem I see.. Try this:

1. Unmount the filesystem
2. Repair it:
```

fsck.ext3 -C 0 -c -D -f -v /dev/sda1
fsck.ext3 -C 0 -f -v /dev/sda1

```
3. Remount and test.

---

### Post by TheSource on 2006-01-29
[QUOTE=dradul]Hmm... An ext3 filesystem I see.. Try this:

1. Unmount the filesystem
2. Repair it:
```

fsck.ext3 -C 0 -c -D -f -v /dev/sda1
fsck.ext3 -C 0 -f -v /dev/sda1

```
3. Remount and test.[/QUOTE]

root@ubuntu:/# fsck.ext3 -C 0 -c -D -f -v /dev/sda1
e2fsck 1.38 (30-Jun-2005)
The filesystem size (according to the superblock) is 18777969 blocks
The physical size of the device is 17494777 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Error reading block 17498112 (Invalid argument) while reading inode and block bitmaps.  Ignore error<y>? no

fsck.ext3: Can't read an block bitmap while retrying to read bitmaps for /


Well I think it was like this before. This partition was another linux install that went bad. I re partitioned and installed on this partition /dev/sda4. I can still access the contents on the hard drive. Too bad I dont have enough space to copy over the files I want and format that partition.


Oh and its not a read only file system becuase I can delete stuff from it.

Edit: Well mabye that was only because I had a terminal open logged in as root.

Edit2: Nevermind cant remove something else as root on that partition. Damn this is wierd.

---

### Post by TheSource on 2006-01-30
Anyone

---

### Post by Chris Tucker on 2006-01-30
if its a reoccurance of a previous problem... probably a bad drive. its like painting over a rust spot on a car without cleaning it and removing the rust.. it'll be out of sight for a little while then it'll show through again.

---

### Post by GTvulse on 2006-01-30
[QUOTE=Chris Tucker]if its a reoccurance of a previous problem... probably a bad drive. its like painting over a rust spot on a car without cleaning it and removing the rust.. it'll be out of sight for a little while then it'll show through again.[/QUOTE]
Yup. or a bad cable/bad connection. SATA drives are particularly sensitve to cabling problems so I would try to find a shielded SATA cable to replace the one you are using now as a first step, if you bought the drive in the last two years or so; it can be an already dying disk if older.

---

### Post by TheSource on 2006-01-30
I think the fsck errors are from when I repartitioned with PartitionMagic. Both the drives mount fine and I can read from them just fine.

---

### Post by GTvulse on 2006-01-30
[QUOTE=TheSource]I think the fsck errors are from when I repartitioned with PartitionMagic. Both the drives mount fine and I can read from them just fine.[/QUOTE]
Hmm... Partition Magic. What an overrated peice of $·%$·%. The error messages you get suggest that the geometry information in the hard drive bitmap sector (that's a sector that comes **after** the MBR and the partition table), contains wrong information about the disk size. There used to be versions of Norton Utilities that could repair such problem for you, but that was before it was bought by Symantec (read: in the stone age of computing).

fdisk could help you repair (or destroy :-)) your disk. Boot from a rescue/live cd, run fdisk on your drive, use the command to verify the partition table (it should ask permission to repair the damage), write the partition to disk if fdisk repaired it and boot up to your disk again. Of course, doing this with a data containing important files with no external backup is like walking the stringwire with no safety net, 50m above the ground :-).

---

