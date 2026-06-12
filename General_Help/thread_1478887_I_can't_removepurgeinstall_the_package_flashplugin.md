---
title: "I can't remove/purge/install the package flashplugin-nonfree"
date: 2010-05-10
forum: General Help
---

### Post by mikekgr on 2010-05-10
Dear Friends,
I faced on these days a very nasty problem, during the upgrading of my system... something bad happened and I can not remove, purge, install, reinstall the package flashplugin-nonfree no matter what tries I did till now. To see my tries please read bellow.
Do any of you have any advanced advice how can solve this BIG problem that occurs to me??

Best Regards,
Mike Kranidis

====================== start of my tries to solve the problem ======================

root@intra-micro:/home/mikek# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
flashplugin-installer flashplugin-nonfree
Suggested packages:
ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
flashplugin-installer
The following packages will be upgraded:
flashplugin-nonfree
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/21.4kB of archives.
After this operation, 61.4kB of additional disk space will be used.
Do you want to continue [Y/n]?
Preconfiguring packages ...
dpkg: error processing flashplugin-nonfree (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
flashplugin-nonfree
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)


root@intra-micro:/home/mikek# dpkg --purge --force-all flashplugin-nonfree
dpkg: warning: overriding problem because --force enabled:
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
(Reading database ... 180367 files and directories currently installed.)
Removing flashplugin-nonfree ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing flashplugin-nonfree (--purge):
subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
flashplugin-nonfree

root@intra-micro:/home/mikek# apt-get --reinstall install flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
flashplugin-nonfree: Depends: flashplugin-installer but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@intra-micro:/home/mikek#

====================== stop of my tries to solve the problem ======================

---

### Post by philinux on 2010-05-10
Try these one by one.

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
sudo apt-get remove -y --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree
```

---

### Post by mikekgr on 2010-05-10
Dear philinux, thanks a lot for your reply.
Finally the solution was in this link [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475) under the title "Upgrade 8.04 -> 10.04 can break apt-get.
The package flashplugin-nonfree has been problematic when upgrading 8.04 -> 10.04 and breaks apt-get;"

I follow your steps enlisted there and I am healthy again

P.S. your steps provided here in these thread did not work

Best Regards,
Mike Kranidis

---

### Post by philinux on 2010-05-10
Doh! Slaps forehead.

---

