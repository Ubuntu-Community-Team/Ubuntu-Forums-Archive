---
title: "GRUB disappeared after Kubuntu re-installation"
date: 2012-01-09
forum: General Help
---

### Post by andy17 on 2012-01-09
As I was saying in my other post, I just re-installed Kubuntu and now Grub is not showing up anymore (I can't choose between Kubuntu and XP, it simply log in Kubuntu).

I searched in the forum but wasn't able to find anything similar...


this is the output of SUDO FDISK -L

```
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 testine, 63 settori/tracce, 9964 cilindri, totale 160086528 settori
Unità = settori di 1 * 512 = 512 byte
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identificativo disco: 0xd9b7d9b7

Dispositivo Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    27342847    13670400   83  Linux
/dev/sda3        27344894   160055594    66355350+   5  Esteso
/dev/sda5       107442783   149565149    21061183+   7  HPFS/NTFS/exFAT
/dev/sda6       149565213   160055594     5245191   82  Linux swap / Solaris
/dev/sda7        27344896   107442175    40048640   83  Linux
```

sda1 is "/" partition
sda7 is "home" partition
sda5 is XP partition



I tried:
```
sudo update-grub2
```

```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```


but still no grub at all when starting PC (neither with Kubuntu, Kubuntu recovery and memtest... simply, no grub is shown)

any idea???
thanks!

Andy

---

### Post by zvacet on 2012-01-09
If you don´t see Grub,press **shif key** and thten you should see it.

---

### Post by MartijnNL on 2012-01-09
If you read /boot/grub/grub.cfg is there any reference to your windows installation? From the last bit you posted it would seem not. Looks like os-prober isn't detecting windows.

One solution might be to add a manual menu entry to the menu:

Edit /etc/grub.d/40_custom and add something like:
```
menuentry "Windows XP" {
set root=(hd0,5)
chainloader +1
}
```

You could also try pressing and holding Shift as soon as the black screen appears during boot (right after the [POST]("https://en.wikipedia.org/wiki/Power-on_self-test") messages). You can then check for the presence of XP in the menu. If it's not there, my solution above might work. Not ideal, but it should work.

---

### Post by andy17 on 2012-01-09
Thanks a lot Martijn!

Tonight I'll give it a try and let you know if it works.

---

