---
title: "Unable to mount volumes after applying updates"
date: 2011-06-28
forum: General Help
---

### Post by kevinhobson2000 on 2011-06-28
Hi All,

After applying Ubuntu updates i am now unable to mount volumes it tells me that i am denied.

I have checked my user permissions and i am allowed to mount.

I have also downgraded MountAll to no avail.

Any help much appreciated.

Cheers

Kev

---

### Post by kevinhobson2000 on 2011-06-28
Update:

I have booted into vista and it sees the partitions fine so it isnt a partition damaged issue.

GParted show the partitions as a unknown format.

Cheers

Kev

---

### Post by varunendra on 2011-06-29
So it is an ntfs partition.... Try **chkdsk /x /f** on that partition from vista, then retry from ubuntu. Also try accessing from a live cd (after performing chkdsk).

---

### Post by kevinhobson2000 on 2011-07-26
Hi,

I tried this and i am still not able to mount the volumes.

Cheers

Kev

---

### Post by kevinhobson2000 on 2011-07-26
Hi,

If i boot from the disk i can access the drives.

Anyone any ideas?

Thanks

Kev

---

### Post by kevinhobson2000 on 2011-07-26
I think its just the version of gparted.

I dont think there is anything wrong with the partitions seems the permssions have been screwed up some how.

Even though my account has permission to mount media and mounted fine before the update.


Is there a way to roll it back similar to system restore in windows?

Thanks

Kev

---

### Post by varunendra on 2011-07-27
> **kevinhobson2000 said:**
> I tried this and i am still not able to mount the volumes.
Do you mean you tried chkdsk in Vista? Did it run smooth returning no errors or corrections?

> **kevinhobson2000 said:**
> 
If i boot from the disk i can access the drives.Which 'disk'? Do you mean the Live CD? Or the Hard disk (booting in Vista)?


> **kevinhobson2000 said:**
> I think its just the version of gparted.
There may be compatibility issue between Gparted and Vista partitions, but it is highly unlikely, especially if your version of GParted is new.

Most often, when 'any' partition manager shows a partition as 'Unknown', it is a partition table error / incompatibility. In this case, you can access the contents from within the OS which created it, but manipulating it using a 3rd party partition manager (like gparted in your case) may cause severe damage to file system.

As for 'rolling back like Sys. Restore in Windows', I don't think there's anything similar in Ubuntu. You can always boot an older kernel (selecting from Grub menu) if it is not uninstalled manually. But your problem is not kernel related as much as I can see.

Please post back the contents of **/etc/fstab** file, and output of:
```
sudo fdisk -l
```

Also, if you enter this command in terminal:
```
sudo mount -a
```
do you get any error messages?

---

