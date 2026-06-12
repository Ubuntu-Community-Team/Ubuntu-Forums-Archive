---
title: "Boot times: the good, the bad, and mine"
date: 2011-08-28
forum: General Help
---

### Post by intheflesh on 2011-08-28
Hey, guys, trying to shave off some boot time, and I ran on some curious things. I know what you're thinking - how much? Well, it's about 40-50s which I consider too much since my gf's single-core Compaq CQ62-215DX laptop boots Windows 7 Home Premium in about 40s with Aero enabled.

Anyway, dmesg shows two interesting lines:
```
[    7.781016] EXT3-fs (sda6): mounted filesystem with ordered data mode
[   30.772728] Adding 1951860k swap on /dev/sda7.  Priority:-1 extents:1 across:1951860k 

```How I see it, it takes &#8776;23 seconds to "add 1951860k of swap space on /dev/sda7" My question is: Whyyyy? Couldn't it be... faster? Just curious. 

Here's my fdisk listing:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8fe48fe4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS
/dev/sda2            4865       60801   449313952+   f  W95 Ext'd (LBA)
/dev/sda5            4865        9963    40957686    7  HPFS/NTFS
/dev/sda6            9964       14826    39062016   83  Linux
/dev/sda7           14827       15069     1951866   82  Linux swap / Solaris
/dev/sda8           15070       60801   367342258+   7  HPFS/NTFS

```...and my /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=212bc2f3-ab40-47f9-8c34-133844c7a604 /               ext3    relatime,errors=remount-ro 0       1
# /data1 was on /dev/sda5 during installation
UUID=3090C9EA90C9B71E /data1          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
UUID=01CB95909631B3A0 /data2          ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# /windows was on /dev/sda1 during installation
UUID=866C46C86C46B32B /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       0
# swap was on /dev/sda7 during installation
UUID=31d6d2a4-7333-4f7f-9045-055c2195454e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by jerrrys on 2011-08-28
first thing to do is disable all startup app's that you don't need

System>preferences>startup app's

---

### Post by intheflesh on 2011-08-28
I did that. Anyway, I commented out the line in fstab that mounted swap partition, and nothing changed. So it's not about swap.

---

### Post by jerrrys on 2011-08-28
what kind of computer do you have, whats the specs

---

### Post by intheflesh on 2011-08-28
AMD Athlon II X4 640
2GB DDR3 (don't know exact specs)
250GB WD hdd
ATi Sapphire HD 5750

I also disabled some services, gonna reboot now and see if this helped.

---

### Post by jerrrys on 2011-08-28
yep, real good specs.  notice you got 4 core.  using all of them?  open up your system monitor and take a look.

---

### Post by intheflesh on 2011-08-28
Yeah, it listed like it was four processors, I guess that's alright. I could use some more ram though...

I was testing with bootchart and disabling ureadahead doesn't seem to make much difference. I'm going to put ureadahead back so it rebuilds /var/lib/ureadahead.pack file and see if it makes any difference.

---

### Post by intheflesh on 2011-08-28
Okay, just tested disabling ureadahead and enabling it again, and it feels a little bit faster than before, and definitely enabled is faster than disabled.
For example:
```

# at the end of dmesg:
#disabled:
[   23.577482] kvm: Nested Virtualization enabled
#enabled:
[   19.944272] kvm: Nested Virtualization enabled
#...
#disabled:
[   32.704039] eth0: no IPv6 routers present
#enabled:
[   29.944036] eth0: no IPv6 routers present
#...
#disabled:
[   61.117738] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
#enabled:
[   37.333582] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

```

I guess this is it in terms of optimization.

---

### Post by jerrrys on 2011-08-28
there are other post on speeding up boot time,  you may find something useful there.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=speed+up+boot&as_qdr=m6&sa=Google+Search&lang=en#821](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=speed+up+boot&as_qdr=m6&sa=Google+Search&lang=en#821)

---

