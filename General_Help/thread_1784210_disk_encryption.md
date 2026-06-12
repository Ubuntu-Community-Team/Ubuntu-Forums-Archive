---
title: "disk encryption"
date: 2011-06-16
forum: General Help
---

### Post by kvcckid on 2011-06-16
Just wondering why when I format a usb dongle for FAT using ubuntu's disk utility, I believe it does a fat32 format, and when using encryption my windows machine and my iMac can't read it?
Shouldn't it just mount and request the key/passphrase?
Thanks in advance

---

### Post by kvcckid on 2011-06-16
sorry for the double post but my question is about encryption independent of operating system.
Any way to do this on ubuntu?

---

### Post by Synoc on 2011-06-16
I COULD be wrong on all of this, but FAT is FAT 16 and hasn't been seriously considered for anything since 90s. fat 32 is superior in every way. I am not even sure if you can format a USB key in FAT 16. there is a 2 GB limit per volume. FAT 32 is allows it format the whole drive as one volume. Also encryption through Windows is done VIA NTFS, if you want it encrypted and portable try the Truecrypt program. it's multi-platform.

---

### Post by wildmanne39 on 2011-06-16
> **kvcckid said:**
> Just wondering why when I format a usb dongle for FAT using ubuntu's disk utility, I believe it does a fat32 format, and when using encryption my windows machine and my iMac can't read it?
Shouldn't it just mount and request the key/passphrase?
Thanks in advance
Hi, I am going to give you some links on what you are looking for.
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live%20CD%20method%20of%20opening%20a%20encrypted%20home%20directory)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
I am not sure these link are what you are looking for but the are on the subject that you asked about.

---

