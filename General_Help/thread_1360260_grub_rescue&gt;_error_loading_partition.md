---
title: "grub rescue&gt; :error loading partition"
date: 2009-12-20
forum: General Help
---

### Post by mIXpRo on 2009-12-20
hii there ,

my friend has ubuntu 9.10 , but in his laptop he installed also vista.
mistakenly his little sister when she booted the laptop she entered at the grub the windows recovery .
she didn't know and god knows what she did , but after that when rebooting ,
at the grub window it says grub rescue >
                                              error : partition not found or something like that .

now i installed the ubuntu on a usb stick and booted the laptop from it ,
and it worked fine you can enter the ubuntu , but if i remove the usb 
the grub error come back again .

any solutions pls .

---

### Post by mIXpRo on 2009-12-20
is this means nobody knows ?
try googling it ?

---

### Post by Leppie on 2009-12-20
try this:
```
$sudo mount /dev/sdXY /mnt  ##replace /dev/sdXY with the linux partition
$sudo grub-install --root-directory=/mnt /dev/sdX  ##replace sdX with the disk he wants to boot off (usually sda)
```

---

