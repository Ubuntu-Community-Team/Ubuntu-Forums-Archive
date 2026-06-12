---
title: "Universal usb installer with alternate install disk"
date: 2011-10-30
forum: General Help
---

### Post by halitus87 on 2011-10-30
Hi,

I am having an issue getting a alternate installer usb stick.

I have tried with universal usb installer but when booting it comes to the normal boot menu asking if you want to try ubuntu on this pc and below that the install ubuntu to hard drive. However non of these selections do anything. booting the iso from a cd or in a VMachine also doesn't do this.

Any ideas?

Thanks
Halitus.

---

### Post by zvacet on 2011-10-30
Did you checked if iso is O.K.?I mean [md5sum.]("https://help.ubuntu.com/community/HowToMD5SUM") You can try install with unetbootin and see if you will be more lucky that way.

---

### Post by A_Swissionary on 2011-10-30
Hi there,
I just had the same issue.
Seems like the Universal USB Installer creates the "Live CD" txt.cfg file when it should do the "Alternate CD" one.

You can therefore either try to create your own txt.cfg file (take the one found on your usb stick in /syslinux as a template); The parameters you SHOULD enter are stored in the /boot/grub/grub.cfg file.
Note however: You can't just copy + Paste them, as both files have different syntaxes.

To make it easier: Here's my not fully tested version of txt.cfg. It did allow me to initiate the Alternate Text Installation:

```

default install
label install
  menu label ^Install Ubuntu
  kernel /install/vmlinuz
  append noprompt cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed quiet initrd=/install/initrd.gz --
label expert
  menu label ^Expert Install
  kernel /install/vmlinuz
  append cdrom-detect/try-usb=true file=/cdrom/preseed/ubuntu.seed priority=low initrd=/install/initrd.gz --
label rescue
  menu label ^Rescue broken system
  kernel /install/vmlinuz
  append noprompt cdrom-detect/try-usb=true rescue/enable=true --

```hth!
Best,
René

---

### Post by halitus87 on 2011-11-05
Hi A_Swissionary and zvacet.

Firstly yes the md5 checks out for the iso. A_swissionary thanks heaps that seams to have put me on the right path. I couldnt find the txt.cfg under /boot/grub at all on either the iso or the usb stick. But I did find it in /isolinux so i copied and pasted the version from the iso to the usb stick (which was different, It mentioned try ubuntu etc.)

from here the usb stick booted and allowed me to start an install. However it wouldn't allow me to press f6 and add any extra boot options. I am trying to install an CLI version only. This is for a NAS/server but the server version of ubuntu seams to have issues creating arrays were the regular version doesn't. So im trying a normal install without the desktop stuff.

I might just edit the txt.cfg file to have an expert install option and do things that way.

Or perhaps copying the all files and folders from the iso to the usb will work now that its been set up to boot properly.

Thanks for the help and sorry for the rushed reply.

Halitus

---

