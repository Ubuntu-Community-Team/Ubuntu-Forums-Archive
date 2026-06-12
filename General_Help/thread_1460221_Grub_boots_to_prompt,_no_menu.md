---
title: "Grub boots to prompt, no menu"
date: 2010-04-22
forum: General Help
---

### Post by Facetious Falcon on 2010-04-22
I've been having a bit of trouble recently with Grub. I've recently installed Grub onto a windows HD because the Ubuntu HD's mbr is acting strange. It's worked to a certain extent - I can at least get a grub prompt but that's it. For some reason there's no grub menu, is there any way to automatically fill the menu or do I need to copy the Kernels to the /boot/ folder?

Help is greatly appreciated, thanks.

---

### Post by Facetious Falcon on 2010-04-22
Also I'm thinking of reinstalling everything however I don't have permission to grab some files off the HD from the live CD. Is there a way of logging in to your user account on a HD from the live CD so I can grab some files and reinstall?

---

### Post by psycho5 on 2010-04-22
You can grab your files by inserting the live cd and load up the desktop, 

hit alt+f2 and type "gnome-terminal"

then just mount your disk to grab the files


sudo mount /dev/sda /mnt

if /dev/sda is your disk in question.

---

### Post by ba_saish on 2010-04-23
you could try using the super grub [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

