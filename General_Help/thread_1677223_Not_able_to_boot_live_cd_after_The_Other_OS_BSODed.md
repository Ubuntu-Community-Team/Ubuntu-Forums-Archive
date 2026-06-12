---
title: "Not able to boot live cd after The Other OS BSODed"
date: 2011-01-28
forum: General Help
---

### Post by jvacek996 on 2011-01-28
I am trying to install Ubuntu on my sister's computer after her Windows BSODed a few times and so I offered her a "failback" system.
The problem is however that the live cd gives a few errors like "cannot mount sth sth sth" (will edit a bit later on after i get another computer to work)
Is it possible that this problem might relate to some Windows BSODs that she experienced earlier on?
Sorry for the lack of details, I'll steal the thing from her and post more accurate details within a split of a second.

---

### Post by TeoBigusGeekus on 2011-01-28
Check the cd for errors.
If the cd is ok, perhaps your sister's pc has a hardware error (dying hd for example) and therefore the BSODs.

---

### Post by jvacek996 on 2011-01-28
> **TeoBigusGeekus said:**
> Check the cd for errors.
If the cd is ok, perhaps your sister's pc has a hardware error (dying hd for example) and therefore the BSODs.
I succesfully installed Ubuntu on another PC with it AFTER I tried to do it on this one. i even tried to install an amd64 version just because my sisteer's pc is capable of it and it gave the same error. but what you sufggest is a hardware issue? Thanks
I'll give more of the info as promised. just hold on :P

---

### Post by jvacek996 on 2011-01-28
ok so here is an identical copz of what it threw up on me.
> (initramfs) mount: mounting /dev/loop0 on //fileszstem.squashfs failed: Inout/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashf) on //fileszstem.squashf
udevd[91]: worker [278] unexpectedly returned with status 0x0100

udevd[91]: worker [278] failed while handling '/devices/virtual/block/loop0'it stil didn't give me the nitramfs shell so i guess something is still going on. hope this helps anyone who is willing to help me. thanks in advance

---

### Post by lykwydchykyn on 2011-01-28
I'd say either her optical drive or RAM is faulty.  See if you can get memtest to run from the CD.

---

### Post by TeoBigusGeekus on 2011-01-28
Perhaps [this]("http://ubuntuforums.org/showthread.php?t=1556602&page=3")?

---

