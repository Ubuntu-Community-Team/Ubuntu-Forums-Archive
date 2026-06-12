---
title: "lost power in middle of distro upgrade...no boot"
date: 2012-01-27
forum: General Help
---

### Post by tatmark1 on 2012-01-27
i lost power in the middle of a distro upgrade from 10.04 to 10.10
now i can not boot. please help...

---

### Post by MARP1961 on 2012-01-27
Did you back up your data files beforehand? If you did, it would probably be easiest just to get a CD of the Ubuntu version you want and do a fresh install. Online distro-upgrades can go wrong as you have found out. Do you have a 10.04 disk still? If so then boot the computer with the disk and select 'Try Ubuntu'. Launch **gparted** and see if anything remains of your old installation.

---

### Post by tatmark1 on 2012-01-27
i have the cd and yes the old is still there

---

### Post by MARP1961 on 2012-01-27
Do you just have a single partition with Ubuntu and all your data on (apart from a small Swap partition)?

---

### Post by tatmark1 on 2012-01-27
yes sir

---

### Post by tatmark1 on 2012-01-27
i had the upgrade installing and some idiot hit the pole and took out the elec...

---

### Post by MARP1961 on 2012-01-27
OK, so doing a fresh install of 10.04 by erasing your previous install would be easy **but you will lose your data files**. If this doesn't matter (because they're not important or you saved them on CD, flash drive or an external hard drive) then go ahead and reinstall the old 10.04, and if you wish just go ahead and do your distro upgrade to 10.10 again. This time, don't rely on battery power.

If you need the data files, **then do not reinstall** until we have asked someone else on this forum for their more expert help. Anyone?

---

### Post by tatmark1 on 2012-01-27
yeah i prefer not to reinstall

---

### Post by MARP1961 on 2012-01-27
Sorry, I'm now in territory where I would need to ask for help! Can someone else please take over and offer help for this failed upgrade??

---

### Post by oldfred on 2012-01-27
You can try to chroot into your system and run the upgrade again. Often that works, but no guarantees.

Instructions on chroot - you many not need the full uninstall/reinstall of grub.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

Then when in chroot also run all these commands.

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
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

---

### Post by tatmark1 on 2012-01-27
i must not know what my hard drive is named as i keep getting error that it cant find it

---

### Post by tatmark1 on 2012-01-27
ok i found that out, i ran sudo mount /dev/sda1/mnt and i get  a cant find error? i just ran fdisk and thats what i had pop up was sda1

---

### Post by oldfred on 2012-01-27
Best if from liveCD you copy commands. Even spaces are important.

sudo mount /dev/sda1/mnt
#should be:
sudo mount /dev/sda[COLOR=Red]1 /[/COLOR]mnt

Note space between 1 & /. Also if you have mounted sda1 by looking at it with Nautilus you will have to unmount it first.

---

