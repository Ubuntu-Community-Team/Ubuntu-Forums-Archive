---
title: "apt-get broken &gt;_&gt;"
date: 2011-11-10
forum: General Help
---

### Post by TamisLaan on 2011-11-10
I tried to install virtual box but ubuntu crashed during installation. Then i had to remove the /var/lib/dpkg/lock. Now when i apt-get install gcalctool it hangs on:

 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS

How do i remove these virtualbox leftovers?

Many thanks in advance!

---

### Post by hhh on 2011-11-10
Try...```
sudo apt-get -f install
```

Or try reinstalling VirtualBox and then purging it.

That's all I got, as they say.

---

### Post by carranty on 2011-11-10
Why did you have to remove the lock file?  Can you install anything with apt-get?  

If Ubuntu crashes during an installation usually all you need to do is type

*dpkg --configure*

after you reboot and it'll sort itself out.  I'm not sure what effect  deleting the lock file will have had (if any).  Try the above anyway, if  it doesn't work maybe you can remove it with
[I]
dpkg -r virtualbox[/I]

(I assume you've tried *apt-get remove virtualbox*)

If after the above you still can't use apt-get please paste the output of 

*dpkg --status virtualbox*

into this thread.

---

### Post by TamisLaan on 2011-11-11
Command:
```
sudo apt-get -f install
```
Hangs on:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  virtualbox-dkms virtualbox-qt
Suggested packages:
  virtualbox-guest-additions-iso vde2
The following packages will be REMOVED:
  virtualbox-4.1
The following NEW packages will be installed:
  virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/22.7 MB of archives.
After this operation, 52.6 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 90462 files and directories currently installed.)
Removing virtualbox-4.1 ...
 * Stopping VirtualBox kernel modules                               [ OK ] 
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Selecting previously deselected package virtualbox.
(Reading database ... 89727 files and directories currently installed.)
Unpacking virtualbox (from .../virtualbox_4.1.2-dfsg-1ubuntu1_amd64.deb) ...
Selecting previously deselected package virtualbox-dkms.
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.1.2-dfsg-1ubuntu1_all.deb) ...
Selecting previously deselected package virtualbox-qt.
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.2-dfsg-1ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Setting up gcalctool (6.2.0-0ubuntu1) ...
Setting up virtualbox (4.1.2-dfsg-1ubuntu1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-dkms (4.1.2-dfsg-1ubuntu1) ...
Loading new virtualbox-4.1.2 DKMS files...
```

---

### Post by TamisLaan on 2011-11-19
**BUMP**



Running sudo apt-get -f install returned:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  virtualbox virtualbox-qt
Suggested packages:
  virtualbox-guest-additions-iso vde2
Recommended packages:
  virtualbox-dkms
The following NEW packages will be installed:
  virtualbox virtualbox-qt
0 upgraded, 2 newly installed, 0 to remove and 27 not upgraded.
1 not fully installed or removed.
Need to get 22.0 MB of archives.
After this operation, 63.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
```

When i say Yes then it tries to install virtualbox but always hangs on:

```
Do you want to continue [Y/n]? Y
Get:1 http://nl.archive.ubuntu.com/ubuntu/ oneiric/universe virtualbox amd64 4.1.2-dfsg-1ubuntu1 [15.6 MB]
Get:2 http://nl.archive.ubuntu.com/ubuntu/ oneiric/universe virtualbox-qt amd64 4.1.2-dfsg-1ubuntu1 [6,369 kB]
Fetched 22.0 MB in 17s (1,240 kB/s)                                            
Selecting previously deselected package virtualbox.
(Reading database ... 87180 files and directories currently installed.)
Unpacking virtualbox (from .../virtualbox_4.1.2-dfsg-1ubuntu1_amd64.deb) ...
Selecting previously deselected package virtualbox-qt.
Unpacking virtualbox-qt (from .../virtualbox-qt_4.1.2-dfsg-1ubuntu1_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for hicolor-icon-theme ...
Setting up virtualbox (4.1.2-dfsg-1ubuntu1) ...
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
Processing triggers for python-central ...
Setting up virtualbox-dkms (4.1.2-dfsg-1ubuntu1) ...
Removing old virtualbox-4.1.2 DKMS files...

------------------------------
Deleting module version: 4.1.2
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-4.1.2 DKMS files...
Building only for 3.0.0-12-generic
Building initial module for 3.0.0-12-generic

```

Running sudo dpkg --configure virtualbox results in:

```
dpkg: error processing virtualbox (--configure):
 package virtualbox is already installed and configured
Errors were encountered while processing:
 virtualbox
```

running sudo dpkg -r virtualbox returned:

```

(Reading database ... 87457 files and directories currently installed.)
Removing virtualbox ...
 * Stopping VirtualBox kernel modules                                                                                                                  [ OK ] 
Processing triggers for man-db ...
Processing triggers for ureadahead ...

```

But installing usb-creator-gtk results in:


```
E: Invalid operation usb-creator-gtk
tux@tux:~$ sudo apt-get install usb-creator-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 usb-creator-gtk : Depends: usb-creator-common (= 0.2.34) but it is not going to be installed
                   Depends: gir1.2-unity-4.0 but it is not going to be installed
 virtualbox-dkms : Depends: virtualbox
 virtualbox-qt : Depends: virtualbox (= 4.1.2-dfsg-1ubuntu1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

So i removed virtualbox-qt successfully, but when removing virtualbox-dkms it is stuck again on:


```
(Reading database ... 87182 files and directories currently installed.)
Removing virtualbox-dkms ...
```

dpkg --status virtualbox returnes:

```
Package: virtualbox
Status: deinstall ok config-files
Priority: optional
Section: misc
Installed-Size: 43812
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 4.1.2-dfsg-1ubuntu1
Config-Version: 4.1.2-dfsg-1ubuntu1
Replaces: virtualbox-ose (<< 4.0.6-dfsg-1~)
Depends: libc6 (>= 2.11), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libpng12-0 (>= 1.2.13-4), libpython2.7 (>= 2.7), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.5.3), libsdl1.2debian (>= 1.2.10-1), libssl1.0.0 (>= 1.0.0), libstdc++6 (>= 4.6), libvncserver0, libx11-6, libxcursor1 (>> 1.1.2), libxext6, libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4), python (>= 2.5), python-central (>= 0.6.11), adduser
Recommends: virtualbox-dkms (= 4.1.2-dfsg-1ubuntu1), virtualbox-qt (= 4.1.2-dfsg-1ubuntu1), libgl1-mesa-glx | libgl1, libqt4-opengl (>= 4:4.5.3)
Suggests: virtualbox-guest-additions-iso, vde2
Breaks: virtualbox-ose (<< 4.0.6-dfsg-1~)
Conflicts: virtualbox-2.0, virtualbox-2.1, virtualbox-2.2, virtualbox-3.0
Conffiles:
 /etc/default/virtualbox 903beafa3922607d1ac07950d9ae2d50
 /etc/init.d/virtualbox e2c78950e836770caa0b1e21f235d191
Description: x86 virtualization solution - base binaries
 VirtualBox is a free x86 virtualization solution allowing a wide range
 of x86 operating systems such as Windows, DOS, BSD or Linux to run on a
 Linux system.
 .
 This package provides the binaries for VirtualBox. The virtualbox-dkms
 package is also required in order to compile the kernel modules needed for
 virtualbox. A graphical user interface for VirtualBox is provided by the
 package virtualbox-qt.
Homepage: http://www.virtualbox.org/
Original-Maintainer: Debian Virtualbox Team <pkg-virtualbox-devel@lists.alioth.debian.org>
Python-Version: >= 2.5
```

It seems that virtual-dkms is the culprit both when installing and removing virtualbox. 

I hope someone can help me i can't install or remove anything which is driving me nuts!!!

---

### Post by LinuxFan999 on 2011-11-19
Your installation is broken, so you need to back up your files, then reinstall Ubuntu..

---

### Post by wonko on 2011-11-23
I might have found a bug in dkms during an upgrade, so if you still haven't found a solution, and apt-get still hangs on dkms, try (during hang) removing a file called /tmp/dkms.xxxx (or checking that root has write-permission).

---

### Post by oldtimer7777 on 2011-11-23
> **LinuxFan999 said:**
> Your installation is broken, so you need to back up your files, then reinstall Ubuntu..

They hosed their system by doing an upgrade..  Lazy method.  Back up your data correctly, like you are supposed to do it, and do a fresh installation.

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

