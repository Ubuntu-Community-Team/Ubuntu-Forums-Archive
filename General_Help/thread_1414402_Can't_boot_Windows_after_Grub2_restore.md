---
title: "Can't boot Windows after Grub2 restore"
date: 2010-02-23
forum: General Help
---

### Post by donsy on 2010-02-23
I recently did a clean install of WindowsXP, and after restoring Grub2 I'm now unable to boot into the Windows partition. The Grub menu has "(on /dev/sda1)" after the Windows entry and I know that's not correct. An fdisk -l yields the following:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1824    14651248+   7  HPFS/NTFS
/dev/sda2            1825        3648    14651280    5  Extended
/dev/sda5            1825        2665     6755301   83  Linux
/dev/sda6            2666        3415     6024343+  83  Linux
/dev/sda7            3416        3648     1871541   82  Linux swap / Solaris

Can someone tell me how to fix this so I can dual-boot Windows and Ubuntu?

---

### Post by brianfactors on 2010-02-23
This is risky. See: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

But I think you can get away with editing /boot/grub/grub.cfg (using something like gksu gedit )

and inserting:
```
menuentry "Microsoft Windows XP (on /dev/sda1)" {
        set root=(hd0,1)
        chainloader +1
}
```

---

### Post by grandmaster on 2010-02-23
my grub.cfg for windows xp is

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 9c60-0b4a
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###


```

hope it helps..

---

### Post by donsy on 2010-02-23
> **brianfactors said:**
> This is risky. See: [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

But I think you can get away with editing /boot/grub/grub.cfg (using something like gksu gedit )

and inserting:
```
menuentry "Microsoft Windows XP (on /dev/sda1)" {
        set root=(hd0,1)
        chainloader +1
}
```

You're not supposed to edit grub.cfg and I don't want to cause any more problems than already exist. Any other ideas?

---

### Post by donsy on 2010-02-23
Ooooohhh!!!!!! I forgot to update-grub! Duh!!!!!!!!!

---

### Post by brianfactors on 2010-03-18
Why not try
```
sudo grub-mkconfig
```and see if it detects the XP partition?

Oh, and you should also run
```
sudo update-grub
```
See if it works.

---

