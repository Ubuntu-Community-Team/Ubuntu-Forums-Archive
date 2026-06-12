---
title: "Does ubuntu support reading from ISO archives?"
date: 2006-01-21
forum: General Help
---

### Post by hk_2999 on 2006-01-21
You know, the CDROM image.

If it doesn't, what are the external programs I have to get? Thanks.

---

### Post by Dr Gonzo on 2006-01-21
Let's say you have an image called img.iso.  You can mount it like this: ```
mount -o loop -t iso9660 img.iso /mnt/iso
```Obviously, you'll need to be in the directory where the iso is, and /mnt/iso must exist.

Hope that works for you.

---

