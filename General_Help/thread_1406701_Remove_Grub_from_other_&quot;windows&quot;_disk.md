---
title: "Remove Grub from other &quot;windows&quot; disk"
date: 2010-02-14
forum: General Help
---

### Post by Sniperchang on 2010-02-14
Hello,

I have windows XP on one disk, I added another disk and I installed UBuntu 9.10 on it. I wish to tempararly remove the ubuntu disk, however grub cannot load unless that disk is connected. It appears that grub has got to the windows disk and my system was booting from there.

I wish to remove grub from all disks, (or at least the windows disk). I tried removing it from the synaptic package manager, but it's still there (but it looks different, maybe another version loaded or something).

I'd like to just be able to boot from either disk using my bios boot menu.

---

### Post by oldfred on 2010-02-14
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by bruno9779 on 2010-02-14
you can setup grub on the other disk. You are going to need to do this every time you remove the HD where grub is installed.

install grub on the second drive:

```
sudo grub-install /dev/sdb
```
(assuming your second HD is sdb)

if this gives errors:

```
sudo grub-install --recheck /dev/sdb
```

and to finish:
```

sudo update-grub
```

---

### Post by Sniperchang on 2010-02-14
Ok. What if I make sure grub is installed (would that be done the same way?) on the linux disk. Then use oldfred link to restore the windows xp boot on the other disk?

I'm hoping this will allow to load windows bootloader when booting from the "windows" disk, and boot grub (or whatever to be able to boot to ubuntu) when booting form the "linux" disk.

---

### Post by bruno9779 on 2010-02-14
it would work to have 2 separate bootloaders, one per disk, but you would have to unplug the HD you don't use at boot

---

### Post by Sniperchang on 2010-02-14
> **bruno9779 said:**
> it would work to have 2 separate bootloaders, one per disk, but you would have to unplug the HD you don't use at boot

Right. Or use the bios boot menu...

Would what I had suggested do that?

Thanks for the help by the way

---

### Post by oldfred on 2010-02-14
If you set the removable disk with grub as first in your boot order, it will find grub and give you a choice of ubuntu or windows. If not found and you have installed the windows boot loader on the internal then that will boot. No choosing in BIOS required.

---

