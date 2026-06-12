---
title: "moved to openbox, really pleasent but where did all my mounts go."
date: 2009-07-24
forum: General Help
---

### Post by ThaDoctor99 on 2009-07-24
Hmm. This is irritating.
I know this is a rather lame question.

Well I finally got to move from gnome to openbox, but now I can't seem to mount my usb harddrive - I would really hate to **** in the /etc/fstab unless that is terribly necessary - and not really without a guide to help.
Well my problem is I can't really seem to find where my usb hard disk is pointing in /dev/ so I can't really mount got some program installed to list all the usb's in some directory. Yeah it shows them in mount, there is only one now though, well it is empty and my hard disk (the external) one is suddenly not empty keeping some different files on there.

Would somebody please help me - hope it gives good karma ;0)

Greetings Denmark.

---

### Post by jerome1232 on 2009-07-24
With the external plugged in what's the output of:

```
sudo fdisk -l
```

---

### Post by ThaDoctor99 on 2009-07-24
Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f800000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19742   158577583+  83  Linux
/dev/sda2           19743       19929     1502077+   5  Extended
/dev/sda5           19743       19929     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   c  W95 FAT32 (LBA)

---

### Post by ThaDoctor99 on 2009-07-24
Well now it just worked. Well didn't know that fdisk command there. 
Thanks.
And I didn't have to change fstab. :-)

---

