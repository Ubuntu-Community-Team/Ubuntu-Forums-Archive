---
title: "I keep having problems installing programs"
date: 2011-09-03
forum: General Help
---

### Post by Vinilguy on 2011-09-03
Every time I try to install anything (GIMP in this case) I get this message:
[PHP]installArchives() failed: Selecting previously deselected package libgimp2.0. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 159279 files and directories currently installed.) 
Unpacking libgimp2.0 (from .../libgimp2.0_2.6.8-2ubuntu1.3_i386.deb) ... 
Selecting previously deselected package gimp-data. 
Unpacking gimp-data (from .../gimp-data_2.6.8-2ubuntu1.3_all.deb) ... 
Selecting previously deselected package libbabl-0.0-0. 
Unpacking libbabl-0.0-0 (from .../libbabl-0.0-0_0.0.22-1build1_i386.deb) ... 
Selecting previously deselected package libgegl-0.0-0. 
Unpacking libgegl-0.0-0 (from .../libgegl-0.0-0_0.0.22-0ubuntu4_i386.deb) ... 
Selecting previously deselected package gimp. 
Unpacking gimp (from .../gimp_2.6.8-2ubuntu1.3_i386.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for man-db ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for python-support ... 
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-runtime (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up liblastfm0 (0.4.0~git20090710-1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblastfm0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmysqlclient16 (5.1.41-3ubuntu12.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmysqlclient16 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libgimp2.0 (2.6.8-2ubuntu1.3) ... 
 
Setting up gimp-data (2.6.8-2ubuntu1.3) ... 
Setting up libbabl-0.0-0 (0.0.22-1build1) ... 
 
Setting up libgegl-0.0-0 (0.0.22-0ubuntu4) ... 
 
Setting up gimp (2.6.8-2ubuntu1.3) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 kdebase-runtime 
 liblastfm0 
 libmysqlclient16 
Setting up liblastfm0 (0.4.0~git20090710-1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing liblastfm0 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up kdebase-runtime (4:4.4.5-0ubuntu1) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing kdebase-runtime (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up libmysqlclient16 (5.1.41-3ubuntu12.10) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing libmysqlclient16 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
[/PHP]

---

### Post by 2F4U on 2011-09-03
Are you installing from a repository or a downloaded package?

---

### Post by Vinilguy on 2011-09-03
Downloaded package

---

### Post by kiddykoff on 2011-09-03
it looks like you're having problems with,
 kdebase-runtime 
 liblastfm0 
 libmysqlclient16 

Try doing a purge, updating, upgrading, and reinstalling.

---

### Post by dino99 on 2011-09-03
you should use the packages inside synaptic because ubuntu settings are quite different from vanilla packages.

Otherwise, open/create an empty folder, download these deb inside, then:

cd /to/that/folder
sudo dpkg -i *.deb

---

### Post by Vinilguy on 2011-09-03
I am quite new to ubuntu, could you please guide me step by step on how to do this?

---

### Post by kiddykoff on 2011-09-03
open a terminal and put this in.
sudo apt-get purge kdebase-runtime liblasfm0 libmysqlclient16; sudo apt-get update; sudo apt-get upgrade; sudo apt-get install kdebase-runtime liblastfm0 libmysqlclient16

(i know there is a better way of writing this out, but this still works)

If it were me i would get rid of them if i could. If you have something that depends on those packages though you would keep them. To check I like to use Synaptic.

---

