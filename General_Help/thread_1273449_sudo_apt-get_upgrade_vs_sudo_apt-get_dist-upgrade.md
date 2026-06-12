---
title: "sudo apt-get upgrade vs sudo apt-get dist-upgrade"
date: 2009-09-23
forum: General Help
---

### Post by dj-toonz on 2009-09-23
Hi all, what's the difference between each of the following

sudo apt-get upgrade

sudo apt-get dist-upgrade

when I goto do a upgrade, i.e after using the open office.org scribblers PPA or even just a do a normal upgrade, it says i.e for example 4 to be installed 12 to be upgraded 0 to be removed & 23 to be kept back & then the upgrade fails.  the only way I can do system updates is by using the sudo apt-get dist-upgrade command for everything to play nicely. Why is that & what's the difference between each og the above commands?

---

### Post by NoaHall on 2009-09-23
sudo apt-get upgrade -> Upgrades the applications and the system parts
dist upgrade -> Completely upgrades everything to the latest distro version released.

---

### Post by lykwydchykyn on 2009-09-23
IME, a regular "upgrade" will not upgrade a package if doing so requires the installation of new packages or the removal of currently installed packages (due to dependency/conflict changes usually).

"dist-upgrade" will do installation/removal if necessary.

[quote=apt-get man page]
       upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in
           /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; under no circumstances are
           currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages
           that cannot be upgraded without changing the install status of another package will be left at their current version. An update must be
           performed first so that apt-get knows that new versions of packages are available.


       dist-upgrade
           dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of
           packages; apt-get has a "smart" conflict resolution system, and it will attempt to upgrade the most important packages at the expense of less
           important ones if necessary. So, dist-upgrade command may remove some packages. The /etc/apt/sources.list file contains a list of locations
           from which to retrieve desired package files. See also apt_preferences(5) for a mechanism for overriding the general settings for individual
           packages.

[/quote]

---

### Post by lykwydchykyn on 2009-09-23
> **NoaHall said:**
> sudo apt-get upgrade -> Upgrades the applications and the system parts
dist upgrade -> Completely upgrades everything to the latest distro version released.

This is not correct.

---

### Post by NoaHall on 2009-09-23
Oh sorry, I read it wrong. 
dist-upgrade will also install extra packages that a new package needs, so you can have the very latest things, upgrade will only update the parts of the software, and not to the very latest version if extra packages are needed.

---

