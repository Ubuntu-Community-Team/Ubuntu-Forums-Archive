---
title: "Persisten USB installation won't upgrade Linux Image"
date: 2012-05-06
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-06
Hi all.

I have Precise installed on a USB stick. It works great, except that it constantly reports that an update is available, but won't install it with an error. here's the code:

```
sale@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  linux-image-3.2.0-24-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 76.5 MB of archives.
After this operation, 17.4 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ precise/main linux-image-3.2.0-23-generic amd64 3.2.0-23.36 [38.2 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ precise-proposed/main linux-image-3.2.0-24-generic amd64 3.2.0-24.38 [38.3 MB]                                
Fetched 76.5 MB in 3min 2s (420 kB/s)                                                                                                                 
Selecting previously unselected package linux-image-3.2.0-23-generic.
(Reading database ... 211713 files and directories currently installed.)
Preparing to replace linux-image-3.2.0-23-generic 3.2.0-23.36 (using .../linux-image-3.2.0-23-generic_3.2.0-23.36_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
Setting up linux-image-3.2.0-23-generic (3.2.0-23.36) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.2.0-23.36 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-23-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-24-generic (3.2.0-24.37) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-24-generic; however:
  Package linux-image-3.2.0-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.24.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                 Errors were encountered while processing:
 linux-image-3.2.0-23-generic
 linux-image-3.2.0-24-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
sale@ubuntu:~$ 

```

---

### Post by oldfred on 2012-05-06
While a persistent install lets you save some things, it still is the CD on a USB and is not updatable as it can install the standard install.

If you want to update kernel, you need a full install on the USB flash drive. You need a 8GB flash as minimum to do that unless you use one of the more lightweight versions.

---

### Post by efflandt on 2012-05-06
On the iso on USB, the kernel boots from a fixed squashfs (compressed) filesystem before persistent data is mounted.  So while persistent data can keep certain settings (like timezone and wireless security or network settings) and can hold installed programs that can run after booting, it cannot (easily) be used for kernel or video driver updates, or anything else that happens before persistent data is mounted.  You basically would need to know how to modify and create your own custom iso.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-07
Thanks for your help guys, it makes it all much clearer.

oldfred, when you mention 'full install on a usb', do you have any resources about that? I'd like to try that, but I've never heard about it before.

---

### Post by oldfred on 2012-05-07
I have a full install of 12.04 on a 8GB partition on my 16GB flash drive. It is just to test that 12.04 works on my laptop as I do not want to reparation to test on it yet. It runs ok, just not speedy from flash drive. From a flash drive a lighter weight version with smaller apps may be a better alternative.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Install process is not really different by version & a full install to a flash drive is no different than any install to a second drive except you want to make some settings to reduce writes.

Installs to 4GB flash, newer versions require 4.4GB as minimum
HOW TO Avoid Wubi & Install Ubuntu 10.04 on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-07
Sweet, much appreciated! Will give it a try as soon as I can.

---

