---
title: "initramfs-tools partially installed, error after every use of apt-get/aptitude."
date: 2011-01-18
forum: General Help
---

### Post by tcopeland on 2011-01-18
Hello all. I was wondering how I can properly install initramfs-tools so it can properly configure boot images. You see, during **every** running of apt-get or aptitude processes, it returns this output after everything else has been installed/purged/removed/upgraded/etc. I've tried everything I can think of (which isn't much, I know): aptitude install, apt-get install, dpkg --configure, dpkg-reconfigure; and yet, it won't set up the image properly. Below is the output returned after every other package operation has been performed by apt-get or aptitude.
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda2
                     UUID=48e81d9a-13f7-43a5-a7a4-6640fdca2eb6
.: 17: Can't open /etc/default/console-setup
E: /usr/share/initramfs-tools/hooks/console_setup failed with return 127.
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Any ideas?

---

### Post by frio on 2011-01-21
Appears I am getting something very similar as I just noticed this on my 10.04.1 LTS server. No idea how long it has been this way. No fix as of yet (at least from me) but I'll post if I find something.

```

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up initramfs-tools (0.92bubuntu78) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-27-generic-pae
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.32-27-generic-pae
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by frio on 2011-02-01
I finally figured it out and it is not good, at least in my case. I believe I have a failing disk and since my last post the problems have gotten worse.

After getting rid of a couple of corrupt images, I was finally able to get the machine to boot back up (yes, it died on a reboot several days ago). Once I got this far, I followed [http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html) very carefully and was able to find the offending block(s) and the file(s) being affected. In my case it turned out to be a bad block that was occupied by /lib/libc-2.11.1.so, an important file. After some finagling, I was able to delete the file and then immediately restore it from a backup figuring that the system would not write to the bad block. It worked. Using the techniques described in the link above, I marked the blocks as bad and everything is working again. No more seg faults.

I will be replacing the disk ASAP. Hopefully someone finds this useful as I had a difficult time in finding useful posts/info out there directly related to this problem.

---

