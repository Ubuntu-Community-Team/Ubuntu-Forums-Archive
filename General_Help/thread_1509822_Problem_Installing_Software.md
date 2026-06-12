---
title: "Problem Installing Software"
date: 2010-06-14
forum: General Help
---

### Post by axeman627 on 2010-06-14
Hello all, first post here. Been playing with Ubuntu for a few weeks and really enjoying it. But apparently I blew something up and perhaps someone can help. When attempting to install software from the software center I get the following error message. Anyone have any idea how I can fix this? Any help would be greatly appreciated...thanks!

Error message.....

nstallArchives() failed: Selecting previously deselected package libboost-regex1.40.0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 155393 files and directories currently installed.) 
Unpacking libboost-regex1.40.0 (from .../libboost-regex1.40.0_1.40.0-4ubuntu4_i386.deb) ... 
Selecting previously deselected package liblua5.1-0. 
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-5_i386.deb) ... 
Selecting previously deselected package libphysfs1. 
Unpacking libphysfs1 (from .../libphysfs1_2.0.0-4_i386.deb) ... 
Selecting previously deselected package libsdl-image1.2. 
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-1_i386.deb) ... 
Selecting previously deselected package libsdl-sound1.2. 
Unpacking libsdl-sound1.2 (from .../libsdl-sound1.2_1.0.3-3build1_i386.deb) ... 
Selecting previously deselected package libsigc++-1.2-5c2. 
Unpacking libsigc++-1.2-5c2 (from .../libsigc++-1.2-5c2_1.2.7-2_i386.deb) ... 
Selecting previously deselected package libwxbase2.8-0. 
Unpacking libwxbase2.8-0 (from .../libwxbase2.8-0_2.8.10.1-0ubuntu1_i386.deb) ... 
Selecting previously deselected package libwxgtk2.8-0. 
Unpacking libwxgtk2.8-0 (from .../libwxgtk2.8-0_2.8.10.1-0ubuntu1_i386.deb) ... 
Selecting previously deselected package asc-data. 
Unpacking asc-data (from .../asc-data_2.4.0.0-1_all.deb) ... 
Selecting previously deselected package asc. 
Unpacking asc (from .../asc_2.4.0.0-1_i386.deb) ... 
Selecting previously deselected package asc-music. 
Unpacking asc-music (from .../asc-music_1.3-2_all.deb) ... 
Processing triggers for man-db ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-support ... 
Setting up kdebase-workspace-bin (4:4.4.2-0ubuntu14) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-workspace-bin (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libpackagekit-qt-12 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up software-properties-kde (0.75.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing software-properties-kde (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libpackagekit-glib2-12 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up python-packagekit (0.5.7-0ubuntu2) ... 
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing python-packagekit (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of packagekit-backend-apt: 
 packagekit-backend-apt depends on python-packagekit (= 0.5.7-0ubuntu2); however: 
  Package python-packagekit is not configured yet. 
dpkg: error processing packagekit-backend-apt (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of packagekit: 
 packagekit depends on libpackagekit-glib2-12 (= 0.5.7-0ubuntu2); however: 
  Package libpackagekit-glib2-12 is not configured yet. 
 packagekit depends on packagekit-backend-apt | packagekit-backend-smart; however: 
  Package packagekit-backend-apt is not configured yet. 
  Package packagekit-backend-smart is not installed. 
dpkg: error processing packagekit (--configure): 
 dependency problems - leaving unconfiNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
gured 
Setting up update-manager-kde (1:0.134.9) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing update-manager-kde (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of kpackagekit: 
 kpackagekit depends on libpackagekit-qt-12; however: 
  Package libpackagekit-qt-12 is not configured yet. 
 kpackagekit depends on kdebase-workspace-bin; however: 
  Package kdebase-workspace-bin is not configured yet. 
 kpackagekit depends on software-properties-kde; however: 
  Package software-properties-kde is not configured yet. 
 kpackagekit depends on packagekit (>= 0.4.7); however: 
  Package packagekit is not configured yet. 
 kpackagekit depends on update-manager-kde; however: 
  Package update-manager-kde is not configured yet. 
dpkg: error processing kpackagekit (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kubuntu-debug-installer: 
 kubuntu-deNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
bug-installer depends on kpackagekit; however: 
  Package kpackagekit is not configured yet. 
dpkg: error processing kubuntu-debug-installer (--configure): 
 dependency problems - leaving unconfigured 
Setting up libboost-regex1.40.0 (1.40.0-4ubuntu4) ... 
 
Setting up liblua5.1-0 (5.1.4-5) ... 
 
Setting up libphysfs1 (2.0.0-4) ... 
 
Setting up libsdl-image1.2 (1.2.10-1) ... 
 
Setting up libsdl-sound1.2 (1.0.3-3build1) ... 
 
Setting up libsigc++-1.2-5c2 (1.2.7-2) ... 
 
Setting up libwxbase2.8-0 (2.8.10.1-0ubuntu1) ... 
 
Setting up libwxgtk2.8-0 (2.8.10.1-0ubuntu1) ... 
 
Setting up asc-data (2.4.0.0-1) ... 
Setting up asc (2.4.0.0-1) ... 
 
Setting up asc-music (1.3-2) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 kdebase-workspace-bin 
 libpackagekit-qt-12 
 software-properties-kde 
 libpackagekit-glib2-12 
 python-packagekit 
 packagekit-backend-apt 
 packagekit 
 update-manager-kde 
 kpackagekit 
 kubuntu-debug-installer 
Setting up software-properties-kde (0.75.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing software-properties-kde (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of kpackagekit: 
 kpackagekit depends on software-properties-kde; however: 
  Package software-properties-kde is not configured yet. 
dpkg: error processing kpackagekit (--configure): 
 dependency problems - leaving unconfigured 
Setting up python-packagekit (0.5.7-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing python-packagekit (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up update-manager-kde (1:0.134.9) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing update-manager-kde (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libpackagekit-glib2-12 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up kdebase-workspace-bin (4:4.4.2-0ubuntu14) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-workspace-bin (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libpackagekit-qt-12 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of packagekit: 
 packagekit depends on libpackagekit-glib2-12 (= 0.5.7-0ubuntu2); however: 
  Package libpackagekit-glib2-12 is not configured yet. 
dpkg: error processing packagekit (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of kubuntu-debug-installer: 
 kubuntu-debug-installer depends on kpackagekit; however: 
  Package kpackagekit is not configured yet. 
dpkg: error processing kubuntu-debug-installer (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of packagekit-backend-apt: 
 packagekit-backend-apt depends on python-packagekit (= 0.5.7-0ubuntu2); however: 
  Package python-packagekit is not configured yet. 
dpkg: error processing packagekit-backend-apt (--configure): 
 dependency problems - leaving unconfigured

---

### Post by zvacet on 2010-06-15
```
sudo dpkg --configure -a
```

---

### Post by nischalinn on 2010-06-15
ya try the command [B]

sudo --configure -a

[/B]it will help you.

---

### Post by axeman627 on 2010-06-15
OK, thanks for your response. I tried that command and here is what I get. Software installs still fail the same.

Error message:

mike@mike-desktop:~$ sudo dpkg --configure -a
Setting up software-properties-kde (0.75.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing software-properties-kde (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kpackagekit:
 kpackagekit depends on software-properties-kde; however:
  Package software-properties-kde is not configured yet.
dpkg: error processing kpackagekit (--configure):
 dependency problems - leaving unconfigured
Setting up python-packagekit (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-packagekit (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up update-manager-kde (1:0.134.9) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing update-manager-kde (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-glib2-12 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up kdebase-workspace-bin (4:4.4.2-0ubuntu14) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdebase-workspace-bin (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-qt-12 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of packagekit:
 packagekit depends on libpackagekit-glib2-12 (= 0.5.7-0ubuntu2); however:
  Package libpackagekit-glib2-12 is not configured yet.
dpkg: error processing packagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kpackagekit; however:
  Package kpackagekit is not configured yet.
dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of packagekit-backend-apt:
 packagekit-backend-apt depends on python-packagekit (= 0.5.7-0ubuntu2); however:
  Package python-packagekit is not configured yet.
dpkg: error processing packagekit-backend-apt (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 software-properties-kde
 kpackagekit
 python-packagekit
 update-manager-kde
 libpackagekit-glib2-12
 kdebase-workspace-bin
 libpackagekit-qt-12
 packagekit
 kubuntu-debug-installer
 packagekit-backend-apt
mike@mike-desktop:~$

---

### Post by lunatico on 2010-07-15
I'm having a similar problem:

```
sudo aptitude install htop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  packagekit-backend-apt 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up packagekit-backend-apt (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing packagekit-backend-apt (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 packagekit-backend-apt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
```

Where you able to fix this?
Anyone?

---

### Post by soldier1st on 2010-07-17
i had a similar issue about a package not being configured but what i did to fix it was to see if that component was installed and sure enough it was not and if it was then i would have chosen to reinstall it and that fixed the issue i had.

---

### Post by lunatico on 2010-07-17
> **soldier1st said:**
> i had a similar issue about a package not being configured but what i did to fix it was to see if that component was installed and sure enough it was not and if it was then i would have chosen to reinstall it and that fixed the issue i had.

Thanks, yeah I tried that... didn't make any difference.
I just reinstalled the entire thing, couldn't afford wasting more time on it.

---

