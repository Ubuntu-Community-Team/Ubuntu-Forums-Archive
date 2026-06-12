---
title: "depmod reports &quot;Can't read module&quot; ... &quot;Exec format error&quot;"
date: 2010-08-11
forum: General Help
---

### Post by msp3k on 2010-08-11
Hi guys,

I have many hosts still running 9.10 (2.6.31-22-generic x86_64).  One host recently suffered a corrupted hard drive after a power outage.  After fscking the drive, I saw a lot of errors from depmod:

WARNING: Can't read module /lib/modules/... Exec format error
Segmentation fault

Fearing the worst I reformatted and reinstalled the machine (still 64-bit 9.10).  But I still see this error, even after a fresh install.

I'm not talking about modules installed with dkms or custom-compiled modules either, I'm talking modules that are a part of the linux-image-2.6.31-22-generic package.

Anyone have any ideas?

---

### Post by msp3k on 2010-08-11
Not sure why the modules became corrupt during a fresh install (perhaps this is a sign of a dying HDD...)  But the following command fixed me right up:

sudo apt-get --reinstall install linux-image-2.6.31-22-generic

Or, if you want a more generic solution:

sudo apt-get --reinstall install linux-image-$(uname -r)

---

