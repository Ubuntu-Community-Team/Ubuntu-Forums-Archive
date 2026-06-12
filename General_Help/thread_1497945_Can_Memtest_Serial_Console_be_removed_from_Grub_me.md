---
title: "Can Memtest Serial Console be removed from Grub menu?"
date: 2010-05-31
forum: General Help
---

### Post by oxf on 2010-05-31
Hi,

On the Grub menu there is the option **memtest86+, serial console 115200 **which I believe is for remote access. Since I dont have/use Remote Access can Serial Console be removed?[B]   

Thanks

[/B]

---

### Post by ryan858 on 2010-05-31
Yep. You're using grub2 right? Just remove the entry from /boot/grub/grub.cfg, near the bottom of the file... it starts with menuentry and ends with }

This would be undone once you ran grub-update though, since it parses other files and writes grub.cfg based on those... There is a way to remove memtest from /etc/grub.d/os-prober, or similar, but I can't remember how... Maybe someone else can explain it.

Right way = edit /etc/grub.d/* and /etc/default/grub and use grub-update
Easy way = edit /boot/grub/grub.cfg and don't use grub-update

I perfer the easy way, cause I know I won't mess anything up, and I think that the .cfg is actually much easier to read. (well, without all the comments anyway) But I do know my way around shell scripts quite well. /etc/default/grub and /etc/grub.d/40_custom would probably be easier if you don't like scripting/coding.

---

### Post by oxf on 2010-05-31
> **ryan858 said:**
> Yep. You're using grub2 right? Just remove the entry from /boot/grub/grub.cfg, near the bottom of the file... it starts with menuentry and ends with }

This would be undone once you ran grub-update though, since it parses other files and writes grub.cfg based on those... There is a way to remove memtest from /etc/grub.d/os-prober, or similar, but I can't remember how... Maybe someone else can explain it.

Right way = edit /etc/grub.d/* and /etc/default/grub and use grub-update
Easy way = edit /boot/grub/grub.cfg and don't use grub-update

I perfer the easy way, cause I know I won't mess anything up, and I think that the .cfg is actually much easier to read. (well, without all the comments anyway) But I do know my way around shell scripts quite well. /etc/default/grub and /etc/grub.d/40_custom would probably be easier if you don't like scripting/coding.

Yes I'm using Grub2. 

I'm a bit confused. Is Serial Console actually a seperate application as such? and can it be purged. or is it part of the regular Memtest?

---

