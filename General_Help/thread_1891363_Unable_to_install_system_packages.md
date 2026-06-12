---
title: "Unable to install system packages"
date: 2011-12-05
forum: General Help
---

### Post by techunit on 2011-12-05
[LEFT]Seems like a simple apt-get problem. But I can't figure it out. Purhaps you guys can lend a helping hand.

```
Errors were encountered while processing:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```One of my Ubuntu repos is acting up.

```
W: GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```I have run the following diagnostics.
```

sudo apt-get install -f
sudo dpkg --configure -a

``````
sudo apt-get install -f
``` yeilded a somewhat interesting result
```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.0.0-13-generic (3.0.0-13.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
/etc/default/grub: 11: i915.i915_enable_rc6=1: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-13-generic; however:
  Package linux-image-3.0.0-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.13.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```This is stopping me from getting the latest kernels and for the last two weeks I have been ignoring it. I have checked synaptic for broken packages and found nothing.

Thanks so much for anyone who takes the time to help.
[/LEFT]

---

### Post by techunit on 2011-12-05
Bump

---

### Post by nedski on 2011-12-14
I had a similar problem and found the answer here: [http://ubuntuforums.org/showthread.php?t=1882082](http://ubuntuforums.org/showthread.php?t=1882082) - 9th post

Briefly, command sequence is:

```
$ sudo apt-get clean
$ cd /var/lib/apt
$ sudo mv lists lists.old
$ sudo mkdir -p lists/partial
$ sudo apt-get clean
$ sudo apt-get update
```

---

