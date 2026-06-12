---
title: "Rescue System"
date: 2010-08-04
forum: General Help
---

### Post by Psychic Saw on 2010-08-04
Hi,

I was checking out gnome 3 using [FONT=monospace]r[/FONT]icotz/testing PPA, after I was finished I remove the PPA and now the system can't load gnome anymore. I'm assuming what happened was I stupidly removed the gnome interface or something along those lines but I don't have enough experience to know what I did wrong.

I tried starting up the system in recovery mode from the grub list to reinstall the missing packages but I can't view the information on the screen because the nVidia driver garble up the boot screen.

Could anyone suggest a fix?

---

### Post by oldfred on 2010-08-04
If you add the nomodeset in place of quiet spash or add it to the recovery kernel boot line can you get to a workable command line?

If not, can you chroot into your system from a liveCD. It may also require the nomodeset and/or the (temporary) install of the nvidia driver to the liveCD.

Commands once in command line or chroot:
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

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

From above line to kansasnoob's - change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic may also be required as part of chroot:
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

---

### Post by Psychic Saw on 2010-08-04
Thanks for the help, but I couldn't wait around so I just recovered the files and formatted the machine. It only took an hours. :)

---

