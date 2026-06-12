---
title: "Can't Open Gparted after RAID creation"
date: 2010-10-26
forum: General Help
---

### Post by jdphillips10 on 2010-10-26
I have a fresh install of ubuntu 10.10 on a home server. The box has 1 80 gb hdd and 4 500gb hdds.
 
I installed gparted and mdadm and used disk utility to create a raid 5 array. The raid array was created and I was able to mount it. So I currently have a 1.5 TB raid array mounted. 
 
2 questions -
 
I want to mount this on startup. Do I just add it to the /etc/fstab file like a single volume?
 
I am unable to open gparted now. I get an error message stating that /dev/md/storage_array cannot be found. This is mounted to /media/storage_array. I don't know where "/md" came from. Any suggestions would be appreciated. Everything still seems to work but I can't use Gparted.

---

### Post by dcstar on 2010-10-27
> **jdphillips10 said:**
> I have a fresh install of ubuntu 10.10 on a home server. The box has 1 80 gb hdd and 4 500gb hdds.
 
I installed gparted and mdadm and used disk utility to create a raid 5 array. The raid array was created and I was able to mount it. So I currently have a 1.5 TB raid array mounted. 
 
2 questions -
 
I want to mount this on startup. Do I just add it to the /etc/fstab file like a single volume?
.........


This is probably still valid:
[http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/](http://bfish.xaedalus.net/2006/11/software-raid-5-in-ubuntu-with-mdadm/)

---

