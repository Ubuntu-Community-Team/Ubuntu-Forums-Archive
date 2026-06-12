---
title: "creating iso of system"
date: 2012-01-16
forum: General Help
---

### Post by kelticdruid on 2012-01-16
i just reinstalled Xubuntu been bouncing from different *buntu flavours and have finally gotten all the software removed i didnt need and added what i want.  is there a way to create a custom iso of my system so incase of system issues i can reinstall with what i have? would save me countless hours of work.

---

### Post by rng on 2012-01-16
I think you need 'remastersys'.

---

### Post by Serpher on 2012-01-16
.iso is for optical disks. If you want a bit for bit backup run dd on the partition in question then compress it.

```
dd if=/dev/sda1 of=backup.img
gzip backup.img
```

---

### Post by Matt__ on 2012-01-16
> **rng said:**
> I think you need 'remastersys'.

there is your answer, it will make you a backup image, but you can also use to make a custom live dvd of your system config...including updates, software, users and passwords if you so choose.

[remastersys]("http://www.remastersys.com/repository/ubuntu/")

It hasnt been updated in a while, but should work ok (I last used the maverick version on natty) but it may make you install a whole bunch of dependencies as youre on Xu.

---

### Post by kelticdruid on 2012-01-17
thank you will try remastersys. i knew there waas a way just forgot what was used :)

---

