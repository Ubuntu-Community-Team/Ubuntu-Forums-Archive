---
title: "problem with sudo dpkg --configure -a"
date: 2010-02-10
forum: General Help
---

### Post by aviramof on 2010-02-10
i have downloaded a few updates and something did go right i tried apt-get and some more things but no luck what can i do to fix it now? 
 
sudo dpkg --configure -a
Setting up initramfs-tools (0.92bubuntu64) ...
update-initramfs: deferring update (trigger activated)
 
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic
cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by aviramof on 2010-02-10
[COLOR=#009900][COLOR=black]i also tried sudo apt-get upgrade and got this[/COLOR]
[COLOR=#009900]update-initramfs: Generating /boot/initrd.img-2.6.32-12-generic[/COLOR]
[COLOR=#009900]cpio: ./lib/udev/firmware.sh: Cannot stat: No such file or directory[/COLOR]
[COLOR=#009900]update-initramfs: failed for /boot/initrd.img-2.6.32-12-generic[/COLOR]
[COLOR=#009900]dpkg: subprocess installed post-installation script returned error exit status 1[/COLOR]
[COLOR=#009900]E: Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]
 
[/COLOR][COLOR=#009900][COLOR=black][/COLOR][/COLOR]

---

### Post by oldos2er on 2010-02-10
Are you running 10.04? If so, please post in [http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

---

