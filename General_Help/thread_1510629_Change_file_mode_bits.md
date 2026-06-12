---
title: "Change file mode bits"
date: 2010-06-15
forum: General Help
---

### Post by kdb8dm on 2010-06-15
Hi all,

I have a dual boot (WinXp, Ubuntu) on my machine. Unbuntu is installed in the same partition of WinXp. Evertime i have to access a windows file or folder i mount the windows drive using the following command 

```
sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda1 /media/c
```

This works just fine. My problem is that all the files are loaded with -rwxrwxrwx and the directories drwxrwxrwx. I cannot change the file mode bits using chmod even in su mode. chmod incidentally works just fine and does not give any error. But the file mode bits are still the same. 

Any suggestions ?

---

### Post by bodhi.zazen on 2010-06-15
Rather then umask, use dmask and fmask

fmask and dmask are similar to umask, but apply to directories and files.

See also :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

