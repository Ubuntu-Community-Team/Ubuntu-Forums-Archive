---
title: "Need HELP - System not booting"
date: 2011-10-10
forum: General Help
---

### Post by AndrewGen on 2011-10-10
I'm getting the following error message when trying to start Ubuntu:
_________________________________________________________
mount: mounting /dev on /root/dev failed: No such file directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg.
 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)
_________________________________________________________
that's it. The system was working fine for months. 
I would appreciate any help,
 
Thanks,
Andrew

---

### Post by prodigy_ on 2011-10-10
Something is wrong with the root file system. If you're sure the HDD is okay, try to boot from a Live CD and run **fsck**.

---

### Post by drs305 on 2011-10-10
It's possible you have some corrupted files. Boot a LiveCD or rescue CD, open a terminal and run the following. Use the correct values for XY. The Ubuntu partition must not be mounted.

```

sudo umount /dev/sdXY  # Make sure the Ubuntu partition is not mounted. Substitute correct values for XY
sudo e2fsck -f -y -v /dev/sdXY
```
Example: sudo e2fsck -f -y -v /dev/sda5

If you get a "device busy", even from the Ubuntu LiveCD, try the Slax LiveCD: 
[http://www.slax.org/get_slax.php ]("http://www.slax.org/get_slax.php")

---

### Post by AndrewGen on 2011-10-10
> **prodigy_ said:**
> Something is wrong with the root file system.  If you're sure the HDD is okay, try to boot from a Live CD and run **fsck**.

> **drs305 said:**
> It's possible you have some corrupted files. Boot a LiveCD or rescue CD, open a terminal and run the following. Use the correct values for XY. The Ubuntu partition must not be mounted.

```

sudo umount /dev/sdXY  # Make sure the Ubuntu partition is not mounted. Substitute correct values for XY
e2fsck -f -y -v /dev/sdXY
```sudo e2fsck -f -y -v /dev/sda5

If you get a "device busy", even from the Ubuntu LiveCD, try the Slax LiveCD: 
[http://www.slax.org/get_slax.php ]("http://www.slax.org/get_slax.php")

**It's up and running.  Thank you both.**

***This forum is great and so are its members.***

---

