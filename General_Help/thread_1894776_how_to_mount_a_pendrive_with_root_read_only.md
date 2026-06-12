---
title: "how to mount a pendrive with root read only?"
date: 2011-12-13
forum: General Help
---

### Post by fbs777 on 2011-12-13
I need to make the root filesystem read only in an embeeded system, but i need to mount a pendrive sometimes and other partitions.

I think the problem is w/ /etc/mtab file, if this file cant be modified then partitions cant be mounted (only those in /etc/fstab)
And if i add the partitions of the pendrive and the second hd in the /etc/fstab than when the pendrive or the second hd are not conected the system dont boot

I tried to link the /etc/mtab to another partition but not work, maybe this file must be accessed before the partitions in /etc/fstab be mounted...

---

### Post by WorMzy on 2011-12-13
If the filesystem is read-only, then you can only mount other filesystems onto existing folders; so you can't mount using (most) file managers or udisks, because these create a new folder in /media for the filesystem to be mounted onto. I don't think that /etc/mtab being unwritable will cause too much of a problem, so long as /proc/self/mounts is writable (which it should be as it uses it's own special filesystem, separate to /)

---

### Post by fbs777 on 2011-12-13
> **WorMzy said:**
> If the filesystem is read-only, then you can only mount other filesystems onto existing folders; so you can't mount using (most) file managers or udisks, because these create a new folder in /media for the filesystem to be mounted onto. I don't think that /etc/mtab being unwritable will cause too much of a problem, so long as /proc/self/mounts is writable (which it should be as it uses it's own special filesystem, separate to /)

you mean the first /media/folder name or even the folders inside the pendrive (like /media/PEN/folderX)? Because all the folders in /media are already created, because i mount all the partitions by the LABEL parameter, so the main folders in /media are the same everytime.

---

### Post by WorMzy on 2011-12-13
> **fbs777 said:**
> you mean the first /media/folder name or even the folders inside the pendrive (like /media/PEN/folderX)? Because all the folders in /media are already created, because i mount all the partitions by the LABEL parameter, so the main folders in /media are the same everytime.

Just the /media/folder name. Everything inside /media/folder is irrelevant.

So when you've booted up into this read-only embedded system, can you mount other partitions by running

```
sudo mount /dev/disk/by-label/PEN /media/PEN
```

Assuming that that disk label and the media folder exist.

If not, what error do you get (if any).

---

### Post by fbs777 on 2011-12-24
ok, now the other partitions is mounting, but i cant write on them.

So if the root fs is read only all the other partitions will be too?

ex: /media/PEN/folder1/file1 will be read only just because its mounting on / ?

---

### Post by WorMzy on 2011-12-24
> **fbs777 said:**
> ok, now the other partitions is mounting, but i cant write on them.

So if the root fs is read only all the other partitions will be too?

No, the other filesystems are independent of the root filesystem. For example, say the root filesystem is /dev/sda1, and your documents are on a separate filesystem, /dev/sda2. You can still mount /dev/sda2 as a writable filesystem onto an existing folder on the root filesystem, for example, /home/fbs/Documents.

That'd mean that you can't add or edit any files that live on the root filesystem (e.g. /etc/fstab, /boot/grub/grub.cfg, etc.), but you can still edit files on the documents filesystem (e.g. /home/fbs/Documents/report.odt, /home/fbs/Documents/list.txt, etc.)

If the filesystem mounted on /media/PEN is read only, then all it's files will be read only.

---

