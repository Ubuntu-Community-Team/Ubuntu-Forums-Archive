---
title: "Unable to update kernel..."
date: 2010-11-11
forum: General Help
---

### Post by oshirowanen on 2010-11-11
I get the following output when I run:
```
sudo aptitude full-upgrade
```

Output:
```
oshirowanen@oshirowanen-desktop:~$ sudo aptitude full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
The following packages will be upgraded:
  linux-image-2.6.32-25-generic 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.5MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 142145 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-25-generic 2.6.32-25.44 (using .../linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-25-generic ...
[COLOR="Red"]dpkg-deb: subprocess paste killed by signal (Broken pipe)
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2[/COLOR]
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
[COLOR="Red"]Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:[/COLOR]
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

oshirowanen@oshirowanen-desktop:~$ 

```

Why is this happening and how do I resolve this issue?

---

### Post by oshirowanen on 2010-11-11
Fixed it by running the following commands:
```
sudo apt-get -f install
sudo apt-get clean
sudo dpkg --clear-avail
sudo apt-get update
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-2.6.32-25-generic_2.6.32-25.45_i386.deb
sudo apt-get -f install
sudo aptitude update
sudo aptitude full-upgrade
```

---

