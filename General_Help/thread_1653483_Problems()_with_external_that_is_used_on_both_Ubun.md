---
title: "Problems(?) with external that is used on both Ubuntu and Windows"
date: 2010-12-26
forum: General Help
---

### Post by alindgr1 on 2010-12-26
I am not sure if this could be a problem with Ubuntu or Windows at all, I'm just hoping that some one can perhaps tell me yes or no.  

I have an external hard drive that I have many movies and TV Shows on.  I use this hard drive on my computer under Ubuntu (10.10) and Windows XP.  My girlfriend uses it on her computer under Windows Vista and on her daughters computer under Windows 7.  

Sometimes, one of the movies will suddenly stop playing.  I have checked the files that this happens to, and the CODEC information is gone from the file.  I have checked the CODECs on the computer, checked the files with several programs, and I am not kidding.  The CODEC information is no longer in the file.

Like I said, I am not sure where this problem is coming from, I am just trying to narrow it down.  Thanks for any help.

---

### Post by efflandt on 2010-12-27
Linux is case sensitive and Windows usually is not.  So if whatever program you are using determines file type from filename extension (after the last dot), make sure that it looks for both capital or small letters, if the program itself is not case insensitive.

Otherwise data should not just disappear, unless writing the file to the drive was interrupted before it was finished (always "safely remove" external drives or flash).

---

