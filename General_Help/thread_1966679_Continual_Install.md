---
title: "Continual Install"
date: 2012-04-27
forum: General Help
---

### Post by Miykel on 2012-04-27
G'day; A few days ago I tried to install kernel 3.4.0rc4, which was a disaster but now every time I do a  sudo apt-get dist-upgrade the upgrade goes fine but then it tries to install the kernel, how can I stop this ??
  I have purged all files connected with the kernel from the file where I downloaded the .deb packages, cleaned out /usr/src and /boot.
  The distro is Ubuntu 12.04 
Regards Miykel

---

### Post by IWantFroyo on 2012-04-27
```
sudo apt-get upgrade --only-upgrade
```

---

### Post by Miykel on 2012-04-27
Thanks for the reply; I run that code but it still wants to install the kernel;

Processing triggers for gnome-menus ...
Setting up linux-image-3.4.0-030400rc4-generic (3.4.0-030400rc4.201204211835) ...
Internal Error: Could not find image (/boot/vmlinuz-3.4.0-030400rc4-generic)
dpkg: error processing linux-image-3.4.0-030400rc4-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up python-problem-report (2.0.1-0ubuntu6) ...
Setting up python-apport (2.0.1-0ubuntu6) ...
Setting up apport (2.0.1-0ubuntu6) ...
apport start/running
Setting up apport-gtk (2.0.1-0ubuntu6) ...
Setting up firefox (12.0+build1-0ubuntu0.12.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (12.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-gnome-support (12.0+build1-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (12.0+build1-0ubuntu0.12.04.1) ...
Setting up linux-libc-dev (3.2.0-24.37) ...
Errors were encountered while processing:
 linux-image-3.4.0-030400rc4-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
miykel@miykel-H61M-USB3-B3:~$ 


Above is the last part of the upgrade, it can't find the files because they do not exist, either the .deb packages I downloaded the other day or the files in /boot, what I'd like to know is what tells the installer to look for them files or to try to install the kernel, at least thats what i imagine I'm looking for.

Regards Miykel

---

### Post by dino99 on 2012-04-27
use synaptic  and deactivate the kernel ppa, then update and continue installation if needed.

---

### Post by Miykel on 2012-04-27
Thanks for the reply Dino99, done a search with Synoptic and found an entry for kernel 3.4.0rc4 32bit, I run 64 bit system, how the 32 bit version was installed I have no idea, but I uninstalled it and all is well again.
Many Thanks
Regards Miykel

---

