---
title: "Installing Ubuntu to an existing partition?"
date: 2011-04-26
forum: General Help
---

### Post by Asmy on 2011-04-26
Right, so I sudo apt-get uninstalled a bunch of stuff I shouldn't have. Now my Ubuntu Partition doesn't boot up correctly, something about the graphic system, video system, etc. all being unconfigured. (I'll get the exact error later.) All I can use is the command line.

So the main problem is: can I install Ubuntu over my old Ubuntu partition without messing up rebooting/GRUB and all that?

---

### Post by lithopsian on 2011-04-26
You can install a new Ubuntu over the old one.  That is easy.

Without messing up Grub?  Is there something special about your Grub that could be messed up?  By default the installation process will install Grub for you and any bootable partitions will be shown.  I suppose you could skip this but why bother?

---

### Post by Paddy Landau on 2011-04-26
If you install over your existing partition, it will recreate grub for you. Don't worry about that.

What you must worry about is your data. *Do you have backups?*

If you do not, you will need to boot from your Live CD and make a backup first.

---

### Post by oldfred on 2011-04-26
If you can boot to a command line you should be able to recover everything. Normally run from chroot, but if command line you do not need the chroot from a liveCD. 

#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
Commands once in chroot:
if not chroot use: sudo -i
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
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
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

---

