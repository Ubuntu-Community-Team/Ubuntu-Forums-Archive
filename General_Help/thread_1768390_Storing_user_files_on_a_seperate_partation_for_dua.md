---
title: "Storing user files on a seperate partation for dual booting"
date: 2011-05-26
forum: General Help
---

### Post by marblecatdog on 2011-05-26
So I set up my laptop to dual boot windows and ubuntu 11.4, and it appears to work fine, I can boot into both etc.  Now what I'm trying to do is set up a separate partition to store all of my documents, pictures etc so that I can have access to them in both ubunut and windows.  So I have this separate partition on my harddrive, formatter as fat32 so both OSs can read and write it, problem is that I'm having lots of trouble auto mounting, accessing and using the files on this partition on ubuntu.  I got it to auto mount, but only root has access to modify files, I can open and read but not delete or modify.  Also I can't make links to the files on this partition, I was hoping to just link the documents and other folders in my ubuntu home directory to the folders in the new partition, but I can't make links to them.  Is there a better way to go at this problem of sharing data between two OSs or any I doing something wrong?  If you need any additional info just ask and i'll do my best to get it to you.  Thanks!

---

### Post by Hedgehog1 on 2011-05-27
Could you please post your /etc/fstab file (assuming you are doing the automount from that file)?

Thanks!

***The Hedge***

:KS

---

