---
title: "external harddrive, odd behavior"
date: 2009-07-17
forum: General Help
---

### Post by Stargazer989 on 2009-07-17
1: i have to use 'sudo nautilus' to transfer files into my external harddrive.
2: files are said to be completely transferred but when i get on windows i only have 1 file and a 1/3 of the file at that. if i re-check the files on ubuntu, they're not there as they have said to have originally been.


additional info: volume is NTFS. system 1: ubuntu 9.04. system 2: vista pro SP1.

---

### Post by aesis05401 on 2009-07-17
> **Stargazer989 said:**
> 1: i have to use 'sudo nautilus' to transfer files into my external harddrive.
2: files are said to be completely transferred but when i get on windows i only have 1 file and a 1/3 of the file at that. if i re-check the files on ubuntu, they're not there as they have said to have originally been.


additional info: volume is NTFS. system 1: ubuntu 9.04. system 2: vista pro SP1.

Is this an an external USB device?  

Have you tried changing permissions on the device?

What happens before you log into Windows (ie: after Ubuntu says it has finished - can you check the status of the files on the external before rebooting into Windows?)

And for clarification, the two OSs you mention are dual-booted off the same machine, correct?  We are not dealing with NFS shares are we?

---

### Post by Kraut~salat on 2009-07-17
make sure you unmounted the hdd before you unplugged it.

You can also force writing of buffered writes onto the harddrive by calling "sync". Try that next time after copying.

---

### Post by Stargazer989 on 2009-07-17
this is an external (usb) harddrive (as descibed in the topic). I may be seeing the problem now; i haven't been 'unmounting' the device before unpluggind (haven't had to before). 

i'll do a test now.

---

### Post by Stargazer989 on 2009-07-17
i should have mentioned it before; these are two different machines. it seems like unmounting the hdd worked. but vista is still vista... ;_; (says the device needs to be checked or something)

closing topic. thanks. :D

---

### Post by Stargazer989 on 2009-07-17
has the 'close topic' option been discontinued or moved? can't find it under Thread Tools anymore. D:

---

