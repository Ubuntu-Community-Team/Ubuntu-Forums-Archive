---
title: "GRUB on MBR"
date: 2010-04-24
forum: General Help
---

### Post by salvachn on 2010-04-24
Hi. I have Fedora 12 and Ubuntu 10.04 installed on my laptop. I prefer the older GRUB, so I preferred not to install GRUB2 to MBR while installing Lucid. My doubt is, if I update the grub-pc package, will it overwrite Fedora's GRUB?

---

### Post by The Thunder Chimp on 2010-04-24
I don't quite understand what you mean, but if you plan to get Lucid from a previous version of Ubuntu (such as Karmic) then you will keep the old grub.

---

### Post by fuzzyworbles on 2010-04-24
just tell grub to install to the device that has ubuntu's / or /boot partition instead of the mbr (or if during installation, don't install grub at all; click advanced after you select your partitions during installation)

---

### Post by salvachn on 2010-04-24
My situation is:

I've got Fedora 12 and Lucid installed already, and I use Fedora's grub.  If I update Lucid, will the grub-pc package install GRUB 2 to the MBR. I  found out that it asks one to select the device to write the bootloader  to. If I choose none, then all is well and  get to use my older grub.

Thanks. :-)

---

### Post by The Thunder Chimp on 2010-04-25
> **salvachn said:**
> My situation is:

I've got Fedora 12 and Lucid installed already, and I use Fedora's grub.  If I update Lucid, will the grub-pc package install GRUB 2 to the MBR. I  found out that it asks one to select the device to write the bootloader  to. If I choose none, then all is well and  get to use my older grub.

Thanks. :-)


For a clean install, you will probably lose your old grub. For an update however, I'm 99% sure that you won't, and that you'll keep the old grub.

---

### Post by fuzzyworbles on 2010-04-25
i wonder if it's possible to uninstall grub from ubuntu completely and just rely on fedora's. i don't know if this is possible and i don't know how fedora's grub works, but if it's anything like old grub in ubuntu, you can just edit it by hand and fedora's updates won't effect it. if this chain of suppositions is correct, then subsequent ubuntu updates won't alter grub2 because there'd be nothing to alter.

just a thought.

---

### Post by salvachn on 2010-04-29
Exactly what I did. Using Fedora's GRUB which I can edit by hand, and since Ubuntu's GRUB2 has shortcuts to the latest vmlinuz and initrd.img on the root directory, I needed to edit the file only once. I did a fresh Lucid install, and chose not to install the bootloader at the last stage.

---

