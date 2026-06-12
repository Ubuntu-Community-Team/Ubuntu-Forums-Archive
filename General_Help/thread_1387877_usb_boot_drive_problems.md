---
title: "usb boot drive problems"
date: 2010-01-22
forum: General Help
---

### Post by calwyn on 2010-01-22
I'm currently between computers (old one broke) and I'm using my parent's and some of my friends computer's. just before my computer broke i used the usb boot disk creator to make a persistent usb boot disk with ubuntu 9.10 on it and backed up some of my more important files. it works; it saves the changes to my documents and keeps new files i make. but it won't download audio and video codecs and it won't download programs from the add/remove program function. it can't find the codecs and says the programs are unavailable. i'm wondering if there is a way to download the codecs from a website on the internet as a file, like how windows has exe files. If not, is there any other way i can get the codecs?

---

### Post by C.S.Cameron on 2010-01-22
How much persistence do you have, Persistence is stored in a file named casper-rw, it's maximum size is 4GB on a FAT32 partition, 2GB on FAT16. This is not a lot of space by today's standards.
Given enough persistence space you should be able to install codecs ok. You can check System Monitor to see how much space you have left.
You can always create a persistence partition as large as your thumbdrive will allow. name it casper-rw and format it ext2, ext3, ext4 or reiserfs.
You can also do a full install to the thumbdrive using the "Install Ubuntu" option from the Live CD. I would recommend disabling,(unplugging), the internal hard drive first.

---

