---
title: "how to rename an ext3 ext usb hard disk?"
date: 2010-04-28
forum: General Help
---

### Post by abhilashm86 on 2010-04-28
i've formatted my 320GB to ext3 using mkfs.ext3, all is working well, how do i rename it and should i change ownership of usb to root?

How do i open this usb external disk in windows 7?

this is my usb extrenal disk, see the name 899d6c97-1ae8-4805-8352-c1c475f2669e, how do i change that??

```
abhilash@abhilash:/media$ ls -l
total 8
drwxr-xr-x 4 root root 4096 2010-04-27 20:16 899d6c97-1ae8-4805-8352-c1c475f2669e
lrwxrwxrwx 1 root root    7 2010-04-27 21:41 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2010-04-27 21:41 floppy0
abhilash@abhilash:/media$ cd 899d6c97-1ae8-4805-8352-c1c475f2669e/
abhilash@abhilash:/media/899d6c97-1ae8-4805-8352-c1c475f2669e$ ls -l
total 20
drwxr-xr-x 10 abhilash abhilash  4096 2010-04-27 21:26 abhi_folder
drwx------  2 root     root     16384 2010-04-27 20:13 lost+found
abhilash@abhilash:/media/899d6c97-1ae8-4805-8352-c1c475f2669e$ 

```

---

### Post by mikewhatever on 2010-04-28
For renaming, try Places->Computer, right click the disk in question, select 'Rename', and ... rename it.

---

### Post by abhilashm86 on 2010-04-28
> **mikewhatever said:**
> For renaming, try Places->Computer, right click the disk in question, select 'Rename', and ... rename it.

Its not renaming when i do above, error is "operation not supported in backend".
Any solution from terminal to rename it?

---

### Post by searchfgold6789 on 2010-04-28
Make sure you are doing this as root.
Try doing
```
su
```or
```
sudo
```in terminal. Then I think it should do everything within that session as root.
And the extended file system is NOT available for windows 7 although it is available [for XP]("http://sourceforge.net/projects/ext2fsd/").
Why don't you see what
```
sudo palimpsest
```
does? usually typing a program's name in the terminal will give you some instructions on how to use it from there.

---

### Post by beren.olvar on 2010-04-28
looks like udev is mounting it using its id. Look at this page [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html) to see how to write a better rule for your device.

AFAIK windows can't read ext3 drives natively, but I think there are windows applications for that. Maybe someone else with more experience with that, or google, can help you.

---

### Post by mikewhatever on 2010-04-28
> **abhilashm86 said:**
> Its not renaming when i do above, error is "operation not supported in backend".
Any solution from terminal to rename it?

Try unmounting first. You can also try to label it with Gparted. Usually when labeled, the name of the partition corresponds to the label.

---

### Post by Morbius1 on 2010-04-28
Is this what you're looking for?
[COLOR=Blue]
EDIT: you need to unmount the mountpoint first[/COLOR]
```
sudo umount /mountpoint
sudo e2label /dev/sdxy whatever_label_you_want
```[COLOR=Blue]*Change sdxy to whatever your correct device is.*[/COLOR]

I think the usb automounter defaults to the partition label. You must not have one so it's going to use the UUID number.

---

