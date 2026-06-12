---
title: "UEC image bundeling"
date: 2010-05-26
forum: General Help
---

### Post by sunder.srv on 2010-05-26
Hi all,

We are in the process of installing and running an image on UEC cloud platform.

We tried the steps given on    "https://help.ubuntu.com/community/UEC/BundlingImages"

When we run the last command we got the following error, 

"cloud@ubuntu13:~$ uec-publish-tarball $UEC_IMG.tar.gz $RELEASE-$TIMESTAMP
Wed May 26 10:36:38 IST 2010: ====== extracting image ======
Warning: no ramdisk found, assuming '--ramdisk none'
kernel : lucid-server-uec-i386-vmlinuz-virtual
ramdisk: none
image  : lucid-server-uec-i386.img
Wed May 26 10:37:22 IST 2010: ====== bundle/upload kernel ======
Wed May 26 10:37:57 IST 2010: ====== bundle/upload image ======
Wed May 26 10:42:35 IST 2010: ====== done ======
emi="emi-200F15AF"; eri="none"; eki="eki-6D351ACB";
"

Our file system has a free space of 63 gb nearly (Total size : 80 gb)

Please help us,

---

### Post by dino99 on 2010-05-26
***** Warning: no ramdisk found, assuming '--ramdisk none' ******

seem you need to create a ramdisk or enable it

---

### Post by wcorey on 2010-06-18
> **dino99 said:**
> ***** Warning: no ramdisk found, assuming '--ramdisk none' ******

seem you need to create a ramdisk or enable it


I believe I did the same thing and it did run. I believe what happens is if you do not specify one in the image it uses the default. I don't pretend to be an expert on Linux system packaging but mine (without specified ram disk image) did run properly.

---

