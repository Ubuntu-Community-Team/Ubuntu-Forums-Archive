---
title: "fsck is called on every startup"
date: 2010-05-09
forum: General Help
---

### Post by AboSamoor on 2010-05-09
I am using bootchart to investigate the slow booting of ubuntu 10.04 and I found that fsck process is called every time in the booting for around 5 seconds even the screen does not show any hard disk checking, is that normal ?

---

### Post by dcstar on 2010-05-10
> **AboSamoor said:**
> I am using bootchart to investigate the slow booting of ubuntu 10.04 and I found that fsck process is called every time in the booting for around 5 seconds even the screen does not show any hard disk checking, is that normal ?

Yes, each partition in /etc/fstab marked with anything other than a "0" in the appropriate field will be passed to fsck to be checked at bootup. fsck will check the settings on all EXT2/3/4 partitions to see if the date/count will trigger a full fsck and will do whatever it is supposed to do for other filesystem types.

---

### Post by rnerwein on 2010-05-10
> **AboSamoor said:**
> I am using bootchart to investigate the slow booting of ubuntu 10.04 and I found that fsck process is called every time in the booting for around 5 seconds even the screen does not show any hard disk checking, is that normal ?

hi
i guess i got the same problem before. it wasn't the /etc/fstab entry but:
the values of[COLOR=Blue] Mount coun[/COLOR]t and[COLOR=Blue] Maximum mount count[/COLOR] was totaly confused.
those values tell the system when a fsck has to run. see: man tune2fs 
you can manupulate those values by using the -c and -C option. e.g.
sudo tune2fs -l /dev/sdXY  shows you the settings.
and
sudo tune2fs -c 1 /dev/sdXY will set the Mount count to 1.
my thread was: filesystem ext2,ex3,ext4

ciao

---

### Post by lavinog on 2010-05-10
Also make sure you don't have a file named forcefsck in your root folder.
There is a bug where mountall doesn't remove this file after forcing a diskcheck.

---

### Post by AboSamoor on 2010-05-18
Changing all the values in fstab to 0 solved the problem, but I am wondering if this will make side effects ?!

---

### Post by CharlesA on 2010-05-18
> **AboSamoor said:**
> Changing all the values in fstab to 0 solved the problem, but I am wondering if this will make side effects ?!

Outside of not checking the disk every x mounts, no.

You should check it every so often to ensure the file system isn't corrupted.

---

