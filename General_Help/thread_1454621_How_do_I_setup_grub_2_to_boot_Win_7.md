---
title: "How do I setup grub 2 to boot Win 7"
date: 2010-04-14
forum: General Help
---

### Post by harrisonk on 2010-04-14
Hello

This problem is for my parents computer, I have a 40 GB HDD and an 80 GB HDD the 80 has Win 7 (TM) and the 40 has Xubuntu 9.04.

I upgraded Grub to grub 2 and got that all sorted out but when ever I select " Windows Vista (loader)" from the grub 2 menu it says " invalad signature".

How would I fix this?

If there is anything I didn't provide Please tell me.

Harrison

---

### Post by harrisonk on 2010-04-20
Bump?

---

### Post by Keith1212 on 2010-04-20
```
sudo gedit /boot/grub/grub.cfg
```add this changing yours to the proper boot path and change windows xp to win 7 or what ever u want and paste it in the grub.cfg in the bottom.

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda2)" {
    insmod ntfs
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 98909a7e909a6314
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

```

if that doesn't work try this link its what i used. [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

good luck

---

### Post by wilee-nilee on 2010-04-20
> **harrisonk said:**
> Hello

This problem is for my parents computer, I have a 40 GB HDD and an 80 GB HDD the 80 has Win 7 (TM) and the 40 has Xubuntu 9.04.

I upgraded Grub to grub 2 and got that all sorted out but when ever I select " Windows Vista (loader)" from the grub 2 menu it says " invalad signature".

How would I fix this?

If there is anything I didn't provide Please tell me.

Harrison

Before you start editing the .cfg which I don't think you can as described post this boot script.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

