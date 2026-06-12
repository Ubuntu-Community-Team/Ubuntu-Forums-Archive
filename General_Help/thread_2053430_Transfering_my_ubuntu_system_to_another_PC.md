---
title: "Transfering my ubuntu system to another PC"
date: 2012-09-05
forum: General Help
---

### Post by Howie Williams on 2012-09-05
I have Ubuntu 12.04 installed on my laptop and the laptop needs to be returned to supplier as there is a problem with battery life.
1. How do I back up and then install my system to any new Laptop I may purchase without losing all my settings and data,emails,addresses, photos,music etc.? (I have an external HDD).

2. How do I then securely wipe my old laptop of all data so I return a clean laptop to the supplier?

---

### Post by SlugSlug on 2012-09-05
I would personally copy over /home and /etc not much else. Then do a full install on new lappy and copy back your files from /home

and restore /etc/configs as and when you need them.

Or you could clone the disk with 'dd' or clonezilla

but I'd like I said, I'd pick first option

---

### Post by Howie Williams on 2012-09-05
Thanks SlugSlug will give that a whirl. Any thoughts on wipeing the old laptop?

---

### Post by bobarry on 2012-09-05
Thanks for this tip!  I've had it with Unity (tried it twice) and am going to try Linux Mint MATE.
I'm running XP 'from now on', and want to do the same with Gnome.
This old dog is TIRED of trying new tricks (that stink).  :)

I tried Mint on one computer (with XP) and it dorked up grub boot. Trying to find a way to fix it.

Bo

---

### Post by lukeiamyourfather on 2012-09-05
> **Howie Williams said:**
> Thanks SlugSlug will give that a whirl. Any thoughts on wipeing the old laptop?

The command shred can be used on block devices (/sda for example). Be careful which device is selected because there's no turning back. Read the manual first and be sure you understand what it says (man shred).

---

### Post by SlugSlug on 2012-09-05
either 'shred' 'dd' or 'boot n nuke'

---

### Post by MARP1961 on 2012-09-05
DBAN (Darik's Boot and Nuke) will do the job of cleaning your hard drive. Just burn the disk and boot with it. Follow instructions and be careful to back up any files before you start:
[http://www.dban.org/download](http://www.dban.org/download)

---

### Post by oldfred on 2012-09-05
If you have installed a lot of applications, you can export a text list and use that to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

More detail on /etc files to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)

[https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync)
Files to include or exclude from full system backup. Post #7
[http://ubuntuforums.org/showthread.php?t=1903085](http://ubuntuforums.org/showthread.php?t=1903085)

Some files to exclude from /home:
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
/home/*/.cache
/home/*/.dbus
/home/*/.dropbox
/home/*/.gvfs
/home/*/.local/share/Trash
/home/*/.mozilla/firefox/*.default/Cache/**
/home/*/.qt
/home/*/.thumbnails
/home/*/Examples
/home/.ecryptfs
/home/lost+found

---

### Post by cmcanulty on 2012-09-05
try gnome classic before mint. I learned if you switch to mint it isn't easy to switch back.

---

