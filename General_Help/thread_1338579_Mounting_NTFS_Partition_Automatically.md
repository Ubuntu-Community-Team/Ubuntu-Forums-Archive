---
title: "Mounting NTFS Partition Automatically"
date: 2009-11-26
forum: General Help
---

### Post by example6 on 2009-11-26
I've been trying for many days to get my Jaunty installation to automatically mount this NTFS partition I have at start up.

When I put the following line in /etc/fstab:
```
/dev/sdc1    /media/STORAGE    ntfs-3g    user        0    0
```

It not only does not auto-mount, I cannot manually mount the drive without using** sudo mount**

When I try to mount from Places -> Removable Media -> STORAGE, it gave the following error:

"Unpriviliged user cannot mount NTFS block devices using the external FUSE library. Either mount the volume as root, or rebuilt NTFS-3G with integrated FUSE support and make it setuip root. Please see more information at http://ntfs-3g.org/support.html#unprivileged"

I then followed the link, and the instructions contained within. Now, instead of getting that error, I don't get any error at all. When I click the little details pointer, it points downward and nothing is shown.

I can mount just fine from wherever when the line is commented out of /etc/fstab, but I would really like to get this thing auto-mounting.

Any help would be greatly appreciated! Thanks!

---

### Post by sisco311 on 2009-11-26
Use ntfs-config (GUI) to create the fstab enrty:

[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by akakingess on 2009-11-26
Here is another link that I found on these forums [http://ubuntuforums.org/showthread.php?t=785263&highlight=automounting+NTFS](http://ubuntuforums.org/showthread.php?t=785263&highlight=automounting+NTFS) , hope this helps or the previous post helps you out.

---

### Post by example6 on 2009-11-26
I installed ntfs-config

But when I run it, It only has two checkboxes.

The first one (Blacked out, unable to be checked) is "Enable write support for internal device"

The other, which I checked, is "Enable write support for external device"

It removed the entire /dev/sdc1 line from my fstab.

At no point did it detect my partition or ask me where to mount it...

So.. back at square one?

---

### Post by sisco311 on 2009-11-26
Is the partition mounted?
unmount it:
```
sudo umount /dev/sdc1
```

EDIT:
it's on an external hard disk?

---

