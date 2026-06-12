---
title: "Synaptics dkms errors"
date: 2011-04-24
forum: General Help
---

### Post by andrew.kunk on 2011-04-24
Hi guys, I've been using ubuntu for a few weeks now and I really like it.

I used a 9.04 live cd and installed it on my laptop in a new partition

The problem is, whenever I install something, whether it be an application installed through the software center, or when I upgraded to 9.10 and then to 10.04 (which i'm using now) I get the following error:

Error! Cannot locate /usr/src/synaptics-1.0.0.dkms.tar.gz
File does not exist.
dpkg: error processing snyaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 synaptics dkms

A pop-up also says that the installation was unsuccessful, although the applications I have installed seem to work fine. 

:confused:

---

### Post by andrew.kunk on 2011-04-24
Oh, and this also happens whenever I install/remove packages in the synaptic package manager... Thought that was important to add.

---

### Post by KegHead on 2011-04-24
Hi!

Try this in terminal;

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo apt-get install linux-image -f

Restart

Advise.

KegHead

---

### Post by andrew.kunk on 2011-04-25
andrew@andrew-laptop:~$ sudo apt-get dist-upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-2.6.32-31 linux-headers-2.6.32-31-generic
  linux-image-2.6.32-31-generic
The following packages will be upgraded:
  libslp1 libtiff4 linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev
6 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 43.2MB of archives.
After this operation, 185MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-2.6.32-31-generic 2.6.32-31.61 [31.5MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libslp1 1.2.1-7.6ubuntu0.1 [52.1kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main libtiff4 3.9.2-2ubuntu0.7 [137kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-generic 2.6.32.31.37 [4,510B]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-image-generic 2.6.32.31.37 [4,518B]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-31 2.6.32-31.61 [9,913kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-2.6.32-31-generic 2.6.32-31.61 [773kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-headers-generic 2.6.32.31.37 [4,510B]
Get:9 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main linux-libc-dev 2.6.32-31.61 [813kB]
Fetched 43.2MB in 2min 17s (315kB/s)                                           
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.32-31-generic.
(Reading database ... 204352 files and directories currently installed.)
Unpacking linux-image-2.6.32-31-generic (from .../linux-image-2.6.32-31-generic_2.6.32-31.61_i386.deb) ...
Done.
Preparing to replace libslp1 1.2.1-7.6 (using .../libslp1_1.2.1-7.6ubuntu0.1_i386.deb) ...
Unpacking replacement libslp1 ...
Preparing to replace libtiff4 3.9.2-2ubuntu0.6 (using .../libtiff4_3.9.2-2ubuntu0.7_i386.deb) ...
Unpacking replacement libtiff4 ...
Preparing to replace linux-generic 2.6.32.30.36 (using .../linux-generic_2.6.32.31.37_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.32.30.36 (using .../linux-image-generic_2.6.32.31.37_i386.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously deselected package linux-headers-2.6.32-31.
Unpacking linux-headers-2.6.32-31 (from .../linux-headers-2.6.32-31_2.6.32-31.61_all.deb) ...
Selecting previously deselected package linux-headers-2.6.32-31-generic.
Unpacking linux-headers-2.6.32-31-generic (from .../linux-headers-2.6.32-31-generic_2.6.32-31.61_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.32.30.36 (using .../linux-headers-generic_2.6.32.31.37_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 2.6.32-30.59 (using .../linux-libc-dev_2.6.32-31.61_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up synaptics-dkms (1.0.0) ...
Loading new synaptics-1.0.0 DKMS files...

Error! Cannot locate /usr/src/synaptics-1.0.0.dkms.tar.gz.
File does not exist.
dpkg: error processing synaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-31-generic (2.6.32-31.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-31-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-31-generic
Found kernel: /boot/vmlinuz-2.6.32-30-generic
Found kernel: /boot/vmlinuz-2.6.31-23-generic
Found kernel: /boot/vmlinuz-2.6.28-19-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
 * dkms: running auto installation service for kernel 2.6.32-31-generic         
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic

Setting up libslp1 (1.2.1-7.6ubuntu0.1) ...

Setting up libtiff4 (3.9.2-2ubuntu0.7) ...

Setting up linux-image-generic (2.6.32.31.37) ...
Setting up linux-generic (2.6.32.31.37) ...
Setting up linux-headers-2.6.32-31 (2.6.32-31.61) ...
Setting up linux-headers-2.6.32-31-generic (2.6.32-31.61) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic
 * dkms: running auto installation service for kernel 2.6.32-31-generic         
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-31-generic /boot/vmlinuz-2.6.32-31-generic

Setting up linux-headers-generic (2.6.32.31.37) ...
Setting up linux-libc-dev (2.6.32-31.61) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 synaptics-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)


thanks, it worked up until sudo apt-get dist-upgrade -f and then I got this error ^

---

### Post by Rubi1200 on 2011-04-25
Try running this:

```
sudo dpkg --configure -a
```then

```
sudo apt-get update
```If the problem is still not resolved, remove the package causing the problems:

```
sudo apt-get purge synaptics-dkms
```

---

### Post by andrew.kunk on 2011-04-25
Thanks everybody

The 'purge' command fixed it, thanks

---

### Post by KegHead on 2011-04-25
Hi!

Congrats!

Please mark your thread as "solved".

KegHead

---

### Post by Rubi1200 on 2011-04-25
> **andrew.kunk said:**
> Thanks everybody

The 'purge' command fixed it, thanks
Glad you got things sorted out finally :-)

---

### Post by ElijahLynn on 2011-10-15
This was very helpful, thanks. 

Purge command also worked for me, does this mean I don't have the package/program anymore or is this just a file it used to install the program?

---

