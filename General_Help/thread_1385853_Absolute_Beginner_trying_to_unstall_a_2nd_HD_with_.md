---
title: "Absolute Beginner trying to unstall a 2nd HD with 9.04"
date: 2010-01-20
forum: General Help
---

### Post by fagan on 2010-01-20
I have been searching through the web trying to find a way to install (mount?) and format a used 80G HD. I have installed GParted and it makes no sense to me. None of the tutorials on youtube have been helpful either (except to get me frustrated) I want to learn Linux and use it for my main os but, having these troubles makes it difficult. I am looking for a mentor who would help teach the teachable also.

---

### Post by zvacet on 2010-01-20
[Here]("http://ubuntuforums.org/showthread.php?t=724817&highlight=multiboot")

---

### Post by vanadium on 2010-01-20
There is an Absolute beginners forum section here, where brand new users can be helped without having to apologize.

The link zvacet gave is vor a dual boot system, which is, as I understand, not your interest now. I understand you just want to use the additional storage space in your existing Ubuntu installation.

Once the drive is properly installed in your system, there are two steps involved: 1) format the drive, and 2) mount the drive in your file system. I can provide the few commands necessary if you post the output here of "sudo fdisk -l".

A next issue will be to adjust permissions to adjust what users can do on the drive. By default, a normal user can only read a drive on linux.

---

