---
title: "Partition doesn't mount correctly at startup"
date: 2011-08-01
forum: General Help
---

### Post by kleinempfaenger on 2011-08-01
Hi,
my "places menu" references folders on a second partion, where I store all my personal files (ntfs, as I use it also from Windows). After boot those folders wouldn't show in Thunar. Some other programs, as Fontmatrix, wouldn't find databases stored there, what messes them up. Thunderbird has problems to recognize profiles etc.
What is strange, the partition seems to be mounted at startup as I can see and select it from Thunar. Also, it appears on Desktop. After selecting the partition, closing and reopening Thunar everything works fine, places would show correctly and Fontmatrix database is ok.
Ntfs-manager is installed, sda2 marked.
Installed pyDSM, sda2 mounts at startup. 

Greetings , kleinempfaenger

---

### Post by sisco311 on 2011-08-01
Hi,

Please post the output of:
```
mount
```
```
cat /etc/fstab
```
and
```
sudo blkid -c /dev/null
```

---

### Post by kleinempfaenger on 2011-08-02
Thanks Sisco,
problem solved, but I couldn't say how.
Just renamed mounting point in /media in pySDM. After that everything was messed up, partition wouldn't mount any more. So I changed back the name of the mounting point, which I found in a link inside of an Inkscape document. Now everything works fine. Places show correctly after startup. Fontmatrix would work fine, too, but I discovered some advantages of Fonty Python ;)

Greetings, kleinempfaenger

---

