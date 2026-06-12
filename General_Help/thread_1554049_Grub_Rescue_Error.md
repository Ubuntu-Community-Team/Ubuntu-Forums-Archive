---
title: "Grub Rescue Error"
date: 2010-08-16
forum: General Help
---

### Post by whitetimer on 2010-08-16
Hi All ...

Last night my desktop froze while i was downloading some files, so i reset my pc.  When it started the boot process, it stopped at the boot cd/dvd with an error message

> 
Error: file not found
Grub Rescue>
How do i resolve this problem ?  I have just tried burnt a new Live CD Image and now i can run the Live CD install ...... But now what do i do ?

I can use the ls and set commands 

ls gives me (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1) (hd1) (hd1,1)

set command gives me Prefix=(hd0,3)/boot/grub   root=(hd0,3)
Help !!!

Many Thanks

---

### Post by r_s on 2010-08-16
boot using a live cd, find which is your linux partition and re-install grub.

[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by whitetimer on 2010-08-16
Never mind ... doing a clean install instead 

Cheers

---

