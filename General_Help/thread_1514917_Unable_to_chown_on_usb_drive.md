---
title: "Unable to chown on usb drive"
date: 2010-06-21
forum: General Help
---

### Post by bazzal1941 on 2010-06-21
Running Ubuntu 10.04.

I have a mounted usb drive where the owner and group for all files and directories is root/root;

I try and sudo chown and it does not give an error but it does not work.

There are references all around this subject on several forums but I have not found an exact solution.

From what I can gather it does not work because it is an NTFS partition. Does anybody know if that is correct

---

### Post by warfacegod on 2010-06-21
Yep that's right chowning won't work on NTFS. If you aren't going to use the drive on any Windows machines then format it to ext4 with Gparted. chown will work after that. Backup your data first!

```
sudo apt-get install gparted
```

---

### Post by bazzal1941 on 2010-06-21
Thanks warfacegod.

---

### Post by warfacegod on 2010-06-21
Sure!:p If this is the answer that you wanted and/or it works for you, please mark this Thread as Solved under Thread Tools

---

