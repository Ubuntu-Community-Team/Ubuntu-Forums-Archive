---
title: "Mounting problems"
date: 2011-07-16
forum: General Help
---

### Post by hogar_pg on 2011-07-16
I have following problem in 10.04 64-bit:

I want to automatically mount 3 partitions during boot, so I did the following:

created 3 folders
```
sudo mkdir /media/Multimedia\ 1/
sudo mkdir /media/Multimedia\ 2/
sudo mkdir /media/Multimedia\ 3/
```edited fstab with:
```
gksu gedit /etc/fstab
```and added following code:
```
/dev/sda3 /media/Multimedia\ 1/ ext4 user,fmask=0111,dmask=0000   0   0
/dev/sdb3 /media/Multimedia\ 2/ ext4 user,fmask=0111,dmask=0000   0   0
/dev/sdc1 /media/Multimedia\ 3/ ext4 user,fmask=0111,dmask=0000   0   0

```As I want to mount that 3 partitions. I checked file system type with Ubuntu's Disk Utility and it is appropriate.

When I run the command:

```
sudo mount -a
```I get the following errors:

```
[mntent]: line 19 in /etc/fstab is bad
[mntent]: line 20 in /etc/fstab is bad
[mntent]: line 21 in /etc/fstab is bad

```As you can guess, lines 19 - 21 are those quoted here. Thanks!

---

### Post by Morbius1 on 2011-07-16
fmask and dmask are a fat, fat32, and ntfs thing not a ext4 or any linux filesystem thing.

---

### Post by hogar_pg on 2011-07-16
following code causes the same error:

```
/dev/sda3 /media/Multimedia\ 1/ ext4 defaults   0   0
/dev/sdb3 /media/Multimedia\ 2/ ext4 defaults   0   0
/dev/sdc1 /media/Multimedia\ 3/ ext4 defaults   0   0

```

error messages:
```
[mntent]: line 19 in /etc/fstab is bad
[mntent]: line 20 in /etc/fstab is bad
[mntent]: line 21 in /etc/fstab is bad

```

---

### Post by karlson on 2011-07-16
> **hogar_pg said:**
> following code causes the same error:

```
/dev/sda3 /media/Multimedia\ 1/ ext4 defaults   0   0
/dev/sdb3 /media/Multimedia\ 2/ ext4 defaults   0   0
/dev/sdc1 /media/Multimedia\ 3/ ext4 defaults   0   0

```

error messages:
```
[mntent]: line 19 in /etc/fstab is bad
[mntent]: line 20 in /etc/fstab is bad
[mntent]: line 21 in /etc/fstab is bad

```

Use try this:

```
/dev/sda3 /media/Multimedia\ 1 ext4 defaults   0   0
/dev/sdb3 /media/Multimedia\ 2 ext4 defaults   0   0
/dev/sdc1 /media/Multimedia\ 3 ext4 defaults   0   0

```

If that doesn't work try this:

```
/dev/sda3 /media/Multimedia_1 ext4 defaults   0   0
/dev/sdb3 /media/Multimedia_2 ext4 defaults   0   0
/dev/sdc1 /media/Multimedia_3 ext4 defaults   0   0

```

---

### Post by dino99 on 2011-07-16
mountall do the job on demand
mountmanager let you tweak devices/partitions as you like

---

### Post by hogar_pg on 2011-07-16
> **karlson said:**
> 
```
/dev/sda3 /media/Multimedia_1 ext4 defaults   0   0
/dev/sdb3 /media/Multimedia_2 ext4 defaults   0   0
/dev/sdc1 /media/Multimedia_3 ext4 defaults   0   0

```

This one works.Thanks

---

