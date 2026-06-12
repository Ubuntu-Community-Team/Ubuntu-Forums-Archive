---
title: "Problem with apt-get"
date: 2010-04-05
forum: General Help
---

### Post by moolcool on 2010-04-05
I am running Ubuntu 10.04 and tried getting XFCE with sudo apt-get install xubuntu-desktop, I think it failed half way through and now no matter what I apt-get I get this error:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
When I run sudo dpkg --configure -a I get the following:
Setting up initramfs-tools (0.92bubuntu69) ... update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ... update-initramfs: Generating /boot/initrd.img-2.6.32-17-generic cp: cannot stat `/lib/plymouth/themes/default': No such file or directory grep: /lib/plymouth/themes/default/default.plymouth: No such file or directory cpio: ./lib/plymouth/.so: Cannot stat: No such file or directory update-initramfs: failed for /boot/initrd.img-2.6.32-17-generic

What should I do?

---

### Post by moolcool on 2010-04-05
P.s. sudo apt-get update and sudo apt-get upgrade didn't work either.

---

### Post by djoxyk on 2010-04-05
reboot and try to run what it ask
in terminal
sudo dpkg --configure -a

---

### Post by moolcool on 2010-04-05
Setting up initramfs-tools (0.92bubuntu69) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-17-generic
cp: cannot stat `/lib/plymouth/themes/default': No such file or directory
grep: /lib/plymouth/themes/default/default.plymouth: No such file or directory
cpio: ./lib/plymouth/.so: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.32-17-generic
dpkg: subprocess installed post-installation script returned error exit status 1

---

### Post by djoxyk on 2010-04-05
how it react on this?

sudo apt-get -f install

---

### Post by moolcool on 2010-04-05
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by garvinrick4 on 2010-04-06
Now this is for a partition labeled karmic as an example. Use what ever label your
partition is and use your own partition # I am using sda1 as an example'


"1. - Download/grab a live cd.
2. - Start live cd and when it loads the desktop open a gnome-terminal.
3. - Create these dirs:
sudo mkdir /media/karmic
sudo mkdir /media/karmic/proc /media/karmic/dev /media/karmic/etc
4. - Mount your linux partition (for me sda1):
sudo mount /dev/sda1 /media/karmic
5. - Bind the dirs:
sudo mount -o bind /proc /media/karmic/proc
sudo mount -o bind /dev /media/karmic/dev/
sudo mount -o bind /dev/pts /media/karmic/dev/pts
6. - Copy this file
sudo cp /etc/resolv.conf /media/karmic/etc/resolv.conf
7. - Update your real linux partition with chroot:
sudo chroot /media/karmic apt-get update
8. - Upgrade your real linux partition with chroot:
sudo chroot /media/karmic apt-get dist-upgrade
9. - If you have some broken package:
sudo chroot /media/karmic apt-get -f install
10. - Reboot and  Fixed for me."

---

