---
title: "Formatting And Mounting Harddrives"
date: 2006-01-20
forum: General Help
---

### Post by renzokuken on 2006-01-20
in my pc at the moment i have three harddrives.

a SATA drive /dev/sda on which ubuntu is installed (ext3)
and two IDE drives, both NTFS which are storage from my windows days (/dev/hda  ..and.. /dev/hdb   ...it is hdb i want to reformat)

i no longer have a need for the files on one of the NTFS drives and would like to reformat it to ext3 and use it as a writable disk for ubuntu.

i used qtparted to reformat the drive as ext3, but am now having problems mounting it, i would like it to be auto mounted like my ntfs drives on bootup but i have noidea what to put in the fstab. thanks.

---

### Post by earobinson on 2006-01-20
/dev/hda7 /mnt/shared ext3 defaults 0 0

how that work?

---

### Post by renzokuken on 2006-01-20
half way there

by adding **/dev/hdb1 /media/storage ext3 defaults 0 0** (obviously had to modify it slightly to yours eraobinson) to my fstab the drive now automounts and appears on my desktop, but i do not have read/write access to it and there is a folder called "Lost+found" in it

what is this and how can i begin copying files to this drive?

---

### Post by renzokuken on 2006-01-20
ok, i can copy files to the drive via 

sudo cp blah.jpg /media/storage

so its all working fine, the problem is obviously permissions.

i just want to be able to easily drag and drop files to and from this drive using nautilus. any ideas?

---

### Post by LordBug on 2006-01-20
check ownership and permissions of /media/storage.  It's probably set to root/root

---

### Post by renzokuken on 2006-01-20
problem solved with a chmod -R a+w /media/storage

is this a permanent change, i.e. will it keep these new permissions after a reboot?

---

### Post by earobinson on 2006-01-20
oops sorry bout that forgot about ownership, I was going kinda blind however cuz Im at work on windows.

---

