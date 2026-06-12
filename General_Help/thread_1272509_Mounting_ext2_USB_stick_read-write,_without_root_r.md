---
title: "Mounting ext2 USB stick read-write, without root rights - possible at all?"
date: 2009-09-22
forum: General Help
---

### Post by Lupusceleri on 2009-09-22
Hello folks, a little noobquestion here that I can't seem to find a clear answer on elsewhere.

Is it at all possible to mount an ext2 or ext3 filesystem on an USB-stick, as read-write for the current user without having access to sudo/root or the ability to modify fstab?

I'm asking this because the university PC automounts the USB drive's partitions upon inserting it, however it mounts the ext2 filesystem as root:root while the NTFS chunk of the drive is automounted read-write no problem.

So instead of the automount I'm trying to do it manually, sort of failed so far.

Thank you kindly for the answer,

Martijn.

---

### Post by mrodlaw on 2009-11-19
Hello everybody,

The same happens to me: FAT, NTFS mounts ok with read/write acces but that doesn't happens to EXT2 / EXT3.

Thanks to any suggestion

---

### Post by dcstar on 2009-11-19
> **mrodlaw said:**
> Hello everybody,

The same happens to me: FAT, NTFS mounts ok with read/write acces but that doesn't happens to EXT2 / EXT3.

Thanks to any suggestion

Put in the EXT2/3 formatted device, then open a terminal, find the name of it and then change the rights:
```
ls -al /dev/media
sudo chmod 777 /dev/media/whatever-the-name-is
```
Everyone should have full R/W rights to the root folder whenever/wherever they plug it in (be aware that any folder created inside it will still have user specific security).

---

### Post by mrodlaw on 2009-11-19
Thanks David,

Worked fine; I just needed to add the '-R' to chmod.

Regards!

---

