---
title: "Radeon Mobility X2300 and OpenGL"
date: 2011-02-05
forum: General Help
---

### Post by witerat on 2011-02-05
Playing alien-arena @ 1 or 2 frame per second kinda sucked so I installed the ATI driver from the software centre. This was worse BadLength errors.
attempts to install fglrx failed 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/18.2MB of archives.
After this operation, 60.0MB of additional disk space will be used.
(Reading database ... 282091 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.723.1-0ubuntu5_i386.deb) ...

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run /usr/share/ati/fglrx-uninstall.sh (this is not recommended).

dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu5_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
lspci lists my card correctly.
My card is not the Radeon Mobility HD X2300.
installing the packages from ATI didn't work either
OpenGL support in my Lucid installation is quite knackered ATM.

most of the solutions I found were 3-4 years old itwas really hard to find one that didn;t fallover for missing/nla packages
:confused:

-----
Asus F3ke amd turion64+  2.00GHz 3Gb  ati radeon mobility X2300

---

