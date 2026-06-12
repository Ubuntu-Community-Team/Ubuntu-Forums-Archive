---
title: "Synaptic Package manager and Updater problem!"
date: 2011-05-03
forum: General Help
---

### Post by ph3nomX on 2011-05-03
It was everything ok untill this started to show up when i wanted to install additional language keyboard setup:

-----this is on synaptich package manager-------
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

the same problem also shows on update manager and Synaptic Package manager.

I have ubuntu 11.04 -32 fresh install with 4 gigs of swap memory.

My laptop configuration is toshiba satelite i5 procesor 4 gigs ram 500 hdd and dual but with windows 7 via grub.

*i had 10.10 installed and it worked perfectly on this laptop....
ty for help

---

### Post by ph3nomX on 2011-05-03
Solved the problem with this:

sudo rm /var/lib/apt/lists/* -vf
 sudo apt-get update

u can close the thread now

---

