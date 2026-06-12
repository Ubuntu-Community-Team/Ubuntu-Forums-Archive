---
title: "Installing Package From LiveCD"
date: 2009-12-02
forum: General Help
---

### Post by hwttdz on 2009-12-02
I would like to install a package from booting with the liveCD (namely the network manager).  The idea was to mount my root partition and then use a chroot and then apt-get install however this doesn't seem to be working out.  I'm getting a "chroot: cannot run command '/bin/bash': No such file or directory".  Let me know if you can think of an easier way of installing or if you know what's going wrong with what I'm trying to do.

---

### Post by MelDJ on 2009-12-02
see: [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by hwttdz on 2009-12-02
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-urwid wine-gecko wine1.2 ttf-symbol-replacement wine1.2-gecko
  ttf-tahoma-replacement winbind
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  network-manager-gnome
The following NEW packages will be installed:
  network-manager network-manager-gnome
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/823kB of archives.
After this operation, 7,274kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err file: karmic/main network-manager 0.8~a~git.20091013t193206.679d548-0ubuntu1
  File not found
Failed to fetch file:///media/sda1/repo/pool/main/n/network-manager/network-manager_0.8~a~git.20091013t193206.679d548-0ubuntu1_amd64.deb  File not found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

---

### Post by garywilson on 2009-12-02
thanks for info dude

---

