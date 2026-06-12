---
title: "Easiest way of copying an entire HD - with hidden partitions and all"
date: 2011-10-25
forum: General Help
---

### Post by nrabett on 2011-10-25
So, I bought a new ASUS laptop which I would like to play around with. I intend to wipe the HD in order to reinstall Win 7 and Ubuntu in dual boot - without the hidden ASUS partitions etc, which have caused enough problems on previous ASUS machines.

At the same time, I would like to have access to the original contents of the HD - as it came from ASUS. I am aware that ASUS offers its own backup and restore solutions, but I would prefer to do this manually.

To the question: I intend to use my Natty Live USB in order to copy the HD - all partitions - to an Ext4 formatted HD connected with USB. Ideally, I would like to keep the backup as a .tar.gz-file - in order to keep the USB HD useable for other backup purposes. What is the easiest way of doing this, using the Live USB?

---

### Post by haqking on 2011-10-25
> **nrabett said:**
> So, I bought a new ASUS laptop which I would like to play around with. I intend to wipe the HD in order to reinstall Win 7 and Ubuntu in dual boot - without the hidden ASUS partitions etc, which have caused enough problems on previous ASUS machines.

At the same time, I would like to have access to the original contents of the HD - as it came from ASUS. I am aware that ASUS offers its own backup and restore solutions, but I would prefer to do this manually.

To the question: I intend to use my Natty Live USB in order to copy the HD - all partitions - to an Ext4 formatted HD connected with USB. Ideally, I would like to keep the backup as a .tar.gz-file - in order to keep the USB HD useable for other backup purposes. What is the easiest way of doing this, using the Live USB?


[www.clonezilla.org](www.clonezilla.org)

---

### Post by nrabett on 2011-10-25
I was not able to see that Clonezilla supports saving partitions or entire HD images as files (as opposed to (edit: saving them as) partitions).

I was thinking more in the lines of 

dd if=/dev/sda1 bs=4096 | tar -czvf > /media/USB_disk/Backup.tar.gz

Edit: Sorry, it appears that Clonezilla does what I want. Solved.

---

### Post by oldtimer7777 on 2011-10-25
Asus provides their paid customers with the ability to buy a restore disc for each laptop/notebook they sell. Toshiba does the same.  They are usually very inexpensive. Sometimes just the shipping and handling and you get a really nice silver pressed dvd with everything you would be wiping off your system.

> **nrabett said:**
> So, I bought a new ASUS laptop which I would like to play around with. I intend to wipe the HD in order to reinstall Win 7 and Ubuntu in dual boot - without the hidden ASUS partitions etc, which have caused enough problems on previous ASUS machines.

At the same time, I would like to have access to the original contents of the HD - as it came from ASUS. I am aware that ASUS offers its own backup and restore solutions, but I would prefer to do this manually.

To the question: I intend to use my Natty Live USB in order to copy the HD - all partitions - to an Ext4 formatted HD connected with USB. Ideally, I would like to keep the backup as a .tar.gz-file - in order to keep the USB HD useable for other backup purposes. What is the easiest way of doing this, using the Live USB?

---

### Post by haqking on 2011-10-25
> **nrabett said:**
> I was not able to see that Clonezilla supports saving partitions or entire HD images as files (as opposed to (edit: saving them as) partitions).

I was thinking more in the lines of 

dd if=/dev/sda1 bs=4096 | tar -czvf > /media/USB_disk/Backup.tar.gz

Edit: Sorry, it appears that Clonezilla does what I want. Solved.

yeah Clonezilla does everything you want, it has a lot of features during expert mode.

Good luck

---

