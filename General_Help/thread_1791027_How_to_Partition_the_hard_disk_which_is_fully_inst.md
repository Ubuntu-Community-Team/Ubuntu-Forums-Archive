---
title: "How to Partition the hard disk which is fully installed with ubuntu 11.04?"
date: 2011-06-26
forum: General Help
---

### Post by Harmanjit on 2011-06-26
I have about 298 GB of hard disk fully installed with ubuntu 11.04. I want to partition the hard disk to install windows 7 (mainly to use some devices/softwares which i am not able to use on ubuntu like a i-ball pen tablet).

Kindly help me out. I tried GParted but wasn't successful. 

Regards,
Harman

---

### Post by jerrrys on 2011-06-26
[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-resize-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-resize-partition)

this operation will probably take several hours.

---

### Post by Harmanjit on 2011-06-26
Thanks, going through the document now...

---

### Post by Harmanjit on 2011-06-26
Hi,

I read the document & burned GParted live on the CD. Now i can't figure out how to unmount the mounted partitions! Please help. How to execute from now on. I am a newbie, so try to explain as simply as possible.

Regards,
Harman

---

### Post by Harmanjit on 2011-06-26
Hi,

Please, this is urgent! Some one please help me out! How can i boot this cd??

Harman

---

### Post by jerrrys on 2011-06-26
just how much reading did you do?  to unmount

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-unmount-partition](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C#gparted-unmount-partition)

---

### Post by Harmanjit on 2011-06-26
Actually i am stuck after downloading the GParted live & then burning it on CD. I am not able to boot it, that's where i am stuck. How to proceed further from here?

---

### Post by jerrrys on 2011-06-26
its a live cd.  just should be able to stick it in the drive and reboot and it should work.  if not, you can use your ubuntu live cd, it has gparted on it.  system>admin>gparted

---

### Post by Harmanjit on 2011-06-26
Wasn't successful. Anyway thanks for your help.

---

### Post by baz.g on 2011-06-26
> **Harmanjit said:**
> Wasn't successful. Anyway thanks for your help.

if it did not boot from the live cd then you may need to check your bios settings to see the boot device order.

this varies from machine to machine but when you first switch the pc on it should show some options to press f keys to enter bios or change boot device order.

these are usually either f10, f11, f12 or del but it really does depend on bios version and motherboard manufacturer.

once you can actually see the order of boot devices, change it so that your cdrom is the first in the list (dont worry, for future when there is no cd it will just go on to the next device which should be your hard drive)

---

