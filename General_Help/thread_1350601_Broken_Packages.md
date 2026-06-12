---
title: "Broken Packages?"
date: 2009-12-09
forum: General Help
---

### Post by Roasted on 2009-12-09
I'm on Jaunty 9.04 64 bit running Kubuntu, and I just upgraded my KDE from 4.2.2 to 4.3.2 using a guide I found online. I had some trouble with the guide, and during the process I had an error with some amd64.deb package within terminal. But it said complete so, whatever, I rebooted.

I came back up and thankfully this time it worked, whereas the last 2 guides I tried made Kubuntu completely bomb when I logged back in. No big deal, I made a backup image prior (ahh, genius!) and I was back in action with 4.2.2 to try again.

So anyway, I'm on 4.3.2 now (which seems much faster than 4.2.2, to be honest) and I wanted to install one of the native window decorators known as "skulpture" which I previously found in add/remove programs.

I fire up add/remove programs and I get an error:



A package dependency could not be found.
More information is available in the detailed report.

Details
There are broken dependecies on your system. Please use an advanced package manage e.g. Synaptic or aptitude to resolve this situation.



oops - what'd I do wrong?


EDIT : 

You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:             
  kstars: Depends: libindi0 (>= 0.6) but it is not going to be installed
  synaptic: Depends: libvte9 (>= 1:0.19.1) but it is not going to be installed
            Depends: scrollkeeper
            Recommends: gksu but it is not going to be installed
            Recommends: libgnome2-perl but it is not going to be installed
            Recommends: software-properties-gtk but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
jason@FOG-Laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11-generic libmaildir4 superkaramba akonadi-kde
  linux-headers-2.6.28-11 libsbigudrv0 kdeartwork-misc indi kode
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libindi0
The following NEW packages will be installed:
  libindi0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
197 not fully installed or removed.
Need to get 0B/712kB of archives.
After this operation, 1864kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 125423 files and directories currently installed.)
Unpacking libindi0 (from .../libindi0_0.6-0ubuntu1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libindi0_0.6-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite `/usr/bin/indiserver', which is also in package indi
Errors were encountered while processing:
 /var/cache/apt/archives/libindi0_0.6-0ubuntu1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jason@FOG-Laptop:~$


So, what's the scoop? Is this to be expected when upgrading KDE within a distro? Is this something everybody sees? Why is it I came across it when I followed the guide to a T? And how do I get this gizmo to work again?

---

### Post by Leppie on 2009-12-09
have you tried synaptic?

---

### Post by MelDJ on 2009-12-09
tried *sudo dpkg* --*configure* -a?

---

### Post by Roasted on 2009-12-10
Someone from IRC helped me out. I forget entirely what I did, some kind of sudo dpkg --remove-force or something like that, THEN I did --configure -a and everything was fine afterwards. Thanks guys!

---

