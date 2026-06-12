---
title: "Problems with initrd build after kernel 3.2.0-24.39 update"
date: 2012-06-14
forum: General Help
---

### Post by CharlesA on 2012-06-14
Hello,

I got an email saying unattended-upgrades installed some updates and a reboot is required, but I noticed some errors in the log that weren't there during the previous kernel update.

The lines in question are bolded.

```
Unattended upgrade returned: True

Warning: A reboot is required to complete this upgrade.

Packages that are upgraded:
 linux-headers-server linux-image-server linux-libc-dev linux-server

Package installation log:
Selecting previously unselected package linux-image-3.2.0-25-generic.
(Reading database ... 98906 files and directories currently installed.)
Unpacking linux-image-3.2.0-25-generic (from .../linux-image-3.2.0-25-generic_3.2.0-25.40_amd64.deb) ...
Done.
Selecting previously unselected package linux-headers-3.2.0-25.
Unpacking linux-headers-3.2.0-25 (from .../linux-headers-3.2.0-25_3.2.0-25.40_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-25-generic.
Unpacking linux-headers-3.2.0-25-generic (from .../linux-headers-3.2.0-25-generic_3.2.0-25.40_amd64.deb) ...
Preparing to replace linux-headers-server 3.2.0.24.26 (using .../linux-headers-server_3.2.0.25.27_amd64.deb) ...
Unpacking replacement linux-headers-server ...
Preparing to replace linux-server 3.2.0.24.26 (using .../linux-server_3.2.0.25.27_amd64.deb) ...
Unpacking replacement linux-server ...
Preparing to replace linux-image-server 3.2.0.24.26 (using .../linux-image-server_3.2.0.25.27_amd64.deb) ...
Unpacking replacement linux-image-server ...
Preparing to replace linux-libc-dev 3.2.0-24.39 (using .../linux-libc-dev_3.2.0-25.40_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Setting up linux-image-3.2.0-25-generic (3.2.0-25.40) ...
Running depmod.
**[COLOR="Red"]update-initramfs: deferring update (hook will be called later)[/COLOR]**
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
[B]: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.[/B]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
Generating grub.cfg ...
[B]Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic[/B]
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-headers-3.2.0-25 (3.2.0-25.40) ...
Setting up linux-headers-3.2.0-25-generic (3.2.0-25.40) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
Setting up linux-headers-server (3.2.0.25.27) ...
Setting up linux-image-server (3.2.0.25.27) ...
Setting up linux-server (3.2.0.25.27) ...
Setting up linux-libc-dev (3.2.0-25.40) ...


Unattended-upgrades log:
Initial blacklisted packages:
Starting unattended upgrades script
Allowed origins are: ['o=Ubuntu,a=precise-security']
Packages that are upgraded: linux-headers-server linux-image-server linux-libc-dev linux-server
Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg_2012-06-14_06:53:36.357833.log'
All upgrades installed
```

Here's the log from the kernel update on May 22:

```
Unattended upgrade returned: True

Warning: A reboot is required to complete this upgrade.

Packages that are upgraded:
 libxml2 libxml2-utils linux-headers-3.2.0-24
 linux-headers-3.2.0-24-generic linux-image-3.2.0-24-generic
 linux-libc-dev

Package installation log:
(Reading database ... 98896 files and directories currently installed.)
Preparing to replace libxml2 2.7.8.dfsg-5.1ubuntu4 (using .../libxml2_2.7.8.dfsg-5.1ubuntu4.1_amd64.deb) ...
Unpacking replacement libxml2 ...
Preparing to replace linux-image-3.2.0-24-generic 3.2.0-24.37 (using .../linux-image-3.2.0-24-generic_3.2.0-24.38_amd64.deb) ...
Done.
Unpacking replacement linux-image-3.2.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Preparing to replace libxml2-utils 2.7.8.dfsg-5.1ubuntu4 (using .../libxml2-utils_2.7.8.dfsg-5.1ubuntu4.1_amd64.deb) ...
Unpacking replacement libxml2-utils ...
Preparing to replace linux-headers-3.2.0-24 3.2.0-24.37 (using .../linux-headers-3.2.0-24_3.2.0-24.38_all.deb) ...
Unpacking replacement linux-headers-3.2.0-24 ...
Preparing to replace linux-headers-3.2.0-24-generic 3.2.0-24.37 (using .../linux-headers-3.2.0-24-generic_3.2.0-24.38_amd64.deb) ...
Unpacking replacement linux-headers-3.2.0-24-generic ...
Preparing to replace linux-libc-dev 3.2.0-24.37 (using .../linux-libc-dev_3.2.0-24.38_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for man-db ...
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.1) ...
Setting up linux-image-3.2.0-24-generic (3.2.0-24.38) ...
Running depmod.
**[COLOR="Red"]update-initramfs: deferring update (hook will be called later)[/COLOR]**
Not updating initrd symbolic links since we are being updated/reinstalled
(3.2.0-24.37 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(3.2.0-24.37 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up libxml2-utils (2.7.8.dfsg-5.1ubuntu4.1) ...
Setting up linux-headers-3.2.0-24 (3.2.0-24.38) ...
Setting up linux-headers-3.2.0-24-generic (3.2.0-24.38) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
Setting up linux-libc-dev (3.2.0-24.38) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place


Unattended-upgrades log:
Initial blacklisted packages:
Starting unattended upgrades script
Allowed origins are: ['o=Ubuntu,a=precise-security']
Packages that are upgraded: libxml2 libxml2-utils linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-image-3.2.0-24-generic linux-libc-dev
Writing dpkg log to '/var/log/unattended-upgrades/unattended-upgrades-dpkg_2012-05-22_06:53:29.437972.log'
All upgrades installed
```

update-initramfs: deferring update (hook will be called later) is in both, so I don't know if that is a problem or not, but in the update from this morning, the unable to find inital ram disk has me worried about booting into the updated kernel.

This is Ubuntu Server 12.04, running headless. I access it via SSH most of the time, but if needed I can get console access to fix the problem.

I did find the page here: [http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/](http://ubuntugenius.wordpress.com/2010/05/24/fix-a-failed-initramfs-update-do-it-before-you-reboot/)

But it is from 2010, so I do not know if it is still valid.

Any ideas?

---

### Post by djroketboy on 2012-06-14
I find it interesting I just got the same error. This is just a wild guess, but I'm thinking it might have something to do with the RocketRaid drivers.

---

### Post by CharlesA on 2012-06-14
> **djroketboy said:**
> I find it interesting I just got the same error. This is just a wild guess, but I'm thinking it might have something to do with the RocketRaid drivers.
Could be. I will try to reinstall the kernel when I get home and report back.

I just recently installed the version 1.4 drivers for rocketraid. I still have the modified 1.3 drivers that I can try if it doesn't work.

Thanks!

---

### Post by CharlesA on 2012-06-14
Looks like I found the problem - bad symlink:

```
charles@Thor:~$ sudo apt-get purge linux-image-3.2.0-25-generic linux-headers-3.                                                                                                                                                             2.0-25
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.2.0-25* linux-headers-3.2.0-25-generic*
  linux-headers-server* linux-image-3.2.0-25-generic* linux-image-server*
  linux-server*
0 upgraded, 0 newly installed, 6 to remove and 6 not upgraded.
After this operation, 216 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 125041 files and directories currently installed.)
Removing linux-headers-server ...
Removing linux-headers-3.2.0-25-generic ...
Removing linux-headers-3.2.0-25 ...
Removing linux-server ...
Removing linux-image-server ...
Removing linux-image-3.2.0-25-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2                                                                                                                                                             .0-25-generic
dkms: removing: rr264x 1.4 (3.2.0-25-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  rr264x
Version: 1.4
Kernel:  3.2.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

rr26xx.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

Backing up initrd.img-3.2.0-25-generic to /boot/initrd.img-3.2.0-25-generic.old-                                                                                                                                                             dkms
Making new initrd.img-3.2.0-25-generic
(If next boot fails, revert to initrd.img-3.2.0-25-generic.old-dkms image)
update-initramfs....

DKMS: uninstall completed.
dkms: removing: vboxhost 4.1.16 (3.2.0-25-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.1.16
Kernel:  3.2.0-25-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.2.0-25-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-25-generic /boot                                                                                                                                                             /vmlinuz-3.2.0-25-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-25-generic /boot/                                                                                                                                                             vmlinuz-3.2.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
[B][COLOR="Red"]done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img
 you may need to re-run your boot loader[grub][/COLOR][/B]
Purging configuration files for linux-image-3.2.0-25-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-25-generic /boot                                                                                                                                                             /vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-25-generic /boot/                                                                                                                                                             vmlinuz-3.2.0-25-generic

```

I checked one of my other precise boxes and it had these two links in /
```
lrwxrwxrwx   1 root root    29 May 29 20:21 vmlinuz -> boot/vmlinuz-3.2.0-24-generic
lrwxrwxrwx   1 root root    29 May 24 11:56 vmlinuz.old -> boot/vmlinuz-3.2.0-23-generic

```

The box with the error didn't, it had:
```
lrwxrwxrwx   1 root    root       33 Apr 28 19:34 initrd.img.old -> /boot/initrd.img-3.2.0-24-generic

lrwxrwxrwx   1 root    root       29 Apr 28 19:34 vmlinuz.old -> boot/vmlinuz-3.2.0-24-generic
```

So I ran this:

```

charles@Thor:~$ **sudo apt-get install linux-headers-server linux-image-server linux-libc-dev linux-server**
Reading package lists... Done
Building dependency tree
Reading state information... Done
linux-libc-dev is already the newest version.
linux-libc-dev set to manually installed.
The following extra packages will be installed:
  linux-headers-3.2.0-25 linux-headers-3.2.0-25-generic linux-image-3.2.0-25-generic
Suggested packages:
  fdutils linux-doc-3.2.0 linux-source-3.2.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.2.0-25 linux-headers-3.2.0-25-generic linux-headers-server linux-image-3.2.0-25-generic linux-image-server linux-server
0 upgraded, 6 newly installed, 0 to remove and 6 not upgraded.
Need to get 0 B/50.6 MB of archives.
After this operation, 216 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package linux-image-3.2.0-25-generic.
(Reading database ... 98897 files and directories currently installed.)
Unpacking linux-image-3.2.0-25-generic (from .../linux-image-3.2.0-25-generic_3.2.0-25.40_amd64.deb) ...
Done.
Selecting previously unselected package linux-headers-3.2.0-25.
Unpacking linux-headers-3.2.0-25 (from .../linux-headers-3.2.0-25_3.2.0-25.40_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-25-generic.
Unpacking linux-headers-3.2.0-25-generic (from .../linux-headers-3.2.0-25-generic_3.2.0-25.40_amd64.deb) ...
Selecting previously unselected package linux-headers-server.
Unpacking linux-headers-server (from .../linux-headers-server_3.2.0.25.27_amd64.deb) ...
Selecting previously unselected package linux-image-server.
Unpacking linux-image-server (from .../linux-image-server_3.2.0.25.27_amd64.deb) ...
Selecting previously unselected package linux-server.
Unpacking linux-server (from .../linux-server_3.2.0.25.27_amd64.deb) ...
Setting up linux-image-3.2.0-25-generic (3.2.0-25.40) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-headers-3.2.0-25 (3.2.0-25.40) ...
Setting up linux-headers-3.2.0-25-generic (3.2.0-25.40) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic
Setting up linux-headers-server (3.2.0.25.27) ...
Setting up linux-image-server (3.2.0.25.27) ...
Setting up linux-server (3.2.0.25.27) ...
charles@Thor:~$ ls -l /

lrwxrwxrwx   1 root    root       33 Jun 14 12:36 initrd.img -> /boot/initrd.img-3.2.0-25-generic
lrwxrwxrwx   1 root    root       29 Jun 14 12:36 vmlinuz -> boot/vmlinuz-3.2.0-25-generic

```

All good now:

Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-25-generic x86_64)

---

### Post by CharlesA on 2012-09-06
This seems to happen whenever there is a kernel update.

This time, DKMS messed up the kernel module and initrd failed to get created.

I got it working but only after rebuilding initrd: 
```
sudo update-initramfs -c -k $(uname -r)

```

And then removing the module from the dkms tree, and rebuilding it.

This has happened after ever kernel upgrade since the OP.

---

