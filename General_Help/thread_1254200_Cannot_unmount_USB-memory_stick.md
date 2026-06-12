---
title: "Cannot unmount USB-memory stick"
date: 2009-08-31
forum: General Help
---

### Post by wolfv6 on 2009-08-31
I am running Ubuntu 9.04 and the USB-memory stick labeled "STORE'N'GO" which is 1G of FAT32. From Nautilus 2.26.2 Properties, the memory stick has 0 bytes used and 0 bytes free.

So here is the problem; umount from the terminal gets an error:
```
wolf-PC:/media> umount /STORENGO
umount: /STORENGO is not mounted (according to mtab)
wolf-PC:/media> umount /STORE'N'GO
umount: /STORENGO is not mounted (according to mtab)
wolf-PC:/media> umount "/STORE'N'GO"
umount: /STORE'N'GO is not mounted (according to mtab)
```There is a README.txt file on STORE'N'GO that I can open, edit, and save.

This line is in /etc/mtab:
```
/dev/sdb1 /media/STORE'N'GO vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```How can I unmount the STORE'N'GO USB-memory stick?

Thank you.

---

### Post by sparky-steve on 2009-08-31
> This line is in /etc/mtab:
```
/dev/sdb1 /media/STORE'N'GO vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```How can I unmount the STORE'N'GO USB-memory stick?

Thank you.try

```
umount /media/STORE'N'GO
```But you may have to escape the quotes (too early for my brain....)

```
umount /media/STORE\'N\'GO
```You can see what is mounted, and where using:

```
mount
```Hope that helps
SS

---

### Post by wirate on 2009-08-31
in your /media folder, an icon might be appearing for the usb drive. try right click and unmount volume

dont know for sure :)

---

### Post by P4man on 2009-08-31
in nautilus there is a little eject icon next to the drive. clicking that does the same. doesnt always have to be so complicated ;)

[img]http://2.bp.blogspot.com/_hoL9qH83NDM/SRCUBfDOeRI/AAAAAAAAAR0/avTib2rSlnw/s320/Nautilus+-+Places+-+Eject+Icons.png[/img]

---

### Post by wolfv6 on 2009-08-31
P4man,
nautilus > unmount worked.

From terminal, umount worked from root, but not from media.  Interesting; maybe a problem concatenating path with double quotes.

```
wolf-PC:/media> umount "STORE'N'GO"
/sbin/umount.hal: STORE'N'GO is not recognized by hal
wolf-PC:/media> umount "/media/STORE'N'GO"
wolf-PC:/media> ls
cdrom  cdrom0  floppy  floppy0    sda1
```Thank you all for your suggestions :)

---

