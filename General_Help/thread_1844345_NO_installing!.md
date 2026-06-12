---
title: "NO installing?!"
date: 2011-09-15
forum: General Help
---

### Post by koei126 on 2011-09-15
Hi, I am having some really huge issues with ubuntu. Every time I try to install, uninstall, or modify a prgram, I get an error. Software center will stay stuck at the final part of an installation or removal, and even I can't even install anything through terminal. It always ends up giving me error messages. Even the update center won't work. What's going on here? It just came out of nowhere and I have full administrative access. I even tried creating another admin account. =/

---

### Post by LowSky on 2011-09-15
Hi welcome to the Forums, but please watch the language.

Could you please post one of these error messages? Thanks. 

We can't help unless you give us all the details.

---

### Post by koei126 on 2011-09-17
This is the error from the update manager:

The installation or removal of a software package failed.

Details:

installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%%dpkg: unrecoverable fatal error, aborting: 
 reading files list for package 'linux-headers-2.6.38-11': Input/output error 
Setting up libgl1-mesa-glx (7.10.2-0ubuntu2.1) ... 
Bus error 
dpkg: error processing libgl1-mesa-glx (--configure): 
 subprocess installed post-installation script returned error exit status 135 
Setting up linux-image-2.6.38-11-generic (2.6.38-11.50) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic 
Segmentation fault 
E: mkinitramfs failure cpio 139 gzip 0 
update-initramfs: failed for /boot/initrd.img-2.6.38-11-generic 
Failed to create initrd image. 
dpkg: error processing linux-image-2.6.38-11-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of libwxgtk2.8-0: 
 libwxgtk2.8-0 depends on libgl1-mesa-glx | libgl1; however: 
  Package libgl1-mesa-glx is not configured yet. 
  Package libgl1 is not installed. 
  Package libgl1-mesa-glx which provides libgl1 is not configured yet. 
dpkg: error processing libwxgtk2.8-0 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of xorg: 
 xorg depends on libgl1-mesa-glx | libgl1; however: 
  Package libgl1-mesa-glx is not configured yet. 
  Package libgl1 is not installed. 
  Package libgl1-mesa-glx which provides libgl1 is not configured yet. 
dpkg: error processing xorg (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libglu1-mesa: 
 libglu1-mesa depends on libgl1-mesa-glx | libgl1; however: 
  Package libgl1-mesa-glx is not configured yet. 
  Package libgl1 is not installed. 
  Package libgl1-mesa-glx which provides libgl1 is not configured yet. 
dpkg: error processing libglu1-mesa (--configure): 
 dependency problems - leaving unconfigured 


Also, it doesn't give an error from the software center, it just stays on the finishing step.

---

### Post by dino99 on 2011-09-17
first, make some cleaning:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

sudo dpkg --configure -a

then force a fsck on next boot:

sudo shutdown -r now

Now, boot on recovery mode (hold 'shift' key down at bios end process to see the grub menu) and select 'repair packages', then reboot:

sudo reboot

---

