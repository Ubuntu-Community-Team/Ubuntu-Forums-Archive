---
title: "PLZ help"
date: 2006-06-20
forum: General Help
---

### Post by exiled on 2006-06-20
I setup my graphics card (nvidia) and had to do an md5sum on xorg.conf (?  new to ubuntu sorry) anyways, i screwed up and didn't write down where it stored the backup (or the command to do it) any help here would be much appreciated, right now im using the live cd sine it cant load, but i can get to the console, but no gui

---

### Post by aysiu on 2006-06-20
Let's assume your Ubuntu partition is /dev/hda5 (it could be whatever--check the output of ```
sudo fdisk -l
``` to find out). In that case, we'd ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda5 /recovery
gksudo nautilus
``` Then go to /recovery/etc/X11. You should see the backup somewhere in there.

---

### Post by exiled on 2006-06-20
[QUOTE=aysiu]Let's assume your Ubuntu partition is /dev/hda5 (it could be whatever--check the output of ```
sudo fdisk -l
``` to find out). In that case, we'd ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda5 /recovery
gksudo nautilus
``` Then go to /recovery/etc/X11. You should see the backup somewhere in there.[/QUOTE]


how do i apply the backup?

---

### Post by aysiu on 2006-06-20
```
gksudo nautilus
``` launches the file browser with root privileges. Just delete the xorg.conf file and replace it with the backup copy (probably called something like xorg.conf060620).

---

### Post by exiled on 2006-06-20
i'll give it a go now and let you know how it turns out, thanks alot

---

### Post by exiled on 2006-06-20
ok, from the live cd i can't get to the hdd where i have installed ubuntu.  when i boot all i have is a black screen with text (no gui) but i can access the terminal (black screen with the following text  "user@computer: ") so i can run commands from there but i don't have a gui, how can i load the backup with just a command and no gui? (ie no nautilus....or will nautilus load form there...i dont think it will)

---

### Post by aysiu on 2006-06-20
Instead of ```
gksudo nautilus
``` and browsing to /recovery/etc/X11, just type ```
cd /recovery/etc/X11
ls
```

Why is the live CD only text with no graphics?
Can't you just boot into recovery mode then without the live CD? It'd be virtually the same thing (except probably faster).

---

### Post by exiled on 2006-06-20
got the problem fixed, thanks for your help

---

