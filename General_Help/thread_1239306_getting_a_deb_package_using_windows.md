---
title: "getting a deb package using windows"
date: 2009-08-13
forum: General Help
---

### Post by chris1950 on 2009-08-13
I used apt-get install linux-header-2.6.28-14-server. After completed I lost my broadcom b43 wireless driver and system sound driver as well as my lan. Can I uninstall this and get everything back or is there a back up file I can use to restore?
How can I download linux-header-2.6.28-13.45_all.deb using my windows PC so I can save it to a usb disk and then install it on my laptop?

---

### Post by spvo on 2009-08-13
I'm not sure about the first part of your question, but you can download the deb package from windows easily enough.  Just select the package you need in synaptic and generate a package download script (in the file menu).  Then look at the script and you'll be able to see the actual location for the package.  EG: [http://us.archive.ubuntu.com/ubuntu/pool/../something.deb](http://us.archive.ubuntu.com/ubuntu/pool/../something.deb)

---

### Post by Arand on 2009-08-13
Database of all ubuntu packages are here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
 -Arand

---

### Post by 3rdalbum on 2009-08-13
The older kernel should still be on your hard disk and in your GRUB boot menu.

If you manually compiled the Broadcom driver, you need to compile it again after every kernel upgrade. Same for any non-Ubuntu drivers.

---

### Post by chris1950 on 2009-08-13
I downloaded linux-headers-lbm-2.28-13-generic_2.6.28-13.14amd64.deb and linux-image-2.6.28-14.47_amd64.deb. Which do I install first?

---

### Post by chris1950 on 2009-08-13
No the orignal install found all the drivers needed but I did have to go to device manager to activate the wireless broadcom B43 driver.

---

