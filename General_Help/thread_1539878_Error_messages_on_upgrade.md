---
title: "Error messages on upgrade"
date: 2010-07-27
forum: General Help
---

### Post by smerral on 2010-07-27
I get annoying error messages with every upgrade. Nothing seems to be affected and everything seems to run OK. I thought the installation of the latest kernel would solve it but apparently not It's the same when I do an autoremove as below:

brian@brian-laptop:~$ sudo apt-get autoremove
[sudo] password for brian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-24-generic (2.6.32-24.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.32-24-generic (2.6.32-24.38) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-24-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-24-generic; however:
  Package linux-headers-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-headers-2.6.32-23-generic
 linux-headers-2.6.32-24-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
brian@brian-laptop:~$ 

Any ideas? Anyone else encountered this?

---

### Post by P4man on 2010-07-27
try this:

```
sudo dpkg --configure -a
```

---

### Post by smerral on 2010-07-28
Thanks for the reply. I tried what you said but it didn't work unfortunately:


brian@brian-laptop:~$ sudo dpkg --configure -a
[sudo] password for brian: 
Setting up linux-image-2.6.32-24-generic (2.6.32-24.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.32-24-generic (2.6.32-24.38) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-24-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-24-generic; however:
  Package linux-headers-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-headers-2.6.32-23-generic
 linux-headers-2.6.32-24-generic
 linux-headers-generic
brian@brian-laptop:~$

---

### Post by rollin on 2010-07-28
I haven't had that error before but you could try under Synaptic, Edit, Fix broken packages? Might be worth a shot!

---

### Post by smerral on 2010-07-28
Well I tried it - it tells me dependency problems are solved. But nothing's changed - it just generates the same errors as above. Ah well, was worth a shot!

---

### Post by rollin on 2010-07-28
> **smerral said:**
> Well I tried it - it tells me dependency problems are solved. But nothing's changed - it just generates the same errors as above. Ah well, was worth a shot!

That sucks then! Hopefully someone with a solution will post, if not I can only suggest something like "apt-get check" or the manpage for apt-get LOL: [http://linux.die.net/man/8/apt-get](http://linux.die.net/man/8/apt-get). Good luck with it all the same though :)

Edit: Being nosey I found this, older post but maybe the commands at the bottom might work... [http://ubuntuforums.org/archive/index.php/t-1246221.html](http://ubuntuforums.org/archive/index.php/t-1246221.html).

---

### Post by P4man on 2010-07-28
It looks like it wont install the new kernel because of a conflict with nvidia DKMS. Did you remove DKMS by any chance? or manually tried installing nvidia drivers? 

You could try removing anything nvidia using synaptic then run the above command again and later reinstall nvidia drivers (preferably through hardware drivers in system > administration and not from the nvidia website).

---

### Post by smerral on 2010-07-28
Thanks!
That solved it.
I don't know why Nvidia came to be installed as I don't require it but removing it did the trick.

Cheers!

---

### Post by devil ether on 2010-09-26
> **P4man said:**
> It looks like it wont install the new kernel because of a conflict with nvidia DKMS. Did you remove DKMS by any chance? or manually tried installing nvidia drivers? 

You could try removing anything nvidia using synaptic then run the above command again and later reinstall nvidia drivers (preferably through hardware drivers in system > administration and not from the nvidia website).

I get the same messages, and i'm thinking - or maybe mostly hoping - it's the for the same reasons. [i also get the bit's about nvidia blah blah techno blah] However i must admit to being unsure of installing the nvidia drivers, as the video card on my laptop is most definitely nvidia, and anytime i've ever either not had drivers or uninstalled them (you know when you're fealing frisky and wanna risk it a little?) I've always had severe issues with actually getting my monitor to work afterwards.

I guess my real question would be this - Which ones should i uninstall?  Just the ones with Nvidia in the name? or all 13 of the ones ive got installed that also say 'works with nvidia....' or 'finds obselete drivers for nvidia' so on and so forth?

Here's the list of what came up when i entered 'nvidia' into synaptic:

jockey-common
jockey-gtk
libvdpau-dev
libvdpau1
nvidia-173-modaliases
nvidia-96-modaliases
nvidia-common
nvidia-current
nvidia-current-modaliases
nvidia-settings
smartdimmer
xserver-xorg-video-nouveau
xserver-xorg-video-nv

thanks for any replies and help!

---

### Post by P4man on 2010-09-27
YOu have the (proprietary) nvidia driver. You can uninstall or disable it the same way you installed it. System > adminstration > hardware drivers. Or remove "nvidia-current" (the rest will be autoremoved).

---

