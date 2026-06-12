---
title: "Automount USB stick as root"
date: 2011-09-28
forum: General Help
---

### Post by bogdanbiv on 2011-09-28
During installing Kubuntu 11.04 I left my usb stick in the PC and now it automagically mounts when I plugit in, but the trouble is it does not contain write rights for the current desktop user.

Other sticks mount just fine (/dev/sdd1), this one does not (/dev/sdc1).

```
$ mount
[..]
/dev/sdc1 on /media/bbbebdd3-40f3-4709-b954-8f8deca70baf type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sdd1 on /media/CORSAIR type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec)
```

I know I can always put a line in /etc/fstab for this specific UID, in fact I'm testing this now, but it seems barbaric. Any other solutions?

```
cat /etc/fstab
[...]
UUID=bbbebdd3-40f3-4709-b954-8f8deca70baf /media/adata    ext3    defaults        0       0  rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec
```

UPDATE: Also it's harder than I expected to find the right params for a fstab entry, since the syntax differs from what you get when doing "mount /dev/disk /mount-point". I've corrected a few errors, but I still expect to have a few errors on this entry.

---

### Post by zitch on 2011-09-29
From your mount output, /dev/sdd1 is formatted as a FAT drive (vfat), which has no permissions to speak of, so it allows anybody to read and write to it.  On the other hand, /dev/sdc1 is formatted as ext3, which will have a similar permission system as your main file system.

Try running the following to allow normal user read-write on the drive with it mounted:

```
sudo chmod 777 /media/bbbebdd3-40f3-4709-b954-8f8deca70baf/
```

And see if a standard account can write to it.

---

### Post by bogdanbiv on 2011-10-02
You were right, after applying 777 to the whole directory tree, it works like a charm.
Oh, and, for future reference, automounting the disk _does_ work still.

One more thing, where are the rules for automounting disks? I knew it had something to do with hal / devicekit, but I didn't know exactly where to look for it.

Here, you can see there is no /etc/devicekit:
$ sudo ls /etc/dev*
ls: cannot access /etc/dev*: No such file or directory

---

