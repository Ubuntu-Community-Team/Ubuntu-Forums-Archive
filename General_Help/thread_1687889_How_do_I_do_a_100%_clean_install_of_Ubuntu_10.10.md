---
title: "How do I do a 100% clean install of Ubuntu 10.10"
date: 2011-02-14
forum: General Help
---

### Post by ravij96 on 2011-02-14
Hi, so after royally screwing some things in ubuntu 10.10 I want to do a clean install.  I want to do a 100% one because I do not have anything important on this ubuntu partition since I have only had it for 2 days.  OK, so if i go to the live cd the install along side another operating system doesnt work for me because the partition is only 30gb.  Now my question is what do i do in the advanced partitioning tool.  I find my partition and click on it.  Then how do i wipe this partition, creating free space, then reinstalling Ubuntu on it.  So, simply all I want is Ubuntu exactly how it was when i first got it with nothing on it but the pre installed things and settings. Also, will this mess up GRUB because the last thing I want is to not be able to log in to either windows or ubuntu.  Thank you to anyone who answers my question :).

---

### Post by Mrich1976 on 2011-02-14
I'll give it a try, because I recently had to do a full, clean install of 10.10, albeit not a dual-boot.

What you'll probably have to do (and someone else would probably be better informed than I) is to wipe the partition. In other words, start the install, and when it asks you about the partition, select the one that Ubuntu is currently on, and there should be some prompt or something to ask you to overwrite the partition.

---

### Post by ravij96 on 2011-02-14
> **Mrich1976 said:**
> I'll give it a try, because I recently had to do a full, clean install of 10.10, albeit not a dual-boot.

What you'll probably have to do (and someone else would probably be better informed than I) is to wipe the partition. In other words, start the install, and when it asks you about the partition, select the one that Ubuntu is currently on, and there should be some prompt or something to ask you to overwrite the partition.
Thanks :D I'm really hoping i can figure this out :/

---

### Post by Iowan on 2011-02-14
I recently re-installed 10.10 on a dual-boot laptop. As I recall, I selected the existing (ext4) partition, marked it for formatting, and set it to mount as "/" (I don't have separate partitions). Owing to a flaky CD/DVD drive, and display issues, I got to do it twice. I left the Windows partition alone.

---

### Post by ravij96 on 2011-02-14
> **Iowan said:**
> I recently re-installed 10.10 on a dual-boot laptop. As I recall, I selected the existing (ext4) partition, marked it for formatting, and set it to mount as "/" (I don't have separate partitions). Owing to a flaky CD/DVD drive, and display issues, I got to do it twice. I left the Windows partition alone.
This worked Ty.

---

