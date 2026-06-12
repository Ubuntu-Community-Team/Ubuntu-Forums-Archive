---
title: "I can't see my HDD under ubuntu ... I need help"
date: 2010-07-24
forum: General Help
---

### Post by q8.legend on 2010-07-24
I'm new to ubuntu, and I have problem with the Hdd ... I have one Hdd that is not shown and I can't see it under ubuntu... all the other Hdd that I have, they works perfectly but only one thats it's not working. althought that its shown under the disk utilty but I can't mount it ... This is the picture from Disk utility...

Note:

the Hdd is working great under windows, & the Hdd only have video files and data (not system files)...

Thanks alot...

[IMG]http://img269.imageshack.us/img269/7830/screenshot10tbharddiska.png[/IMG]

---

### Post by CharlesA on 2010-07-24
If you run this:

```
sudo fdisk -l
```

Is the drive listed?

---

### Post by q8.legend on 2010-07-24
> **CharlesA said:**
> If you run this:

```
sudo fdisk -l
```Is the drive listed?


Yes..

[IMG]http://img52.imageshack.us/img52/3448/screenshotq8legendq8.png[/IMG]

---

### Post by CharlesA on 2010-07-24
What kind of file system is shown on that drive when it's shown in Windows?

I'm guessing NTFS since it's a 1TB drive (and it shows as NTFS in the screenshot in the OP)

It looks like Ubuntu doesn't know what file system that drive is using.

Check [here]("http://www.arsgeek.com/2006/11/01/ubuntu-tricks-how-to-mount-your-windows-partition-and-make-it-readwritable-with-ntfs-3g/") to see if you can mount it manually.

---

### Post by q8.legend on 2010-07-25
I solved it by using"NTFS configuration tool" and mount the HDD... I faced problem after doing that, I couldn't enter my ubuntu after that. because it said mount error. So, I fixed that by editing the HDD in fstab(comment it)...

Then it works perfectly ;)

Thanks alot

---

