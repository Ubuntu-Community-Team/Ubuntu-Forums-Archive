---
title: "Cleaning up dead enries in Grub 2 menu"
date: 2010-07-18
forum: General Help
---

### Post by HandLotion on 2010-07-18
I have two leftover entries in the Grub2 menu  after running update-grub. One is leftover from an Ubuntu installation under Windows 7 referring to a Vista boot.  Never had Vista on my system, and if I were to select this option it will lock my computer. Same deal with an older Jaunty boot option - as I have identical worded options one good and one dead option.

If I have to live with these two dead selections on my Grub2 menu I will. But I'd rather get rid of them. I don't want to use an old tool for Grub editing that is no longer workable for Grub 2.

---

### Post by techunit on 2010-07-18
boot from your Ubuntu Live CD and type the following code in to the terminal...

```
sudo update-grub
```

---

### Post by HandLotion on 2010-07-18
> **techunit said:**
> boot from your Ubuntu Live CD and type the following code in to the terminal...

```
sudo update-grub
```

That doesn't fix anything.  Dead references remain on Grub 2 boot menu.

I assume the entries labeled as .old are the problem, but how to get rid of them?

=================== sda5: Location of files loaded by Grub: ===================


  79.1GB: boot/grub/core.img
  89.8GB: boot/grub/grub.cfg
  79.8GB: boot/initrd.img-2.6.32-21-generic
  80.0GB: boot/initrd.img-2.6.32-23-generic
  79.8GB: boot/vmlinuz-2.6.32-21-generic
  79.2GB: boot/vmlinuz-2.6.32-23-generic
  80.0GB: initrd.img
  79.8GB: initrd.img.old
  79.2GB: vmlinuz
  79.8GB: vmlinuz.old

---

### Post by HandLotion on 2010-07-24
I removed the dead entries from the grub.cfg file. As long as I don't run update-grub again the grub menu will remain correct. Not an eloquent solution, but it's the best I can do unless I can prevent the os-prober from picking up dead O/S info.

---

### Post by drs305 on 2010-07-24
HandLotion,

Editing the grub.cfg isn't the best solution, as you know. Grub is updated whenever a new kernel is introduce, the grub package it updated, or as you know, when you run "update-grub".

It sounds like the old menu items are being found by Grub2 in an old grub.cfg or menu.lst file, or it's finding old kernels elsewhere on your machine.

For a non-elegant solution (but better than the one you are currently using), if you don't have another OS on your computer, remove the executable bit from /etc/grub.d/30_os-prober. This will prevent Grub2 from searching the rest of your machine for other OS's. You can remove the bit by running a file browser as root, or merely run this command:
```
sudo chmod -x /etc/grub.d/30_os-prober && sudo update-grub
```

The other way is to find old grub.cfg and menu.lst files in the /boot/grub folder of your old Ubuntu installs, old kernels in the other partition's /boot folder, etc. You can see where these files are being found by opening your (old/unmodified) /boot/grub/grub.cfg file and seeing where the menu item points. They are most likely in the # 30_os-prober section of the file. Then go there and remove the 'offending' items. Once you have removed the files, rerun "sudo update-grub".

---

