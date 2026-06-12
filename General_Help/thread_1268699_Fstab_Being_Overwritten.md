---
title: "Fstab Being Overwritten"
date: 2009-09-17
forum: General Help
---

### Post by etchmigrant on 2009-09-17
I've recently migrated from Debian Etch to Ubuntu 9.04, with (manually compiled) KDE 3.5, and I'm having problems with auto-mounting with fstab.  Here is a copy of my fstab as I enter it:  >  /dev/sda1        /      ext3    relatime,errors=remount-ro 0       1 /dev/sda6        /home  ext3    relatime        0       2 /dev/sda2        /mnt/windoze   ntfs ro,umask=0222 0 0 /dev/sda5        none            swap    sw              0       0   However, when I reboot the machine, something overwrites it, and I end up with:  >  # /dev/sda1 UUID=9581a9bc-8a73-4409-9077-b57fe1e402c8 /               ext3    relatime,errors=remount-ro 0       1 # /dev/sda6 UUID=ac70d8ca-0fc6-48b3-b1ad-72fe614aca16 /home           ext3    relatime        0       2 # /dev/sda5 UUID=177711c4-44b9-439d-907f-09e8be5896b7 none            swap    sw              0       0 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 /dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0    And, of course, *mount x * tells me whichever device I try to mount isn't listed in fstab.  Manually mounting works fine, as long as I include switches and options, but a simple &quot;mount /dev/sda5&quot; does not.  Dolphin (KDE4) will automatically detect and mount any devices just by clicking them.  Konqueror (KDE 3.5), however, will not even recongnise the devices in in it's media directory, unless they're auto-mounted.   I did partition the disk **after** installing Ubuntu with parted.  I'm wondering if there's possibly some residue left over from that?  Basically, I want to find out what's overwriting my fstab, and stop it doing it....any suggestions?

---

### Post by schmidtbag on 2009-09-17
i'm really unsure why this happened, but why don't you just go with a different distro instead?  ubuntu is meant to do everything for you in the way it comes as, its supposed to be as work free as possible and you compiled an entire graphical interface.  try mepis, it uses kde3 and its very modern and still updated.  its deian based, like ubuntu, and just as easy to set up.  i'd say its by far the best kde3 disto i've used, and its popularity is proof by itself


ubuntu is just too large, theres so many possibilities that could affect your problem for people like me who don't know everything about /etc/fstab, so go with something a little more simple and just as reliable

---

