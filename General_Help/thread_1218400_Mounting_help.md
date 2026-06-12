---
title: "Mounting help?"
date: 2009-07-20
forum: General Help
---

### Post by conradin on 2009-07-20
HI all, 
I am trying to mount a SCSI hard Drive. The Device shows up in Gparted as /dev/sdc1  with an xfs file system. 
```
 
sudo mount /dev/sdc1 /media/SCSI2

```

I also included an entry in /etc/fstab:
 
```

/dev/sdc1        /media/SCSI2   auto    rw,user,noauto,exec,utf8 0       0

```

But I keep getting the error  mount: Function not implemented
the device shows up in the "places" folder but when I click on it, says "invalid mount option when attempting to mount this volume"

I am not sure what any of this means, can someone give me the newbie version and help me mount this file system please?

---

### Post by merlinus on 2009-07-20
Try this:

```
/dev/sdc1 /media/SCSI2 xfs auto,rw,user,exec,utf8 0 0
```

---

### Post by conradin on 2009-07-20
> **merlinus said:**
> Try this:

```
/dev/sdc1 /media/SCSI2 xfs auto,rw,user,exec,utf8 0 0
```

Ok, I added the code above to /etc/fstab but Im still looking at the same error messages.  I have of course also tried:
```

sudo mount -t xfs  /dev/sdc1 /media/SCSI2

```

to no avail. Any other suggestions?

---

### Post by merlinus on 2009-07-20
I am not familiar with xfs, but perhaps there is a problem with that???

Also, just to be sure, you did create the mountpoint?

And you might try jfs instead of xfs.

---

### Post by conradin on 2009-07-20
> **merlinus said:**
> I am not familiar with xfs, but perhaps there is a problem with that???

Also, just to be sure, you did create the mountpoint?

And you might try jfs instead of xfs.

Yes, I created the mount point. when I tried jfs I got: 
```

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
 xfs is an old file system for IRIX. 
Does it matter the disk Flag is set to --root?

---

### Post by merlinus on 2009-07-20
Can you change the disk flag to something else and try it?  Shouldn't hurt...

But so far everything you have done is according to the book, AFAIK.

---

### Post by conradin on 2009-07-20
> **merlinus said:**
> Can you change the disk flag to something else and try it?  Shouldn't hurt...

But so far everything you have done is according to the book, AFAIK.

I changed the Disk Flag (to --) and its still giving me the same darn messages. 
I'm so lost for what to do with this.

---

### Post by merlinus on 2009-07-20
If the filesystem is sound, perhaps it is the scsi drive and ubuntu.  You might try googling to see if you can find anything.

Another idea is to unmount it, or comment out the entry in /etc/fstab, and then try to mount it manually.  If there are error messages, perhaps they will be more informative.

---

### Post by conradin on 2009-07-21
> **merlinus said:**
> If the filesystem is sound, perhaps it is the scsi drive and ubuntu.  You might try googling to see if you can find anything.

Another idea is to unmount it, or comment out the entry in /etc/fstab, and then try to mount it manually.  If there are error messages, perhaps they will be more informative.

Im thinking the SCSI Card is fine since I had a SCSI Drive with the EFS (file system) and that mounted with pretty much no hassle. (after writing an entry into etc/fstab)
 
I tried manual mounting as well that was fail. I tried restoring the file system with XFS_repair -v and remounting it. Still nothing. 

I also downloaded the XFS utilities available from the symantic package manager.  The only other thing I was thinking was to try using an older linux kernel and hope it has better support for the xfs file system.

Currently Im doing DD_Restore to create an image file on a newer IDE hard Drive. I have Little hope that this will work. Im still wide open for any suggestions.

---

### Post by conradin on 2009-07-21
Ok, This might not belong here, but I used 
```

sudo dd_rescue /dev/sdc1 '/media/disk-1/Mirage/backup.img'

```
I tried to mount the image file using 
```

sudo mount -t xfs '/media/disk-1/Mirage/backup.img'  /media/temp -o loop

```

but still got:
mount: Function not implemented

---

### Post by conradin on 2009-07-21
I finally solved my mounting issue for the XFS file system by downloading a copy of warty warthog and installing it to another computer. Then I simply installed my SCSI hardware and mounted it by modifying /etc/fstab, and creating a mount point. 
 
Thank you merlinus for all you assistance!!

---

