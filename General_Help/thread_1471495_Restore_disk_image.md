---
title: "Restore disk image"
date: 2010-05-03
forum: General Help
---

### Post by ez4u2sa67 on 2010-05-03
Hello,
I am having a problem finding a piece of software. I've searched a lot and still have not come up with an answer. My situation is as follows: I have an image file the I wish to restore to my USB flash drive but so far I've had no luck doing this. I was wondering if there was a program/command that could help me restore the disk image.

---

### Post by eschvoca on 2010-05-03
Hi,

If your image files is disk.img then do:

```
dd if=disk.img of=/dev/sdb2
```

Where sdb2 is your usb partition.  Warning: this will erase the partition!  To find out your USB partition, unplug and plug-in your usb drive while looking at 'dmesg'.  It should also appear in your "Places" menu.

Is that what you mean by 'image'?  How did you get the image file?

-E

---

### Post by ez4u2sa67 on 2010-05-03
> **eschvoca said:**
> 

Is that what you mean by 'image'?  How did you get the image file?

-E
Yes I did mean Image file.

---

### Post by ez4u2sa67 on 2010-05-03
```
theo@theo-laptop:~$ dd if='/home/theo/Downloads/IMAGE.img' of=/dev/sdc
dd: opening `/dev/sdc': Permission denied
```
Meh, I'm getting user denied but I am the admin.

---

### Post by pYrO1v1aniac on 2010-05-15
> **ez4u2sa67 said:**
> ```
theo@theo-laptop:~$ dd if='/home/theo/Downloads/IMAGE.img' of=/dev/sdc
dd: opening `/dev/sdc': Permission denied
```
Meh, I'm getting user denied but I am the admin.


Append sudo to the front of that command. Even if you are the admin, you still need to sudo, because you're in a multiuser system. Once you sudo it will ask for your password.

---

