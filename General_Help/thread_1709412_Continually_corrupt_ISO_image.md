---
title: "Continually corrupt ISO image"
date: 2011-03-18
forum: General Help
---

### Post by Dyonas on 2011-03-18
I was going to install Ubuntu 10.10 (32-bit) on my laptop as a dual-boot with Windows Server 2008 R2 but for reasons I can't work out the ISO is corrupt every time. I've downloaded it six times now and all of them fail the MD5 check. Is there an issue with the ISO image hosted? I don't see how I can get six consecutive failures any other way.

---

### Post by Grenage on 2011-03-18
Run a Memory/RAM check, it's possible that bad RAM could corrupt the data.

---

### Post by seawolf167 on 2011-03-18
> **Grenage said:**
> Run a Memory/RAM check, it's possible that bad RAM could corrupt the data.

+1. Most likely its your RAM, reboot and run memtest86 overnight (so it can run 7+ cycles) and see if any errors occur.

It could also be a failing/bad driver for your ethernet card if memtest86 doesn't turn up any errors, the solution to that would be to put in a PCI card if using your Mobo slot (or vice versa) and test that out

---

### Post by dh04000 on 2011-03-18
> **Dyonas said:**
> I was going to install Ubuntu 10.10 (32-bit) on my laptop as a dual-boot with Windows Server 2008 R2 but for reasons I can't work out the ISO is corrupt every time. I've downloaded it six times now and all of them fail the MD5 check. Is there an issue with the ISO image hosted? I don't see how I can get six consecutive failures any other way.

Have you tried different mirrors or tried a torrent?

---

### Post by pricetech on 2011-03-18
Plus one for both ideas previously mentioned.

Just wanted to recommend though that you opt for 10.04 since it's a LTS and well be supported longer and has had more time to mature.

---

### Post by Dyonas on 2011-03-18
Well now, this is embarrassing.. my memory was faulty, but not the computer kind. I was checking the hash for the alternate download instead of the desktop download. By the time I realised I had the torrent which matched up nicely. Nothing to see here, move along *hides shame*

---

### Post by pricetech on 2011-03-18
Been there, done that, had the red face.

Glad you got it sorted out.

---

