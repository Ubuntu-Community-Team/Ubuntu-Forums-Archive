---
title: "Help removing windows from grub loader"
date: 2009-11-08
forum: General Help
---

### Post by ratedrampage on 2009-11-08
Ok everyone ive been using ubuntu for the past 3 weeks and wanted to remove windows. I used a gparter (or whatever) live CD to remove the windows partition and expand the ubuntu one. It worked. I now have 235GB of ubuntu goodness. Now I want to remove the windows option on my grub loader. I've read a good ammount of posts regarding this matter and couldnt understand. Could someone please point out a simple way of doing this? I am using Karmic Koala if that matters. I noticed my hard drive is not hd1 or something but sda1. Does that make a difference?

This is what i got from fdisk.

Thanks in advance.

[B]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9dfb9df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       30278   243208003+  83  Linux
/dev/sda3           30279       30401      987997+   5  Extended
/dev/sda5           30280       30401      979965   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x609e642b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
[/B]

---

### Post by Primefalcon on 2009-11-08
> **ratedrampage said:**
> Ok everyone ive been using ubuntu for the past 3 weeks and wanted to remove windows. I used a gparter (or whatever) live CD to remove the windows partition and expand the ubuntu one. It worked. I now have 235GB of ubuntu goodness. Now I want to remove the windows option on my grub loader. I've read a good ammount of posts regarding this matter and couldnt understand. Could someone please point out a simple way of doing this? I am using Karmic Koala if that matters. I noticed my hard drive is not hd1 or something but sda1. Does that make a difference?

This is what i got from fdisk.

Thanks in advance.

[B]Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb9dfb9df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               1       30278   243208003+  83  Linux
/dev/sda3           30279       30401      987997+   5  Extended
/dev/sda5           30280       30401      979965   82  Linux swap / Solaris

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x609e642b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS
[/B]

ig your using grub 1 rather than the new grub in karmic

just go to  run this command

```
gksudo gedit /boot/grub/menu.lst
```

and remove the entry block for windows from there

---

### Post by ratedrampage on 2009-11-09
Its karmic. When I went to edit there was a blank file that did not exist.

---

### Post by mikewhatever on 2009-11-09
The best way I found so far is from grub2 guide.
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

```
GRUB_DISABLE_OS_PROBER=true

    * Enables/disables the os-prober check of other partitions for operating systems, including Windows, Linux, OSX and Hurd.
```

It's not ideal, especially with multiple OSs, but should work with just two.

---

### Post by ratedrampage on 2009-11-10
Thanks a bunch mate. It worked!

[offtopic]

How can I post a how to and where?
I want to help people install JDownloader :D

---

