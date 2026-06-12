---
title: "Remove force-architecture installs"
date: 2011-06-11
forum: General Help
---

### Post by Hark3n on 2011-06-11
Howzit guys,

Small problem that I ran into.

I installed the latest version of Freecad by downloading the 32-bit deb file directly from the developers website.  Installed it with dpkg --force-architecture.

In the end the installed didn't work.  Decided to rather try the older version in the repositories, but now I get the following error when I try to install.

> ****@****:~$ sudo apt-get install freecad
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  freecad-doc
The following NEW packages will be installed:
  freecad
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/6,264 kB of archives.
After this operation, 18.5 MB of additional disk space will be used.
dpkg: error processing /var/cache/apt/archives/freecad_0.10.3247.dfsg-2ubuntu3_amd64.deb (--unpack):
 freecad: 0.10.3247.dfsg-2ubuntu3 (Multi-Arch: no) is not co-installable with freecad:i386 0.11.3729-1lucid1 (Multi-Arch: no) which is currently installed
Errors were encountered while processing:
 /var/cache/apt/archives/freecad_0.10.3247.dfsg-2ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I have dug around on the net and the forums, but I can't seem to find a working solution.

Any help would be appreciated.

---

### Post by dino99 on 2011-06-11
dont mix 32 & 64 packages :(

sudo rm processing /var/cache/apt/archives/freecad_0.10.3247.dfsg-2ubuntu3_amd64.deb

---

### Post by Hark3n on 2011-06-11
I know I shouldn't mix them, but I guess I like to scratch where is doesn't itch.

Anyway, running that command returns "rm: cannot remove `processing': No such file or directory"

---

### Post by oldos2er on 2011-06-11
Try ```
sudo dpkg -r freecad
```

---

