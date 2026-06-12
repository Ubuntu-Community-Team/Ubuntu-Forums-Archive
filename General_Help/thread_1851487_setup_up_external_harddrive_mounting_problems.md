---
title: "setup up external harddrive: mounting problems"
date: 2011-09-28
forum: General Help
---

### Post by BcRich on 2011-09-28
Hi
I just got a western digital my book 2TB external Usb 3 HDD, and I'm currently trying to set it up so that the drive automatically mounts at startup consistently. I'm using ubuntu studio 10.10 AMD64, and I also have Storage Device Manager (PySDM) installed. I can see the drive in Places but when I try to mount it by clicking on it I get the following error
```
Unable to mount My Book 
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``` 
also when my computer is starting up ubuntu give me the following error
```
disk drive for /media/sdc1 is not ready yet or not present
Continue to wait; or Press S to Skip or M for manual recovery
```
choosing to wait does not have any effect, and pressing S will give me the same error with sde1 instead of sdc1, pressing S again will continue to boot Ubuntu normally.
The drive is NTFS I know that ubuntu can read NTFS, but should the drive be formatted to be ext4? will this help solve the problem I'm having with mounting?

---

### Post by oldos2er on 2011-09-28
If Windows needs to access the drive, keep it NTFS. Shouldn't be a problem to mount it whether it's ext4 or NTFS.

Was it shut down cleanly?

---

### Post by BcRich on 2011-09-28
> **oldos2er said:**
> If Windows needs to access the drive, keep it NTFS. Shouldn't be a problem to mount it whether it's ext4 or NTFS.

Was it shut down cleanly?
hi
 thanks 4 the reply. i don't use any other os other than ubuntu so maybe i'll format the drive as ext4. problem is there are some files on the drive i'd like to make copies of before formatting the drive. so i need to mount the drive first. it's when i try to mount the drive that i get the errors. as far as i know the drive has been shutdown cleanly. any ideas what the error messages noted in my previous post mean?
thanks :)

---

### Post by collisionystm on 2011-09-28
Your best bet is to plug it into a windows workstation and do a 'safely remove USB' This what I always had to do when an NTFS drive failed to mount on Linux.

---

### Post by BcRich on 2011-09-28
> **collisionystm said:**
> Your best bet is to plug it into a windows workstation and do a 'safely remove USB' This what I always had to do when an NTFS drive failed to mount on Linux.

hi collisionystm
thanks for the suggestion, unfortunately i don't have a windows computer (or perhaps thats more fortunate than unfortunate in some cases). is there a way of forcing the drive to mount? like with pysdm or something...

---

### Post by collisionystm on 2011-09-28
> **BcRich said:**
> hi collisionystm
thanks for the suggestion, unfortunately i don't have a windows computer (or perhaps thats more fortunate than unfortunate in some cases). is there a way of forcing the drive to mount? like with pysdm or something...

Unfortunately I do not know of a way. If you find a way to do it that works, let me know. I could not find a solution. I am sure I did not search hard enough. Hopefully someone will come along that  can help. 

I wonder if you ran ReactOS in virtualbox and mounted your drive if it would work. It is pretty much an OpenSource Windows Compatible system.
[http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)

---

### Post by BcRich on 2011-09-28
> **collisionystm said:**
> 
I wonder if you ran ReactOS in virtualbox and mounted your drive if it would work. It is pretty much an OpenSource Windows Compatible system.
[http://www.reactos.org/en/index.html](http://www.reactos.org/en/index.html)
interesting i had not heard of reactos thanks for the heads up collisionystm :)

---

