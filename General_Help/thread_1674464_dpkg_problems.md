---
title: "dpkg problems"
date: 2011-01-23
forum: General Help
---

### Post by crewkid89 on 2011-01-23
I have been getting this error.  I am currently running xubuntu 8.04.4 on a really old laptop. I can't seem to solve it the way apt is asking me to. Here is what I am getting:

kevin@kevin-laptop:~$ sudo dpkg --configure -a
[sudo] password for kevin: 
Setting up linux-ubuntu-modules-2.6.24-28-generic (2.6.24-28.47) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-28-generic
touch: cannot touch `/boot/initrd.img-2.6.24-28-generic.new': No such file or directory
/usr/sbin/mkinitramfs: 279: cannot create /boot/initrd.img-2.6.24-28-generic.new: Directory nonexistent
update-initramfs: failed for /boot/initrd.img-2.6.24-28-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-28-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-28-generic

Any help in solving this problem would be greatly appreciated.

---

### Post by derklempner on 2011-01-23
What happened initially for you to have to use **sudo dpkg --configure -a**?

---

### Post by crewkid89 on 2011-01-23
a failed update of the same package

---

### Post by derklempner on 2011-01-23
Okay, seems like I've already answered this question once tonight, so it should be simple.  Open a terminal and type:
```
cd /var/lib/dpkg/updates
sudo rm -rf ./*
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by crewkid89 on 2011-01-23
thanks so much for your quick reply still no dice though. there was nothing in that directory but I tried anyways, error returned:

update-initramfs: Generating /boot/initrd.img-2.6.24-28-generic
touch: cannot touch `/boot/initrd.img-2.6.24-28-generic.new': No such file or directory
/usr/sbin/mkinitramfs: 279: cannot create /boot/initrd.img-2.6.24-28-generic.new: Directory nonexistent
update-initramfs: failed for /boot/initrd.img-2.6.24-28-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-28-generic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.24-28-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by crewkid89 on 2011-01-24
yea... still haven't figured this one out.  I might just do a clean install if I can't figure anything else out

---

### Post by crewkid89 on 2011-01-25
no hope? I'll probably just do a clean install.  How is lubuntu as a replacement for what I currently have.

---

