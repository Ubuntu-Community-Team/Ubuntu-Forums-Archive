---
title: "User permissions for removable ext3 disk in multi user environment"
date: 2010-11-18
forum: General Help
---

### Post by Fopper on 2010-11-18
Hello,

My girlsfriend and I share a laptop and we have different settings so different users. She has a removable disk that I also use from time to time and is also plugged in in an other PC that only has my account on it. The extra account for her is rather new and after we made it we ran into problems with user permissions on the removable disk. As it was only used by foppe:foppe all files and maps are owned by them, but when she wants to use it she can't write to these files and maps. 
Ofcourse I can chmod them every time a different user needs them, but that doesn't look like permanent solution. So my question is whether there is a way to mount the disk as a certain user (foppe) or that I can use umask in some way (it is a ext3 formated disk, and I understood umask is not possible then). 
I tried to copy paste the line from mtab into fstab and add user=foppe, but then nautilus says I need to be root to mount the drive.

---

### Post by viralmeme on 2010-11-18
> **Fopper said:**
> a laptop .. has a removable disk that .. was only used by foppe:foppe

Make her a member of group foppe:

$sudo usermod -a -G foope girlfriend

---

### Post by Fopper on 2010-11-19
Thank you, I did that, but it is not yet working. Group rights are different then user rights I guess and I could read as everyone. If I am not mistaken standard the rights are 644 for files and 755 for directories, so a group has no extra rights than everyone.

---

### Post by deanjm1963 on 2010-11-19
I have a removable called "removable" that I use between two different machines with two different users.

I changed the ownership to myself:users e.g.

```
sudo chown -R dean:users /media/removable
```

I've had no problems with either myself or the other user reading and writing files to it.

Hope this helps.

---

