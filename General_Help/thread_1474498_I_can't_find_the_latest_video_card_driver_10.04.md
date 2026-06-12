---
title: "I can't find the latest video card driver 10.04"
date: 2010-05-06
forum: General Help
---

### Post by ibrahim.k on 2010-05-06
Hi,  When I was using 9.10 Karmic I have downloaded drivers for  Nvidia version 185  but after installing 10.04 I can't find it !  I can only find nvidia 173 which is older and causing problems  slow on performance.  please see the image below.  [[img]http://ibrahim-k.co.cc/kleeja/download.php?img=6[/img]](http://ibrahim-k.co.cc/kleeja/download.php?img=6)

---

### Post by realzippy on 2010-05-06
Choose the "current driver".It is the newest (195.xx)...

---

### Post by ibrahim.k on 2010-05-06
How can I download the latest version ??? 195 its not even on the list

---

### Post by philinux on 2010-05-06
Select "version current" that will install nvidia-current 195.36.15

---

### Post by ibrahim.k on 2010-05-06
> **philinux said:**
> Select "version current" that will install nvidia-current 195.36.15


I have downloaded the "version current" but it wasn't better than 185 that one was better can I download it ?

---

### Post by philinux on 2010-05-06
> **ibrahim.k said:**
> I have downloaded the "version current" but it wasn't better than 185 that one was better can I download it ?

Not entirely sure how this works now. You could try this.

```
sudo apt-get install nvidia-glx-185
```

Then open Hardware drivers and see if it is there as an option. If it is deactivate Current and activate 185.

**No guarantees**. The Current driver works just fine here 8600GT.

---

### Post by ibrahim.k on 2010-05-06
I got this what does it mean ?? 

sudo apt-get install nvidia-glx-185ibrahim@ibrahim-laptop:~$ sudo apt-get install nvidia-glx-185
[sudo] password for ibrahim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-185 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up nvidia-185-modaliases (195.36.15-0ubuntu2) ...

thnx for helping me

---

### Post by philinux on 2010-05-06
On my system it installed it. It must have already been installed on yours then. If hardware drivers doesn't offer it as an option then I'm at a loss. There probably is an update-alternatives command but I've not seen one yet.

---

### Post by ibrahim.k on 2010-05-08
[SIZE=4]I can't install anything now !!! something wrong had happened ![/SIZE]

for example.


installArchives() failed: Selecting previously deselected package guake.  
(Reading database ...  (Reading database ... 5% (Reading database ...  10% (Reading database ... 15% (Reading database ... 20% (Reading  database ... 25% (Reading database ... 30% (Reading database ... 35%  (Reading database ... 40% (Reading database ... 45% (Reading database  ... 50% (Reading database ... 55% (Reading database ... 60% (Reading  database ... 65% (Reading database ... 70% (Reading database ... 75%  (Reading database ... 80% (Reading database ... 85% (Reading database  ... 90% (Reading database ... 95% (Reading database ... 100% (Reading  database ... 125402 files and directories currently installed.) 
Unpacking guake (from .../guake_0.4.1-3_amd64.deb) ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up nvidia-173 (173.14.22-0ubuntu11) ... 
dpkg (subprocess): unable to execute installed post-installation script:  Exec format error 
dpkg: error processing nvidia-173 (--configure): 
 subprocess installed post-installation script returned error exit  status 2 
Setting up nvidia-current (195.36.15-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script:  Exec format error 
dpkg: error processing nvidia-current (--configure): 
 subprocess installed post-installation script returned error exit  status 2 
Setting up guake (0.4.1-3) ... 
 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 nvidia-173 
 nvidia-current 
Setting up nvidia-current (195.36.15-0ubuntu2) ... 
dpkg (subprocess): unable to execute installed post-installation script:  Exec format error 
dpkg: error processing nvidia-current (--configure): 
 subprocess installed post-installation script returned error exit  status 2

---

### Post by dino99 on 2010-05-08
i dont know what you are doing, but with ubuntu there is nothing to "download" ;)

If Ubuntu devs fine tuned our grahic drivers, its not for nothing.

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Goto synaptic and remove/purge ALL nvidia packages installed, check into repo tab that you only use genuine Lucid repo (no ppa or third party activated), then install:

nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

then: sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install -f
sudo update-initramfs -u

then reboot

---

### Post by ibrahim.k on 2010-05-08
There is something wrong on.
sudo apt-get autoremove



ibrahim@ibrahim-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libtidy-0.99-0 (20091223cvs-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libtidy-0.99-0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up nvidia-173 (173.14.22-0ubuntu11) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-173 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up nvidia-current (195.36.15-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-chardet (2.0.1-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-chardet (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up python-feedparser (4.1-14) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-feedparser (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up python-fpconst (0.7.2-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-fpconst (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-soappy:
 python-soappy depends on python-fpconst; however:
  Package python-fpconst is not configured yet.
dpkg: error processing python-soappy (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-utidylib:
 python-utidylib depends on libtidy-0.99-0 (>= 20051018); however:
  Package libtidy-0.99-0 is not configured yet.
dpkg: error processing python-utidylib (--configure):
 dependency problems - leaving unconfigured
Setting up hddtemp (0.3-beta15-45) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing hddtemp (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 libtidy-0.99-0
 nvidia-173
 nvidia-current
 python-chardet
 python-feedparser
 python-fpconst
 python-soappy
 python-utidylib
 hddtemp
E: Sub-process /usr/bin/dpkg returned an error code (1)
ibrahim@ibrahim-laptop:~$

---

### Post by 1Tanuki on 2010-05-09
> **dino99 said:**
> i dont know what you are doing, but with ubuntu there is nothing to "download" ;)

If Ubuntu devs fine tuned our grahic drivers, its not for nothing.

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

Goto synaptic and remove/purge ALL nvidia packages installed, check into repo tab that you only use genuine Lucid repo (no ppa or third party activated), then install:

nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

then: sudo rm -f /etc/X11/xorg.conf

sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo apt-get install -f
sudo update-initramfs -u

then reboot

Ive had a very similar problem.. Ive purchased another video card to attempt a dual screen with my TV... i have my TV hooked into my VGA on the built in nvidia video, and the monitor hooked into the DVI on the card... when i booted the TV said it had to go to safe mode.. i have attempted to do what you list here, but when i type sudo apt-get install nvidia-current it says

```
joel@tanuki:~$ sudo apt-get install nvidia-current
[sudo] password for joel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-current is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-current has no installation candidate

```
 ive tried unselecting the multiverse, restricted and any secondary packages, didnt help..

any help would be appreciated

---

