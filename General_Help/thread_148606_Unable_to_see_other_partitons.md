---
title: "Unable to see other partitons"
date: 2006-03-22
forum: General Help
---

### Post by Anilkumar on 2006-03-22
Hello everybody

plz help me

In my ubuntu i am not able to see my other partitons.how can i fix this problems?

plz fix my problem

---

### Post by Ramses de Norre on 2006-03-22
[https://wiki.kubuntu.org/MountingWindowsPartitions]("https://wiki.kubuntu.org/MountingWindowsPartitions")
It's the same in ubuntu/kubuntu.
If it's an ext3 partiton you'll need different options which I can't give you now (not on linux for the moment).

---

### Post by Anilkumar on 2006-03-23
plz i could not get god support i am getting errors like this 
when i want to mount my second partition

anilkumar@anilkumar:~$ mkdir /media/song
anilkumar@anilkumar:~$ sudo mount /dev/hda2 /media/song -t vfat -o iocharset=utf8,umask=000
mount: wrong fs type, bad option, bad superblock on /dev/hda2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


what is alll about

plz fix me

i went by using the link u gave me

---

### Post by justleen on 2006-03-23
are the drives NTFS formatted?

---

