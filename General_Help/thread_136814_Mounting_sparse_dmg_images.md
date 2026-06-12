---
title: "Mounting sparse dmg images"
date: 2006-02-26
forum: General Help
---

### Post by Klin'Targ on 2006-02-26
Is there anyway to mount a sparse .dmg hfs+ disk image on linux?

Normal (non-sparse) disk images mount flawlessly with this method:
```
sudo mount -o loop -t hfsplus test2.dmg testmnt
```

However, sparse disk images give the error (in dmesg) "HFS+-fs: unable to find HFS+ superblock"

Any ideas?

---

### Post by berbs on 2007-08-14
I have a similar problem. The sparse image from a previous backup is also encrypted. Is there a way to mount this image? Thx

---

