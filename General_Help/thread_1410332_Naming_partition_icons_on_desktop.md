---
title: "Naming partition icons on desktop"
date: 2010-02-18
forum: General Help
---

### Post by Ron W on 2010-02-18
I have a number of partitions, each having an icon on the Desktop.

However, they are only referred to by size of partition. What I would like to do is give them a relevant name, e.g. photos, MP3s, etc.

My fstab uses UUIDs. Can I change the names while using these to refer to the partitions?

Thanks for any help

Ron

---

### Post by plucky on 2010-02-19
> **Ron W said:**
> I have a number of partitions, each having an icon on the Desktop.

However, they are only referred to by size of partition. What I would like to do is give them a relevant name, e.g. photos, MP3s, etc.

My fstab uses UUIDs. Can I change the names while using these to refer to the partitions?

Thanks for any help

Ron

I believe gparted on the Live CD would allow you to label un-mounted ext2/3/4 partitions,but not too sure if it will do NTFS.It did Fat32 on my pen drive however when I formatted it and gave it a label.The pen drive now displays an icon and label on the desktop when plugged in.

Good Luck

---

### Post by hobo14 on 2010-02-19
Or, a messier way to do it would be to mount them in /mnt mount points instead of /media mount points, then manually create links on the desktop to the mount points.

---

### Post by isecore on 2010-02-19
ntfstools in the repos have a utility for labeling NTFS partitions. Fairly easy to use, provided you're mostly comfortable with the commandline. That's provided you don't feel like booting into Windows and changing the labels there :)

> **plucky said:**
> I believe gparted on the Live CD would allow you to label un-mounted ext2/3/4 partitions,but not too sure if it will do NTFS.It did Fat32 on my pen drive however when I formatted it and gave it a label.The pen drive now displays an icon and label on the desktop when plugged in.

Good Luck

---

### Post by cong06 on 2010-02-19
I can confirm that gparted can label ntfs.
If there are any problems make sure that you have ntfs-3g and ntfsprogs installed.

Labeling partitions is a very clean way of doing this. It allows identification for most operating systems.

---

### Post by paddy100 on 2010-02-19
[FONT=Arial]I find a very simple way to do this is to use NTFSlabel.

```
sudo apt-get install ntfsprogs
```

then use the syntex [/FONT][FONT=Arial]ntfslabel [options] device [new_label]

eg..... to label sde1 to 'DATA' do the following....

```
sudo umount /dev/sde1
sudo ntfslabel /dev/sde1 DATA
sudo mount /dev/sde1 [mountpoint]
```

hope it helps[/FONT]

---

