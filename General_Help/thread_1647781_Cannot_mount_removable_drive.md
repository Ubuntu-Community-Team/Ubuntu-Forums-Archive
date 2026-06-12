---
title: "Cannot mount removable drive"
date: 2010-12-17
forum: General Help
---

### Post by GNUway Tech on 2010-12-17
My PC is an HP with a removable drive that I recently reformatted to use as a backup for my audio files. Now, however, since I've began working with my audio files, the drive won't mount.

I'm getting an error message like this:

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so



If I have to reformat this drive, I will lose all my audio files.

---

### Post by akand074 on 2010-12-17
Did you format it in Ubuntu? To what file type? It used to mount in Ubuntu but now doesn't? Are you using it in Windows as well? I would reformat it in Ubuntu to fat32 if it's being used on multiple OSes.. seems like there is a problem with the formatting.

---

### Post by GNUway Tech on 2010-12-17
I formatted it in Ubuntu using GParted. It's in ext3 format. I've only ever used it in Ubuntu, and it mounted fine. I'm not using it on any other operating systems.

I hope beyond anything that I don't have to reformat the drive, because all my audio files are on it. I don't have any other backup for them. If I can just get it to mount again, I'll move the files over to another drive. Is there a way to change the format without losing the files???

---

### Post by akand074 on 2010-12-17
> **GNUway Tech said:**
> I formatted it in Ubuntu using GParted. It's in ext3 format. I've only ever used it in Ubuntu, and it mounted fine. I'm not using it on any other operating systems.

I hope beyond anything that I don't have to reformat the drive, because all my audio files are on it. I don't have any other backup for them. If I can just get it to mount again, I'll move the files over to another drive. Is there a way to change the format without losing the files???

Weird. But if it's plugged is it recognized by Ubuntu when you run this in the terminal:

```
sudo fdisk -l
```

If it does, then you can try to mount it manually. 

```
sudo mount -t ext3 /dev/sdXY /mnt
```

Replacing X and Y with whatever partition the usb drive is being read as. Otherwise you can install [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"). You can get information about it from there but it's in the Ubuntu repositories:

```
sudo apt-get install testdisk
```

---

