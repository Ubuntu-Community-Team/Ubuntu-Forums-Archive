---
title: "unable to upgrade"
date: 2009-08-21
forum: General Help
---

### Post by HiImTye on 2009-08-21
so I had an update to linux-image-2.6.28-15-generic but it won't actually install. here is the output from the terminal

```
~$ sudo apt-get upgrade
[sudo] password for tye:     
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.                             
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y                               
Setting up linux-image-2.6.28-15-generic (2.6.28-15.49) ...    
Running depmod.                                                
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic
Running postinst hook script /sbin/update-grub.                
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default       
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...                  
Found kernel: /boot/vmlinuz-2.6.28-15-generic                            
Found kernel: /boot/vmlinuz-2.6.28-14-generic                            
Found kernel: /boot/vmlinuz-2.6.28-13-generic                            
Found kernel: /boot/vmlinuz-2.6.28-11-generic                            
Found kernel: /boot/vmlinuz-2.6.27-11-generic                            
Found kernel: /boot/vmlinuz-2.6.24-23-generic                            
Found kernel: /boot/memtest86+.bin                                       
Updating /boot/grub/menu.lst ... done                                    

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):                                             
 subprocess post-installation script returned error exit status 2                                               
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-15-generic:                  
 linux-restricted-modules-2.6.28-15-generic depends on linux-image-2.6.28-15-generic; however:                  
  Package linux-image-2.6.28-15-generic is not configured yet.                                                  
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):                                
 dependency problems - leaving unconfigured                                                                     
dpkg: dependency problems prevent configuration of linux-image-generic:                                         
 linux-image-generic depends on linux-image-2.6.28-15-generic; however:                                         
  Package linux-image-2.6.28-15-generic is not configured yet.                                                  
dpkg: error processing linux-image-generic (--configure):                                                       
 dependency problems - leaving unconfigured                                                                     
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:                            
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-15-generic; however:               
  Package linux-restricted-modules-2.6.28-15-generic is not configured yet.                                     
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.                                                                                                                   
                            No apport report written because the error message indicates its a followup error from a previous failure.         
                                                                                                                                      No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                                                                                                   ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.15.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.28-15-generic (2.6.28-15.49) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-15-generic; however:
  Package linux-headers-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-2.6.28-15-generic
 linux-restricted-modules-2.6.28-15-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.28-15-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

doing the install from recovery mode produces an endless loop of the above and dpkg trying to fix it

any ideas?

---

### Post by abhilashm86 on 2009-08-21
maybe things slightly messed up in lists, so try this
```
 sudo dpkg --configure -a

``` it should be able to resolve........

---

### Post by HiImTye on 2009-08-21
this is what I get (also the second half of the loop in 'fix broken packages' in recovery mode)

```
~$ sudo dpkg --configure -a
[sudo] password for tye:         
Setting up linux-headers-2.6.28-15-generic (2.6.28-15.49) ...
Examining /etc/kernel/header_postinst.d.                     
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-15-generic (--configure):                                                   
 subprocess post-installation script returned error exit status 2                                                       
Setting up linux-image-2.6.28-15-generic (2.6.28-15.49) ...                                                             
Running depmod.                                                                                                         
update-initramfs: Generating /boot/initrd.img-2.6.28-15-generic                                                         
Running postinst hook script /sbin/update-grub.                                                                         
Searching for GRUB installation directory ... found: /boot/grub                                                         
Searching for default file ... found: /boot/grub/default                                                                
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst                                               
Searching for splash image ... none found, skipping ...                                                                 
Found kernel: /boot/vmlinuz-2.6.28-15-generic                                                                           
Found kernel: /boot/vmlinuz-2.6.28-14-generic                                                                           
Found kernel: /boot/vmlinuz-2.6.28-13-generic                                                                           
Found kernel: /boot/vmlinuz-2.6.28-11-generic                                                                           
Found kernel: /boot/vmlinuz-2.6.27-11-generic                                                                           
Found kernel: /boot/vmlinuz-2.6.24-23-generic                                                                           
Found kernel: /boot/memtest86+.bin                                                                                      
Updating /boot/grub/menu.lst ... done                                                                                   

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-15-generic (--configure):                                             
 subprocess post-installation script returned error exit status 2                                               
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-15-generic; however:
  Package linux-headers-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-15-generic:
 linux-restricted-modules-2.6.28-15-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-15-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-15-generic; however:
  Package linux-image-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-15-generic; however:
  Package linux-restricted-modules-2.6.28-15-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.15.20); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.15.20); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.28-15-generic
 linux-image-2.6.28-15-generic
 linux-headers-generic
 linux-restricted-modules-2.6.28-15-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
```

---

### Post by HiImTye on 2009-08-22
ok, I did a dpkg-reconfigure -a, dropped to a recovery console and apt-get remove'd all 7 of the packages then apt-get install'd all of them and I get the same error..

anyone have any idea how to fix this?

---

### Post by HiImTye on 2009-08-23
bump for next-day check

---

### Post by P4man on 2009-08-23
im not  sure, but is it possible you didnt install nvidia drivers from the repo's? I'd try removing the nvidia drivers first, then try dpkg-reconfigure -a again. IF that works, then install the nvidia drivers back (from the repo's this time).

---

### Post by HiImTye on 2009-08-24
I'm not using nVidia drivers, I have a "Rage XL AGP 2X" with custom drivers to enable compositing but I've upgraded the kernel many times (from 8.04 on) so it shouldn't be an issue

---

### Post by P4man on 2009-08-24
Are you sure?

> run-parts: executing /etc/kernel/postinst.d/**nvidia-common**
run-parts: /etc/kernel/postinst.d/**nvidia-common** exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst line 1002.

---

### Post by HiImTye on 2009-08-25
yup, I'm sure, I had to compile them

---

### Post by HiImTye on 2009-09-01
so to fix this I had to do the following:

```
sudo apt-get purge nvidia common && sudo apt-get install nvidia-common
```

purging it let me properly install the kernel and then I added it again 'just in case'

---

### Post by rforums on 2009-12-26
thankyou.. worked like a charm..

---

