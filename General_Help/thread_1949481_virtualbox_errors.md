---
title: "virtualbox errors"
date: 2012-03-30
forum: General Help
---

### Post by qwertyjjj on 2012-03-30
I get the following errors.
I tried uninstalling and reinstalling and same thing:

```

virtualbox is to be removed.
  Package virtualbox-4.1 which provides virtualbox is not installed.
(Reading database ... 191848 files and directories currently installed.)
Removing virtualbox ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Selecting previously deselected package virtualbox-4.1.
(Reading database ... 191733 files and directories currently installed.)
Unpacking virtualbox-4.1 (from .../virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jack@jack-Inspiron-9300:~$ sudo apt-get install virtualbox-4.1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libvncserver0 libkeybinder0 python-keybinder
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  virtualbox-4.1
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/68.7 MB of archives.
After this operation, 128 MB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 191733 files and directories currently installed.)
Unpacking virtualbox-4.1 (from .../virtualbox-4.1_4.1.10-76795~Ubuntu~oneiric_i386.deb) ...
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Setting up virtualbox-4.1 (4.1.10-76795~Ubuntu~oneiric) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  Error! Your kernel headers for kernel 3.0.0-17-generic cannot be found.
Please install the linux-headers-3.0.0-17-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located


```

---

### Post by Habitual on 2012-03-30
"Please install the linux-headers-3.0.0-17-generic package,"

---

### Post by qwertyjjj on 2012-03-30
> **Habitual said:**
> "Please install the linux-headers-3.0.0-17-generic package,"

Shouldn't it already be installed?
How do I install headers? Isn;t that source stuff?

---

### Post by qwertyjjj on 2012-03-30
> **Habitual said:**
> "Please install the linux-headers-3.0.0-17-generic package,"

jack@jack-Inspiron-9300:~$ sudo apt-get install linux-headers-3.0.0-17-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libvncserver0 libkeybinder0 python-keybinder
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.0.0-17
The following NEW packages will be installed:
  linux-headers-3.0.0-17 linux-headers-3.0.0-17-generic
0 upgraded, 2 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/12.3 MB of archives.
After this operation, 98.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package linux-headers-3.0.0-17.
(Reading database ... 192207 files and directories currently installed.)
Unpacking linux-headers-3.0.0-17 (from .../linux-headers-3.0.0-17_3.0.0-17.30_all.deb) ...
Selecting previously deselected package linux-headers-3.0.0-17-generic.
Unpacking linux-headers-3.0.0-17-generic (from .../linux-headers-3.0.0-17-generic_3.0.0-17.30_i386.deb) ...
Setting up linux-headers-3.0.0-17 (3.0.0-17.30) ...
Setting up linux-headers-3.0.0-17-generic (3.0.0-17.30) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.0.0-17-generic /boot/vmlinuz-3.0.0-17-generic
[B]Error! Problems with depmod detected.  Automatically uninstalling this module.
DKMS: Install Failed (depmod problems).  Module rolled back to built state.[/B]
jack@jack-Inspiron-9300:~$

---

