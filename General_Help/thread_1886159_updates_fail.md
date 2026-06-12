---
title: "updates fail"
date: 2011-11-24
forum: General Help
---

### Post by l07 on 2011-11-24
Each time I "restart to complete update," then run ```
sudo aptitude update && sudo aptitude dist-upgrade
``` nothing changes, producing exactly the same output upon running the same command.
```
The following partially installed packages will be configured:
  linux-headers-2.6.35-31-generic linux-headers-generic linux-image-2.6.35-31-generic linux-image-generic 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.35-31-generic (2.6.35-31.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                                                                                                                    Errors were encountered while processing:
 linux-image-2.6.35-31-generic
 linux-headers-2.6.35-31-generic
 linux-headers-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-31-generic (2.6.35-31.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.35-31-generic
 linux-image-2.6.35-31-generic
 linux-headers-generic

```

---

### Post by jerrrys on 2011-11-26
you can try:

sudo dpkg --configure -a

sudo apt-get install -f

and maybe even

sudo apt-get update && sudo apt-get upgrade

---

### Post by l07 on 2011-12-11
I tried each of those, but the error persisted.

sudo dpkg --configure -a
```
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-31-generic (2.6.35-31.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.35-31-generic
 linux-image-2.6.35-31-generic
 linux-headers-generic

```sudo apt-get install -f
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-31-generic (2.6.35-31.62) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                        Errors were encountered while processing:
 linux-image-2.6.35-31-generic
 linux-headers-2.6.35-31-generic
 linux-headers-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```sudo apt-get update && sudo apt-get upgrade
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  acpid linux-headers-2.6.35-31 linux-headers-2.6.35-31-generic linux-image-2.6.35-31-generic linux-libc-dev
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 45.9MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://security.ubuntu.com/ubuntu/ maverick-security/main linux-image-2.6.35-31-generic i386 2.6.35-31.63 [33.9MB]
Get:2 http://security.ubuntu.com/ubuntu/ maverick-security/main linux-headers-2.6.35-31 all 2.6.35-31.63 [10.3MB]                                                                                                                           
Get:3 http://security.ubuntu.com/ubuntu/ maverick-security/main linux-headers-2.6.35-31-generic i386 2.6.35-31.63 [804kB]                                                                                                                   
Get:4 http://security.ubuntu.com/ubuntu/ maverick-security/main acpid i386 1.0.10-5ubuntu4.4 [47.3kB]                                                                                                                                       
Get:5 http://security.ubuntu.com/ubuntu/ maverick-security/main linux-libc-dev i386 2.6.35-1031.63 [829kB]                                                                                                                                  
Fetched 45.9MB in 7min 58s (95.9kB/s)                                                                                                                                                                                                       
(Reading database ... 271007 files and directories currently installed.)
Preparing to replace linux-image-2.6.35-31-generic 2.6.35-31.62 (using .../linux-image-2.6.35-31-generic_2.6.35-31.63_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.35-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
Preparing to replace linux-headers-2.6.35-31 2.6.35-31.62 (using .../linux-headers-2.6.35-31_2.6.35-31.63_all.deb) ...
Unpacking replacement linux-headers-2.6.35-31 ...
Preparing to replace linux-headers-2.6.35-31-generic 2.6.35-31.62 (using .../linux-headers-2.6.35-31-generic_2.6.35-31.63_i386.deb) ...
Unpacking replacement linux-headers-2.6.35-31-generic ...
Preparing to replace acpid 1.0.10-5ubuntu4.1 (using .../acpid_1.0.10-5ubuntu4.4_i386.deb) ...
acpid stop/waiting
Unpacking replacement acpid ...
Preparing to replace linux-libc-dev 2.6.35-1031.62 (using .../linux-libc-dev_2.6.35-1031.63_i386.deb) ...
Unpacking replacement linux-libc-dev ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up linux-image-2.6.35-31-generic (2.6.35-31.63) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31 (2.6.35-31.63) ...
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.63) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                        Setting up acpid (1.0.10-5ubuntu4.4) ...
Installing new version of config file /etc/acpi/powerbtn.sh ...
acpid start/running, process 24056
Setting up linux-libc-dev (2.6.35-1031.63) ...
Errors were encountered while processing:
 linux-image-2.6.35-31-generic
 linux-headers-2.6.35-31-generic
 linux-headers-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by l07 on 2011-12-17
Still no change.

---

### Post by wildmanne39 on 2011-12-17
Hi, you can try what this link suggests but read it carefully.
[http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/](http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/)
Thanks

---

### Post by l07 on 2011-12-18
I tried that, no change.
```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-31-generic (2.6.35-31.63) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.63) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                        Errors were encountered while processing:
 linux-image-2.6.35-31-generic
 linux-headers-2.6.35-31-generic
 linux-headers-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I deleted the matching files in /var/lib/dpkg/info and when I wanted to list them here, trash says "unable to display all the contents, operation not supported," and just keeps the busy cursor. This is in sudo nautilus, which I used to look for the files.
I looked for these files:
 linux-headers-2.6.35-31-generic
 linux-headers-generic
 linux-image-2.6.35-31-generic
 linux-image-generic

with extensions .postrm and .list, and deleted those that were present. They don't seem to be recreated.

---

### Post by l07 on 2011-12-20
Still no change.

---

### Post by l07 on 2011-12-26
```
$ sudo aptitude update && sudo aptitude dist-upgrade -y
                            
The following partially installed packages will be configured:
  linux-headers-2.6.35-31-generic linux-headers-generic linux-image-2.6.35-31-generic linux-image-generic 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up linux-image-2.6.35-31-generic (2.6.35-31.63) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.63) ...
No apport report written because MaxReports is reached already
                                                              Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                          Errors were encountered while processing:
 linux-image-2.6.35-31-generic
 linux-headers-2.6.35-31-generic
 linux-headers-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-headers-2.6.35-31-generic (2.6.35-31.63) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-31-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-31-generic (2.6.35-31.63) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-31-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
 * dkms: running auto installation service for kernel 2.6.35-31-generic                                                                                                                                                                      
 *       nvidia-current (260.19.06)...                                                                                                                                                                                                [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-31-generic /boot/vmlinuz-2.6.35-31-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-31-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-31-generic; however:
  Package linux-headers-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-31-generic; however:
  Package linux-image-2.6.35-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.35-31-generic
 linux-image-2.6.35-31-generic
 linux-headers-generic
```

---

