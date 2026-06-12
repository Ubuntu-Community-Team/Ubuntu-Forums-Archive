---
title: "Update without updating kernel?"
date: 2011-04-21
forum: General Help
---

### Post by garrett228 on 2011-04-21
I have a 3dsp pci wifi card, and the last kernel it supports is Ubuntu 10.04 2.6.32-(21-24) I want to update but dont want to accidentally update the kernel. Any advice guys?

Sorry for this post I didnt spell the title of the first correctly, im a little f'd right now lol.

---

### Post by spikoley on 2011-04-22
You can run the updates and when you reboot select the kernel you want.  Next edit which kernel will be used on boot.  Edit the grub file to boot the correct kernel.

```
gksudo gedit /etc/default/grub
```

This [guide]("https://help.ubuntu.com/community/Grub2") should help you with editing the options, but if you have any questions let us know.

After you make the changes make sure you run update-grub.

```
sudo update-grub
```

---

### Post by Jechem on 2011-04-22
You can choose which updates you need in Update Manager. You can uncheck the linux kernel updates if you don't want them.

---

