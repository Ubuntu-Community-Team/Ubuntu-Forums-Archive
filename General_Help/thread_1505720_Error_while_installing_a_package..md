---
title: "Error while installing a package."
date: 2010-06-09
forum: General Help
---

### Post by ibrahim.k on 2010-06-09
There is something wrong with the nvidia driver installation, but i dont know what is it exactly or how to fix it, when i try to install anything i get this error 



installArchives() failed: Selecting previously deselected package gnomeradio. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171659 files and directories currently installed.) 
Unpacking gnomeradio (from .../gnomeradio_1.8-1_amd64.deb) ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up nvidia-173 (173.14.22-0ubuntu11) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing nvidia-173 (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up gnomeradio (1.8-1) ... 
 
Errors were encountered while processing: 
 nvidia-173 
Setting up nvidia-173 (173.14.22-0ubuntu11) ... 
dpkg (subprocess): unable to execute installed post-installation script: Exec format error 
dpkg: error processing nvidia-173 (--configure): 
 subprocess installed post-installation script returned error exit status 2

---

### Post by Jinger on 2010-06-09
If you have a Nvidia you can find driver in System-->Administration-->Driver Hardware

Where did you get that driver?

---

### Post by bodhi.zazen on 2010-06-09
Do you have separate /tmp or /home or other partitions mounted noexec ?

---

