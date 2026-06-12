---
title: "Segmentation faultsts... 0%"
date: 2010-01-30
forum: General Help
---

### Post by anjanesh on 2010-01-30
For some reason Im getting a **Segmentation faultsts... 0%** error when trying to do a apt-get install on a VPS.

```
root:/var/www# sudo apt-get install php5-mcrypt
Segmentation faultsts... 0%
root:/var/www#
```

Where did this come from ?

---

### Post by paul_in_london on 2010-01-30
Try this:

```
sudo rm -vf /var/cache/apt/*.bin
sudo aptitude update
sudo aptitude full-upgrade
sudo aptitude install php5-mcrypt

```

If it doesn't work first time, boot into recovery mode and repeat those commands.

HTH

---

### Post by anjanesh on 2010-01-30
```
root:~# sudo rm -vf /var/cache/apt/*.bin
removed `/var/cache/apt/pkgcache.bin'
removed `/var/cache/apt/srcpkgcache.bin'
root:~# sudo aptitude update
Segmentation fault
root:~#
```> If it doesn't work first time, boot into recovery mode and repeat those  commands. Can I do this on a  VPS ?

---

### Post by paul_in_london on 2010-01-30
I don't really know anything about VPS. So this error is happening on a virtual server and you don't want to reboot it?

I've had this problem on my desktop though and if removing the bin files doesn't work at first then booting into recovery mode and trying again sorts it out.

---

### Post by anjanesh on 2010-01-31
>  and you don't want to reboot it? Unless there is an option to reboot in the command line.

---

### Post by anjanesh on 2010-01-31
Btw, I got the VPS with Ubuntu 9.04 and did a dist-upgrade to 9.10.
I guess this has to do with this ?

---

