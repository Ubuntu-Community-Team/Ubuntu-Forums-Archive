---
title: "Writing to external Hard drive"
date: 2006-06-06
forum: General Help
---

### Post by SuperMightyMo on 2006-06-06
Hey

I had a question about writing to my external hard drive. When i try to write to my hard drive it gives the error message "no premmission to write". I can write if i use my terminal i use 

```
cp /home/personal_files/bla.zip /media/sdb5/bla.zip
```

but i have to be root to work for that....

does anybody know how to solve this, or to log in as root or something..?

---

### Post by aysiu on 2006-06-06
Can you plug in your drive, and then post back here the output of these terminal commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by SuperMightyMo on 2006-06-06
Hey

Thanx for your fast reply, but my system crashe ( windows falt :P), and now i have formated my external hard drive in NTFS, so i can store more thanx 4 gig's in one file. ( ps, is there an other format where i can do that, and when it has to be readed/writen by both windows en linux?). 

So i don't need to write to my external hard drive anymore, 

do you know if you can log in as root?, or can write to NTFS with Linux?

Thanx for your Help...

SuperMightyMo

---

### Post by christhemonkey on 2006-06-06
[http://www.ubuntuforums.org/showthread.php?t=142481](http://www.ubuntuforums.org/showthread.php?t=142481)

But use with caution. As it states:
> Warning! Ntfs writing support is still experimental! You should not enable it on production machines and/or volumes you don't have backups of. Proceed at your own risk!

---

### Post by givré on 2006-06-06
[QUOTE=SuperMightyMo]
do you know if you can log in as root?[/QUOTE]
You must not do that kind of things, definitly too dangerous. But you could have write access on an external hard drive as a simple user (in FAT32), just need some configuration.

[QUOTE=SuperMightyMo]or can write to NTFS with Linux?[/QUOTE]
Still experimental, you can do it but it's quite dangerous too 8-)

---

### Post by aysiu on 2006-06-06
Ext3 (Linux's native filesystem) can be read from and written to by Windows with the help of [http://www.fs-driver.org](http://www.fs-driver.org) and it can definitely store files bigger than 4 GB

NTFS will be read-only if you follow these instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by SuperMightyMo on 2006-06-07
Thanx for all your support, i think thiss will defenitly help me on my way...

---

