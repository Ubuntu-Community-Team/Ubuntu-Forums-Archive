---
title: "Mounting a file"
date: 2011-12-19
forum: General Help
---

### Post by RefinersFire on 2011-12-19
A couple of years ago I tried to rescue a HDD which I accidentally formatted. It was a Windows XP Pro HDD. I cannot remember what format the HDD was (NTFS or FAT). These files are important and I need to access them. When I try mounting the .dd file (mount -t ntfs /media/image.dd image.dd -o loop) I get the reply (The device '/dev/loop0' doesn't seem to have a valid NTFS.)

If it is a fat file system, how would I mount it? (could be FAT32)

---

### Post by lechien73 on 2011-12-19
You could try:

```
sudo mount -t vfat /media/image.dd image.dd -o loop
```

Alternatively, running:

```
file /media/image.dd
```

might tell you more about it.

---

### Post by RefinersFire on 2011-12-21
Thanks. I will try that tonight.

---

### Post by RefinersFire on 2011-12-21
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by btindie on 2011-12-22
Is it an image of the entire hard disk or just the partition?

If it's the entire hard disk it then contains a partition table, you need to first assign the image to a loop back device using losetup. Then use partx /dev/loop0 to create the new device nodes that you'll need to access the partition. It'll probably create something like /dev/loop0p1 . You can then mount it using that as the device name.

---

