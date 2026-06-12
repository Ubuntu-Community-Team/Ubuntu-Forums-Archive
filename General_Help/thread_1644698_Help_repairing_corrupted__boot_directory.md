---
title: "Help repairing corrupted  /boot directory"
date: 2010-12-13
forum: General Help
---

### Post by pcolamar on 2010-12-13
Hi there,
 I have accidentally deleted all the files in my /boot directory of my Lynx 10.04 64bits installation.

Is there any way I can manually reinstall them ?
I need just to reinstall a kernel so I can reboot

Can I manually copy them from somewhere (CD, etc.)

Thanks

---

### Post by garvinrick4 on 2010-12-13
##If you copied one from same version Live CD you just might have to chroot into / and update-grub.
Open a terminal: (this is using sda5 as file system (use your own).
## Have never deleted my boot files and or kernels before so this is best I got, good luck.
```

[CODE]sudo mount /dev/sda5 /mnt
``````
sudo mount -o bind /dev /mnt/dev
``````
sudo mount -o bind /dev/pts /mnt/dev/pts
``````
sudo mount -o bind /proc /mnt/proc
``````
sudo mount -o bind /sys /mnt /sys
``````
sudo chroot /mnt
``````
update-grub
``````
exit
``````
sudo umount /mnt/dev/pts
``````
sudo umount /mnt/dev
``````
sudo umount /mnt/proc
``````
sudo umount /mnt/sys
``````
sudo umount /mnt
``````
sudo reboot
```
[/code]## Let me know if had any success. I kind of wonder what you are missing. If just the boot files you can remove and reinstall grub while in chroot.
Hopefully you just threw away config files.

---

### Post by pcolamar on 2010-12-14
garvinrick4,
  I did a kind of rm *.* in the /boot directory, it's not the grub config that is gone but all the files that where in the directory.
I guess I have to find them somewhere, copy them in /boot and then do your "magic"  
The problem is that, so far  I do not seem to find them in the CD

---

### Post by oldfred on 2010-12-14
I think garvinrick4 had the right idea to chroot, but I think since /boot is a separate partition you have to also mount that as part of the chroot as that is where you want the new grub & kernels installed to. Change sda5 to your / partition and sda2 to your /boot partition.

sudo -i
mount /dev/sda5 /mnt
#if /boot
mount /dev/sda2 /mnt/boot

for i in dev proc sys usr; do mount --bind /$i /mnt/$i; done
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf #(may or may not be necessary to establish an internet connection)
sudo chroot  /mnt

#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

#When done:
exit
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/sys
sudo umount /mnt/usr
sudo umount /mnt/boot
sudo umount /mnt

---

### Post by pcolamar on 2010-12-16
Done (and Solved!)
I have done a mix of your proposed solutions.
I had forgotten to say I have 2 Ubuntu's distro's installed on the same HDD, so :
1) I have copied from the /boot of the LiveCD of the corrupted version (Lynx 10.04) the files initrd and vmlinuz.

2) update-grub, so I got a new entry line in the grub menu (that of course was in the /boot/grub of the non corrupted installation and I hadn't realized immediatly)

3) Booted up the Lynx 10.4 with the standard kernel I copied from the livecd

4) Immediatly after I accepted all the updates available (350 MB !) and , of course, one of them was the  last Lynx kernel.

Back in business

Thanks to all for you help
Palmer

---

