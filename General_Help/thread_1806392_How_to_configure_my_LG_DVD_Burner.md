---
title: "How to configure my LG DVD Burner"
date: 2011-07-17
forum: General Help
---

### Post by c.washington.h on 2011-07-17
I just installed Ubuntu on my newly built computer from a USB drive. I have tried to install a LG DVD burner but when I insert media the computer does not recognize my player. I am searching for help on configuring my drive so that I can use it.

---

### Post by bhinderm on 2011-07-17
Do you mean when you insert blank media into it, it is not detected by the player? Can you read other previously burned cds/dvds?

What do you see when you run "sudo dmesg|grep -i dvd" in the terminal? You should see something like:

root@bhinderm-lx:/var/log# sudo dmesg|grep -i dvd
[    2.072031] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray

---

### Post by bhinderm on 2011-07-17
Sorry for asking so many questions, but also, is it a USB drive or an internal PCI drive?

---

### Post by c.washington.h on 2011-07-17
It an internal PCI drive. Unfortunately I am out of town now so I won't be able to try that code on my computer till next weekend. And when I insert any kind of media it isn't recognized.

---

### Post by bhinderm on 2011-07-17
Ah I see, sorry I meant SATA not PCI. Please post back with the command once you are at your computer

---

### Post by c.washington.h on 2011-07-23
It is a SATA drive. Sorry for the confusion

---

### Post by c.washington.h on 2011-07-23
This popped up:
[    2.963636] ata1.00: ATAPI: HL-DT-ST DVDRAM GH22NS70, EX00, max UDMA/100

---

### Post by c.washington.h on 2011-07-31
That wasw the output when i entered what you gave me

---

