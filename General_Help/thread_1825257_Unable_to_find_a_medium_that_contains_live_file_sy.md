---
title: "Unable to find a medium that contains live file system ubuntu"
date: 2011-08-15
forum: General Help
---

### Post by ibrahim.k on 2011-08-15
Hello there, I am trying to install Meerkat 10.10 on my desktop  using an external hard disk but I get a message that says "unable to  find a medium that contains live file system" Md5 is okay ! and I have  used usb start-up disc creator.

I have searched for this problem before and found many threads but it was not helpful.

thnx

---

### Post by LowSky on 2011-08-15
Sorry I'm just trying to understand. Does the External hard drive being used as the usb liveCD?

---

### Post by ibrahim.k on 2011-08-15
Yes, Exactly.
I have used Start up disc creator.
System >>Administration >> Start up disc creator

---

### Post by varunendra on 2011-08-15
> **ibrahim.k said:**
> Yes, Exactly.
I have used Start up disc creator.
System >>Administration >> Start up disc creator
Startup disk creator in 10.10 has been reported to produce this error sometimes due to some bug in its syslinux modules. There are fixes/workarounds to it, but I'd suggest to try the one included in 10.04, or else try unetbootin.

I presume that you have a primary FAT32 partition on the external drive onto which you are installing the live OS. I remember to have seen at least one user reporting that converting the partition to FAT16 fixed the error for him. But in the same thread (on another forum/blog) it didn't work for others.

---

### Post by ibrahim.k on 2011-08-18
Thnx everybody..

I have burned the ISO file into an empty CD this is how it worked.
I did not use an external hard drive for installing or usb flash disc

---

