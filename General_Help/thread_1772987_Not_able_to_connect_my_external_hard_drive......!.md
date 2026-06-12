---
title: "Not able to connect my external hard drive......!"
date: 2011-06-01
forum: General Help
---

### Post by kaparthy on 2011-06-01
hi, i've been using xubuntu for a few days now and i am encountering this irritating problem!
i am able to connect other thumb drives and other flash drives to my laptop and they run fine on xubuntu but when i try to connect my 80 gigs external hard drive, it displays the following error message and shows nothing but an empty window of the hard drive with no contents of it :
ERROR:

"Failed to open directory "This IS RJ's". 
Error stating file '/media/This IS RJ's/xubuntu-11.04-desktop-i386.iso': Input/output error."

where "this is RJ's" is my hard drives label and the "xubuntu-11.04-desktop-i386.iso" is a file i believe inside the drive. ( is it causing the problem?)
this external hard disk is working fine on windows xp. but what is the problem on xubuntu? plz help guyz!

---

### Post by TeoBigusGeekus on 2011-06-01
I'd try relabeling the drive to a name with no spaces in it.

---

### Post by seawolf167 on 2011-06-01
I would run a disk check to make sure there aren't any bad sectors

```
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sdb
```

Where /dev/sdb is your external drive, i.e. from

```
sudo fdisk -l
```

---

