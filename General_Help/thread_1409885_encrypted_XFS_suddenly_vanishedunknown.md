---
title: "encrypted XFS suddenly vanished/unknown"
date: 2010-02-18
forum: General Help
---

### Post by give.away on 2010-02-18
I formated and encrypted a partition as XFS (via Disk Utilities), but suddenly the partition is not recognized anymore.

I tried to mount it with:
```
sudo mount -t xfs /dev/sda4 /media/disk
```
But I got following error:
```
mount: wrong fs type, bad option, bad superblock on /dev/sda4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
I then did:
```
dmesg | tail
```
And got:
```
[  255.413203] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[  255.418589] SGI XFS Quota Management subsystem
[  255.438428] XFS: bad magic number
[  255.438435] XFS: SB validate failed
[  585.721043] XFS: bad magic number
[  585.721050] XFS: SB validate failed
```

Now I'm stuck. I assume it does not work because of the encryption - but I usually managed this partition via Disk Utilities, but now that the partition is not recognized anymore, I have to mount it manually, which I obviously don't know how ;)

Please help!
Thanks!

---

### Post by funnyav on 2010-03-13
I get the same thing! I'm running xfs_repair on it now.
My main problem is that i have ubuntu installed on a external usb hdd and after a system update it doesn't get past grub loading screen... I can sometimes still boot via my internal drive's grub [but then THAT crashes if the USB is not plugged in at boot time].

Bleh. Will say if anything changed :)

---

