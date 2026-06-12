---
title: "boot menu problems"
date: 2010-02-15
forum: General Help
---

### Post by wanglemoose on 2010-02-15
Hi all im running a duel boot system with windows xp pro on my old hard drive and ubuntu 9.10 amd64 on the new hard drive. I have it set so that at start up you choose which os to boot with ubuntu as the default. my problem is that every version update ends up on the boot menu. how do i clean this so that i only have one ubuntu and windows to choose from.
cheers mick.

[IMG]http://i964.photobucket.com/albums/ae123/wanglemoose44/Photo0193-1.jpg[/IMG]

---

### Post by bwhite82 on 2010-02-15
I always recommend having not only the newest kernel installed but a "known-good" older as well. Other than that, you can get rid of the rest in Synaptic. Just search for "linux", then click on the installed sort column and remove the old "linux-image-"'s and "linux-headers-" etc.

---

### Post by Megafag on 2010-02-15
> **Soldierboy said:**
> I always recommend having not only the newest kernel installed but a "known-good" older as well. Other than that, you can get rid of the rest in Synaptic. Just search for "linux", then click on the installed sort column and remove the old "linux-image-"'s and "linux-headers-" etc.

Alternatively, if you dont want to accidentally make your computer un-bootable you can simply take the other ubuntu entries out of your grub list.

```
sudo gedit /boot/grub/menu.lst
```

but i think that will only work if you are using a version of ubuntu before karmic.

---

