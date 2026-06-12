---
title: "Help with a .DMG file?"
date: 2011-06-24
forum: General Help
---

### Post by Egregious on 2011-06-24
I know it's for a mac, but i have a .DMG file and i know you can mount them on Ubuntu, i went to the directory and typed 
```

file LeagueofLegendsBetaDownloader.dmg 

```
with the output LeagueofLegendsBetaDownloader.dmg: data

then i typed 
```
sudo mount -t hfs -o loop LeagueofLegendsBetaDownloader.dmg /mnt
```
with the result of mount: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

How do i get it to mount so i can install?

---

### Post by nerdy_kid on 2011-06-24
> **Egregious said:**
> I know it's for a mac, but i have a .DMG file and i know you can mount them on Ubuntu, i went to the directory and typed 
```

file LeagueofLegendsBetaDownloader.dmg 

```
with the output LeagueofLegendsBetaDownloader.dmg: data

then i typed 
```
sudo mount -t hfs -o loop LeagueofLegendsBetaDownloader.dmg /mnt
```
with the result of mount: wrong fs type, bad option, bad superblock on /dev/loop0, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so

How do i get it to mount so i can install?

While it may be possible to mount the dmg, it is impossible to install it.  Ubuntu uses a totally different system then MacOSX.

If you still want to mount it despite knowing it is useless, then this might work:

```

sudo mount -o loop DMG MOUNTPOINT

```

---

### Post by Matt__ on 2011-06-24
would it mount and work in [MAC on Linux](http://www.maconlinux.org/) ?

---

### Post by nerdy_kid on 2011-06-24
> **Matt__ said:**
> would it mount and work in [MAC on Linux](http://www.maconlinux.org/) ?

mac on linux looks like a virtual machine, correct?  In which case, I know VirtualBox can run the Intel OSX if your CPU has hardware virtualization.  QEMU might be able to run OSX without CPU HV but I don't think so.

---

