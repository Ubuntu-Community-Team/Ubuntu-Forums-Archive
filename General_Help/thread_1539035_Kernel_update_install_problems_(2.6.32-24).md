---
title: "Kernel update install problems (2.6.32-24)"
date: 2010-07-26
forum: General Help
---

### Post by BlackDex on 2010-07-26
Hello there,

I have a problem after the kernel update for lucid.
I just installed the available updates, and now i get errors.

How can i fix this???

Here is the output of apt-get install.

```

root@blackdex-ubuntu:/lib/modules# apt-get install -f linux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image linux-image-2.6.32-24-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.32 linux-source-2.6.32 linux-tools
The following NEW packages will be installed:
  linux linux-image linux-image-2.6.32-24-generic linux-image-generic
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 31.4MB of archives.
After this operation, 128MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-24-generic 2.6.32-24.38 [31.4MB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-generic 2.6.32.24.25 [4,028B]                                                                                                                                        
Get:3 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image 2.6.32.24.25 [4,016B]                                                                                                                                                
Get:4 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux 2.6.32.24.25 [4,008B]                                                                                                                                                      
Fetched 31.4MB in 13s (2,315kB/s)                                                                                                                                                                                                           
Selecting previously deselected package linux-image-2.6.32-24-generic.
(Reading database ... 229426 files and directories currently installed.)
Unpacking linux-image-2.6.32-24-generic (from .../linux-image-2.6.32-24-generic_2.6.32-24.38_amd64.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_2.6.32.24.25_amd64.deb) ...
Selecting previously deselected package linux-image.
Unpacking linux-image (from .../linux-image_2.6.32.24.25_amd64.deb) ...
Selecting previously deselected package linux.
Unpacking linux (from .../linux_2.6.32.24.25_amd64.deb) ...
Setting up linux-image-2.6.32-24-generic (2.6.32-24.38) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows Recovery Environment (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-24-generic; however:
  Package linux-image-2.6.32-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.32.24.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 2.6.32.24.25); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    No apport report written because MaxReports is reached already
                                     Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-generic
 linux-image
 linux
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by BlackDex on 2010-07-26
{bump}

---

### Post by BlackDex on 2010-07-26
Thanks to "oCean_" on the ubuntu IRC channel it is solved now.
He pointed me to this post: [https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795](https://bugs.launchpad.net/ubuntu/+source/nvidia-common/+bug/303795)

Basically the problem was the **nvidia-common** package which caused the trouble.
After purging that package and reinstalling it, the problem was solved.

---

### Post by skykooler on 2010-09-10
For me the problem was that I had uninstalled GRUB after installing BURG. Reinstalling GRUB fixed the problem.

---

