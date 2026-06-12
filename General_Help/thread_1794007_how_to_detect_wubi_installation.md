---
title: "how to detect wubi installation?"
date: 2011-06-30
forum: General Help
---

### Post by forger on 2011-06-30
Is there a way to check if the current installation was done through wubi?
e.g. something like "lsb_release -a" command that would show that the installation was done through wubi?

Perhaps the "/host" mounted directory?

---

### Post by Mark Phelps on 2011-06-30
While /host is generally used with a Wubi install, someone could also have created that directory.

Why not just do an fdisk and look at the filesystems.  If there are no Linux filesystems there, and Ubuntu runs from an internal drive, it must have been a Wubi installation.

---

### Post by bcbc on 2011-06-30
Probably the easiest way is to check /etc/fstab.

If you want to do it in [code]("https://github.com/bcbc/Wubi-resize/blob/master/wubi-resize.sh#L155")
```
grub-probe --target=device /boot
# if the result is /dev/loop0 
sudo losetup /dev/loop0
```

The result should show /host/ubuntu/disks/root.disk

---

