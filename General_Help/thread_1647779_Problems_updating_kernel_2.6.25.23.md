---
title: "Problems updating kernel 2.6.25.23"
date: 2010-12-17
forum: General Help
---

### Post by rajeeja on 2010-12-17
[B]INCORRECT TITLE "2.6.35-23" is correct!
[/B]

I'm unable to update the kernel:
```
rajeev@nix:~$ sudo apt-get install
[sudo] password for rajeev: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
^YNot updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-10-generic (2.6.37-10.24) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-10-generic

```

This is my version of grub now:

```

rajeev@nix:~$ grub-install -v
grub-install (GNU GRUB 0.97)

```

Prior to this i installed grub 2 and had grub.cfg. After running the following commands:

```
sudo aptitude update
sudo aptitude -f install
```

It was prompting me to:
Could not find /boot/grub/menu.lst. Would you like it generated for you? == i pressed no.

Did these commands get me to grub again from grub 2? Since I now see this:
```


rajeev@nix:~$ grub-install -v
grub-install (GNU GRUB 0.97)

```


Attaching the results (RESULTS.txt) from running the boot info script:

At present:

1. I'm able to boot windows
2. I'm able to boot via 
kernel 2.6.35.23 and 2.6.35.22

The problem is there is no panel what so ever, i can't even see the top bar, shutdown button/time or application button or sides.

Please let me know if you need more details.

Many thanks.

---

### Post by rajeeja on 2010-12-17
This is the full message when trying to update. The problem seems to be with graphics. I have a dell xps 1330 integrated graphics card. 

On running gnome-panel from the terminal i can see the panels. 

```
rajeev@nix:~$ sudo apt-get install
[sudo] password for rajeev: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
^YNot updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-10-generic (2.6.37-10.24) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
 * dkms: running auto installation service for kernel 2.6.37-10-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-9-generic (2.6.37-9.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-9-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
 * dkms: running auto installation service for kernel 2.6.37-9-generic          
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-9-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-9-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-10-generic; however:
  Package linux-image-2.6.37-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.10.12); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.37-10-generic
 linux-image-2.6.37-9-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Many thanks,

Another completely different bug that's affecting me is :
[https://bugs.launchpad.net/ubuntu/+source/gdb/+bug/690431](https://bugs.launchpad.net/ubuntu/+source/gdb/+bug/690431)

---

### Post by tokyobadger on 2010-12-17
what output does
```
lsb_release -a
```
give you?

---

### Post by cariboo on 2010-12-17
Moved to General Help, as this doesn't belong in Natty Testing & Discussion.

---

### Post by sikander3786 on 2010-12-18
In order to know more about your setup, (there was an error message regarding LILO in your output above), I would suggest to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

I hope there are no other problems with boot as you said and this is not a Wubi install (??). Anyways, boot script would tell us.


Regarding the issue, try,

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

Keep on posting the error messages ;-)

---

### Post by rajeeja on 2010-12-18
> **tokyobadger said:**
> what output does
```
lsb_release -a
```
give you?

rajeev@nix:~/Desktop$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu natty (development branch)
Release:	11.04
Codename:	natty
rajeev@nix:~/Desktop$

---

### Post by rajeeja on 2010-12-18
> **cariboo907 said:**
> Moved to General Help, as this doesn't belong in Natty Testing & Discussion.

lsb_release says natty...anyways..

---

### Post by rajeeja on 2010-12-18
> **sikander3786 said:**
> In order to know more about your setup, (there was an error message regarding LILO in your output above), I would suggest to post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

I hope there are no other problems with boot as you said and this is not a Wubi install (??). Anyways, boot script would tell us.


Regarding the issue, try,

```
sudo apt-get clean
```

```
sudo apt-get autoclean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get upgrade
```

Keep on posting the error messages ;-)

```
rajeev@nix:~/Desktop$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rajeev@nix:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 21 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-10-generic (2.6.37-10.24) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
 * dkms: running auto installation service for kernel 2.6.37-10-generic       
 *       virtualbox-ose (3.2.12)...                                      [ OK ]
 *       blcr (0.8.2)...                                                 [fail]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-9-generic (2.6.37-9.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-9-generic
mExamining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
 * dkms: running auto installation service for kernel 2.6.37-9-generic        
 *       virtualbox-ose (3.2.12)...                                      [ OK ]
 *       blcr (0.8.2)...                                                 [fail]
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-9-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-9-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-10-generic; however:
  Package linux-image-2.6.37-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.10.12); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.37-10-generic
 linux-image-2.6.37-9-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by rajeeja on 2010-12-18
```
rajeev@nix:~/Desktop$ sudo dpkg --configure -a
Setting up linux-image-2.6.37-10-generic (2.6.37-10.24) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
 * dkms: running auto installation service for kernel 2.6.37-10-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-10-generic; however:
  Package linux-image-2.6.37-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.10.12); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-2.6.37-9-generic (2.6.37-9.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-9-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
 * dkms: running auto installation service for kernel 2.6.37-9-generic          
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/zz-lilo 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Warning: Not updating LILO; /etc/lilo.conf not found
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) n

Not creating /boot/grub/menu.lst as you wish

run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-9-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-9-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.37-10-generic
 linux-image-2.6.35-23-generic
 linux-image-generic
 linux-generic
 linux-image-2.6.37-9-generic

```

---

### Post by rajeeja on 2010-12-18
[I]Sorry  for being verbose about the o/p, just wanted to communicate all the o/p..
[/I]
```

sudo apt-get update && sudo apt-get upgrade
```


```
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US    
Hit http://archive.canonical.com natty Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ natty/partner Translation-en          
Ign http://archive.canonical.com/ubuntu/ natty/partner Translation-en_US       
Hit http://archive.canonical.com maverick Release                              
Get:2 http://dl.google.com stable Release [1,347 B]                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://extras.ubuntu.com natty Release.gpg                                 
Ign http://extras.ubuntu.com/ubuntu/ natty/main Translation-en                 
Ign http://extras.ubuntu.com/ubuntu/ natty/main Translation-en_US              
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Hit http://archive.canonical.com natty Release                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Hit http://ppa.launchpad.net maverick/main Sources                             
Get:3 http://dl.google.com stable/main i386 Packages [735 B]                   
Hit http://extras.ubuntu.com natty Release                                     
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-security Release.gpg                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Hit http://archive.canonical.com maverick/partner Sources                      
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://extras.ubuntu.com maverick/main i386 Packages             
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Hit http://archive.canonical.com natty/partner Sources               
Hit http://archive.canonical.com natty/partner i386 Packages         
Hit http://extras.ubuntu.com natty/main i386 Packages                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com natty Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ natty/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty/universe Translation-en_US
Hit http://us.archive.ubuntu.com natty-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com natty-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ natty-security/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://us.archive.ubuntu.com maverick-security Release
Hit http://us.archive.ubuntu.com natty Release  
Hit http://us.archive.ubuntu.com natty-updates Release
Hit http://us.archive.ubuntu.com natty-security Release
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com natty/main i386 Packages
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty/universe i386 Packages
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/main i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com natty-security/main i386 Packages
Hit http://us.archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com natty-security/universe i386 Packages
Hit http://us.archive.ubuntu.com natty-security/multiverse i386 Packages
Fetched 2,279 B in 1s (1,155 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  libboost-dev libboost-program-options-dev libboost-python-dev
  libboost-thread-dev libunity3 libzeitgeist-gio shiki-brave-theme
  shiki-dust-theme shiki-human-theme shiki-illustrious-theme shiki-noble-theme
  shiki-wine-theme shiki-wise-theme
The following packages will be upgraded:
  apport apport-gtk compiz compiz-core compiz-gnome compiz-plugins cpp-4.5
  foomatic-db g++-4.5 g++-4.5-multilib gcc-4.5 gcc-4.5-base gcc-4.5-multilib
  gfortran-4.5 jockey-common jockey-gtk launchpad-integration lib64gcc1
  lib64gomp1 lib64stdc++6 libdecoration0 libgcc1 libgfortran3 libgomp1 libiw30
  liblaunchpad-integration-common liblaunchpad-integration1
  liblaunchpad-integration1.0-cil liblpint-bonobo0 libstdc++6
  libstdc++6-4.5-dev libvte-common libvte9 libxerces-c28 libxi-dev libxi6
  nvidia-common openprinting-ppds python-apport python-launchpad-integration
  python-problem-report python-vte ttf-vlgothic ubuntu-sso-client unity-common
  update-manager update-manager-core wireless-tools xinput
49 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
5 not fully installed or removed.
Need to get 39.5 MB of archives.
After this operation, 57.3 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main ubuntu-sso-client all 1.1.7-0ubuntu1 [39.2 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main lib64gcc1 i386 1:4.5.2-1ubuntu1 [42.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty/main libgomp1 i386 4.5.2-1ubuntu1 [24.0 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ natty/main lib64gomp1 i386 4.5.2-1ubuntu1 [25.4 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ natty/main libgfortran3 i386 4.5.2-1ubuntu1 [237 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ natty/main gfortran-4.5 i386 4.5.2-1ubuntu1 [4,706 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ natty/main g++-4.5-multilib i386 4.5.2-1ubuntu1 [1,042 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ natty/main gcc-4.5-multilib i386 4.5.2-1ubuntu1 [2,207 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ natty/main libstdc++6-4.5-dev i386 4.5.2-1ubuntu1 [1,527 kB]                                                     
Get:10 http://us.archive.ubuntu.com/ubuntu/ natty/main g++-4.5 i386 4.5.2-1ubuntu1 [5,495 kB]                                                               
Get:11 http://us.archive.ubuntu.com/ubuntu/ natty/main gcc-4.5 i386 4.5.2-1ubuntu1 [6,860 kB]                                                               
Get:12 http://us.archive.ubuntu.com/ubuntu/ natty/main cpp-4.5 i386 4.5.2-1ubuntu1 [4,143 kB]                                                               
Get:13 http://us.archive.ubuntu.com/ubuntu/ natty/main gcc-4.5-base i386 4.5.2-1ubuntu1 [12.0 kB]                                                           
Get:14 http://us.archive.ubuntu.com/ubuntu/ natty/main libstdc++6 i386 4.5.2-1ubuntu1 [333 kB]                                                              
Get:15 http://us.archive.ubuntu.com/ubuntu/ natty/main lib64stdc++6 i386 4.5.2-1ubuntu1 [326 kB]                                                            
Get:16 http://us.archive.ubuntu.com/ubuntu/ natty/main libgcc1 i386 1:4.5.2-1ubuntu1 [51.1 kB]                                                              
Get:17 http://us.archive.ubuntu.com/ubuntu/ natty/main libvte-common all 1:0.27.2-0ubuntu3 [24.5 kB]                                                        
Get:18 http://us.archive.ubuntu.com/ubuntu/ natty/main libvte9 i386 1:0.27.2-0ubuntu3 [334 kB]                                                              
Get:19 http://us.archive.ubuntu.com/ubuntu/ natty/main python-vte i386 1:0.27.2-0ubuntu3 [29.4 kB]                                                          
Get:20 http://us.archive.ubuntu.com/ubuntu/ natty/main update-manager all 1:0.145.10 [650 kB]                                                               
Get:21 http://us.archive.ubuntu.com/ubuntu/ natty/main update-manager-core i386 1:0.145.10 [154 kB]                                                         
Get:22 http://us.archive.ubuntu.com/ubuntu/ natty/main python-problem-report all 1.16-0ubuntu5 [27.9 kB]                                                    
Get:23 http://us.archive.ubuntu.com/ubuntu/ natty/main python-apport all 1.16-0ubuntu5 [103 kB]                                                             
Get:24 http://us.archive.ubuntu.com/ubuntu/ natty/main apport all 1.16-0ubuntu5 [53.6 kB]                                                                   
Get:25 http://us.archive.ubuntu.com/ubuntu/ natty/main apport-gtk all 1.16-0ubuntu5 [23.9 kB]                                                               
Get:26 http://us.archive.ubuntu.com/ubuntu/ natty/main libdecoration0 i386 1:0.9.2.1+glibmainloop3-0ubuntu5 [26.4 kB]                                       
Get:27 http://us.archive.ubuntu.com/ubuntu/ natty/main compiz-gnome i386 1:0.9.2.1+glibmainloop3-0ubuntu5 [73.7 kB]                                         
Get:28 http://us.archive.ubuntu.com/ubuntu/ natty/main compiz-plugins i386 1:0.9.2.1+glibmainloop3-0ubuntu5 [1,245 kB]                                      
Get:29 http://us.archive.ubuntu.com/ubuntu/ natty/main compiz-core i386 1:0.9.2.1+glibmainloop3-0ubuntu5 [266 kB]                                           
Get:30 http://us.archive.ubuntu.com/ubuntu/ natty/main compiz all 1:0.9.2.1+glibmainloop3-0ubuntu5 [6,006 B]                                                
Get:31 http://us.archive.ubuntu.com/ubuntu/ natty/main jockey-gtk all 0.6-0ubuntu4 [9,174 B]                                                                
Get:32 http://us.archive.ubuntu.com/ubuntu/ natty/main jockey-common all 0.6-0ubuntu4 [124 kB]                                                              
Get:33 http://us.archive.ubuntu.com/ubuntu/ natty/main launchpad-integration all 0.1.45 [8,686 B]                                                           
Get:34 http://us.archive.ubuntu.com/ubuntu/ natty/main liblaunchpad-integration-common all 0.1.45 [7,606 B]                                                 
Get:35 http://us.archive.ubuntu.com/ubuntu/ natty/main liblaunchpad-integration1 i386 0.1.45 [6,898 B]                                                      
Get:36 http://us.archive.ubuntu.com/ubuntu/ natty/main liblaunchpad-integration1.0-cil i386 0.1.45 [5,264 B]                                                
Get:37 http://us.archive.ubuntu.com/ubuntu/ natty/main liblpint-bonobo0 i386 0.1.45 [6,162 B]                                                               
Get:38 http://us.archive.ubuntu.com/ubuntu/ natty/main libxi-dev i386 2:1.3-6 [110 kB]                                                                      
Get:39 http://us.archive.ubuntu.com/ubuntu/ natty/main libxi6 i386 2:1.3-6 [28.6 kB]                                                                        
Get:40 http://us.archive.ubuntu.com/ubuntu/ natty/main nvidia-common i386 0.2.25 [12.1 kB]                                                                  
Get:41 http://us.archive.ubuntu.com/ubuntu/ natty/main openprinting-ppds all 20101217-0ubuntu1 [2,035 kB]                                                   
Get:42 http://us.archive.ubuntu.com/ubuntu/ natty/main python-launchpad-integration i386 0.1.45 [7,314 B]                                                   
Get:43 http://us.archive.ubuntu.com/ubuntu/ natty/main ttf-vlgothic all 20101218-1 [4,970 kB]                                                               
Get:44 http://us.archive.ubuntu.com/ubuntu/ natty/main unity-common all 3.2.8-0ubuntu1 [9,712 B]                                                            
Get:45 http://us.archive.ubuntu.com/ubuntu/ natty/main libiw30 i386 30~pre9-3ubuntu6 [19.3 kB]                                                              
Get:46 http://us.archive.ubuntu.com/ubuntu/ natty/main wireless-tools i386 30~pre9-3ubuntu6 [118 kB]                                                        
Get:47 http://us.archive.ubuntu.com/ubuntu/ natty/main xinput i386 1.5.3-1 [23.0 kB]                                                                        
Get:48 http://us.archive.ubuntu.com/ubuntu/ natty/main foomatic-db all 20101217-0ubuntu1 [620 kB]                                                           
Get:49 http://us.archive.ubuntu.com/ubuntu/ natty/universe libxerces-c28 i386 2.8.0+deb1-2build2 [1,319 kB]                                                 
Fetched 39.5 MB in 43s (918 kB/s)                                                                                                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 427887 files and directories currently installed.)
Preparing to replace ubuntu-sso-client 1.1.5-0ubuntu2 (using .../ubuntu-sso-client_1.1.7-0ubuntu1_all.deb) ...
Unpacking replacement ubuntu-sso-client ...
Preparing to replace lib64gcc1 1:4.5.1-12ubuntu1 (using .../lib64gcc1_1%3a4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement lib64gcc1 ...
Preparing to replace libgomp1 4.5.1-12ubuntu1 (using .../libgomp1_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement libgomp1 ...
Preparing to replace lib64gomp1 4.5.1-12ubuntu1 (using .../lib64gomp1_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement lib64gomp1 ...
Preparing to replace libgfortran3 4.5.1-12ubuntu1 (using .../libgfortran3_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement libgfortran3 ...
Preparing to replace gfortran-4.5 4.5.1-12ubuntu1 (using .../gfortran-4.5_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement gfortran-4.5 ...
Preparing to replace g++-4.5-multilib 4.5.1-12ubuntu1 (using .../g++-4.5-multilib_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement g++-4.5-multilib ...
Preparing to replace gcc-4.5-multilib 4.5.1-12ubuntu1 (using .../gcc-4.5-multilib_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement gcc-4.5-multilib ...
Preparing to replace libstdc++6-4.5-dev 4.5.1-12ubuntu1 (using .../libstdc++6-4.5-dev_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement libstdc++6-4.5-dev ...
Preparing to replace g++-4.5 4.5.1-12ubuntu1 (using .../g++-4.5_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement g++-4.5 ...
Preparing to replace gcc-4.5 4.5.1-12ubuntu1 (using .../gcc-4.5_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement gcc-4.5 ...
Preparing to replace cpp-4.5 4.5.1-12ubuntu1 (using .../cpp-4.5_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement cpp-4.5 ...
Preparing to replace gcc-4.5-base 4.5.1-12ubuntu1 (using .../gcc-4.5-base_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement gcc-4.5-base ...
Processing triggers for python-support ...
Processing triggers for man-db ...
Setting up gcc-4.5-base (4.5.2-1ubuntu1) ...
(Reading database ... 427887 files and directories currently installed.)
Preparing to replace libstdc++6 4.5.1-12ubuntu1 (using .../libstdc++6_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.5.2-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 427887 files and directories currently installed.)
Preparing to replace lib64stdc++6 4.5.1-12ubuntu1 (using .../lib64stdc++6_4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement lib64stdc++6 ...
Preparing to replace libgcc1 1:4.5.1-12ubuntu1 (using .../libgcc1_1%3a4.5.2-1ubuntu1_i386.deb) ...
Unpacking replacement libgcc1 ...
Setting up libgcc1 (1:4.5.2-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 427887 files and directories currently installed.)
Preparing to replace libvte-common 1:0.27.2-0ubuntu1 (using .../libvte-common_1%3a0.27.2-0ubuntu3_all.deb) ...
Unpacking replacement libvte-common ...
Preparing to replace libvte9 1:0.27.2-0ubuntu1 (using .../libvte9_1%3a0.27.2-0ubuntu3_i386.deb) ...
Unpacking replacement libvte9 ...
Preparing to replace python-vte 1:0.27.2-0ubuntu1 (using .../python-vte_1%3a0.27.2-0ubuntu3_i386.deb) ...
Unpacking replacement python-vte ...
Preparing to replace update-manager 1:0.145.9 (using .../update-manager_1%3a0.145.10_all.deb) ...
Unpacking replacement update-manager ...
Preparing to replace update-manager-core 1:0.145.9 (using .../update-manager-core_1%3a0.145.10_i386.deb) ...
Unpacking replacement update-manager-core ...
Preparing to replace python-problem-report 1.16-0ubuntu4 (using .../python-problem-report_1.16-0ubuntu5_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 1.16-0ubuntu4 (using .../python-apport_1.16-0ubuntu5_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 1.16-0ubuntu4 (using .../apport_1.16-0ubuntu5_all.deb) ...
stop: Unknown instance: 
Unpacking replacement apport ...
Preparing to replace apport-gtk 1.16-0ubuntu4 (using .../apport-gtk_1.16-0ubuntu5_all.deb) ...
Unpacking replacement apport-gtk ...
Preparing to replace libdecoration0 1:0.9.2.1+glibmainloop3-0ubuntu4 (using .../libdecoration0_1%3a0.9.2.1+glibmainloop3-0ubuntu5_i386.deb) ...
Unpacking replacement libdecoration0 ...
Preparing to replace compiz-gnome 1:0.9.2.1+glibmainloop3-0ubuntu4 (using .../compiz-gnome_1%3a0.9.2.1+glibmainloop3-0ubuntu5_i386.deb) ...
Unpacking replacement compiz-gnome ...
Preparing to replace compiz-plugins 1:0.9.2.1+glibmainloop3-0ubuntu4 (using .../compiz-plugins_1%3a0.9.2.1+glibmainloop3-0ubuntu5_i386.deb) ...
Unpacking replacement compiz-plugins ...
Preparing to replace compiz-core 1:0.9.2.1+glibmainloop3-0ubuntu4 (using .../compiz-core_1%3a0.9.2.1+glibmainloop3-0ubuntu5_i386.deb) ...
Unpacking replacement compiz-core ...
Preparing to replace compiz 1:0.9.2.1+glibmainloop3-0ubuntu4 (using .../compiz_1%3a0.9.2.1+glibmainloop3-0ubuntu5_all.deb) ...
Unpacking replacement compiz ...
Preparing to replace jockey-gtk 0.6-0ubuntu3 (using .../jockey-gtk_0.6-0ubuntu4_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.6-0ubuntu3 (using .../jockey-common_0.6-0ubuntu4_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace launchpad-integration 0.1.44 (using .../launchpad-integration_0.1.45_all.deb) ...
Unpacking replacement launchpad-integration ...
Preparing to replace liblaunchpad-integration-common 0.1.44 (using .../liblaunchpad-integration-common_0.1.45_all.deb) ...
Unpacking replacement liblaunchpad-integration-common ...
Preparing to replace liblaunchpad-integration1 0.1.44 (using .../liblaunchpad-integration1_0.1.45_i386.deb) ...
Unpacking replacement liblaunchpad-integration1 ...
Preparing to replace liblaunchpad-integration1.0-cil 0.1.44 (using .../liblaunchpad-integration1.0-cil_0.1.45_i386.deb) ...
Removing liblaunchpad-integration1.0-cil from Mono
Unpacking replacement liblaunchpad-integration1.0-cil ...
Preparing to replace liblpint-bonobo0 0.1.44 (using .../liblpint-bonobo0_0.1.45_i386.deb) ...
Unpacking replacement liblpint-bonobo0 ...
Preparing to replace libxi-dev 2:1.3-5 (using .../libxi-dev_2%3a1.3-6_i386.deb) ...
Unpacking replacement libxi-dev ...
Preparing to replace libxi6 2:1.3-5 (using .../libxi6_2%3a1.3-6_i386.deb) ...
Unpacking replacement libxi6 ...
Preparing to replace nvidia-common 0.2.24build1 (using .../nvidia-common_0.2.25_i386.deb) ...
Unpacking replacement nvidia-common ...
Preparing to replace openprinting-ppds 20100915-0ubuntu4 (using .../openprinting-ppds_20101217-0ubuntu1_all.deb) ...
Unpacking replacement openprinting-ppds ...
Preparing to replace python-launchpad-integration 0.1.44 (using .../python-launchpad-integration_0.1.45_i386.deb) ...
Unpacking replacement python-launchpad-integration ...
Preparing to replace ttf-vlgothic 20101022-1 (using .../ttf-vlgothic_20101218-1_all.deb) ...
Unpacking replacement ttf-vlgothic ...
Preparing to replace unity-common 3.2.6-0ubuntu2 (using .../unity-common_3.2.8-0ubuntu1_all.deb) ...
Unpacking replacement unity-common ...
Preparing to replace libiw30 30~pre9-3ubuntu5 (using .../libiw30_30~pre9-3ubuntu6_i386.deb) ...
Unpacking replacement libiw30 ...
Preparing to replace wireless-tools 30~pre9-3ubuntu5 (using .../wireless-tools_30~pre9-3ubuntu6_i386.deb) ...
Unpacking replacement wireless-tools ...
Preparing to replace xinput 1.5.2-1 (using .../xinput_1.5.3-1_i386.deb) ...
Unpacking replacement xinput ...
Preparing to replace foomatic-db 20100915-0ubuntu4 (using .../foomatic-db_20101217-0ubuntu1_all.deb) ...
Unpacking replacement foomatic-db ...
Preparing to replace libxerces-c28 2.8.0+deb1-2build1 (using .../libxerces-c28_2.8.0+deb1-2build2_i386.deb) ...
Unpacking replacement libxerces-c28 ...
Processing triggers for python-support ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gconf2 ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'fonts/package'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for fontconfig ...
Processing triggers for libglib2.0-0 ...
Processing triggers for python-support ...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic                                                                                      
 *       virtualbox-ose (3.2.12)...                                                                                                                   [ OK ] 
 *       blcr (0.8.2)...                                                                                                                              [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-10-generic (2.6.37-10.24) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
 * dkms: running auto installation service for kernel 2.6.37-10-generic                                                                                      
 *       virtualbox-ose (3.2.12)...                                                                                                                   [ OK ] 
 *       blcr (0.8.2)...                                                                                                                              [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.37-9-generic (2.6.37-9.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-9-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
 * dkms: running auto installation service for kernel 2.6.37-9-generic                                                                                       
 *       virtualbox-ose (3.2.12)...                                                                                                                   [ OK ] 
 *       blcr (0.8.2)...                                                                                                                              [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-9-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-9-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-10-generic; however:
  Package linux-image-2.6.37-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.10.12); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-sso-client (1.1.7-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Setting up lib64gcc1 (1:4.5.2-1ubuntu1) ...
Setting up libgomp1 (4.5.2-1ubuntu1) ...
Setting up lib64gomp1 (4.5.2-1ubuntu1) ...
Setting up libgfortran3 (4.5.2-1ubuntu1) ...
Setting up cpp-4.5 (4.5.2-1ubuntu1) ...
Setting up gcc-4.5 (4.5.2-1ubuntu1) ...
Setting up gfortran-4.5 (4.5.2-1ubuntu1) ...
Setting up gcc-4.5-multilib (4.5.2-1ubuntu1) ...
Setting up lib64stdc++6 (4.5.2-1ubuntu1) ...
Setting up libvte-common (1:0.27.2-0ubuntu3) ...
Setting up libvte9 (1:0.27.2-0ubuntu3) ...
Setting up python-vte (1:0.27.2-0ubuntu3) ...
Setting up update-manager-core (1:0.145.10) ...
Setting up update-manager (1:0.145.10) ...
Setting up python-problem-report (1.16-0ubuntu5) ...
Setting up libdecoration0 (1:0.9.2.1+glibmainloop3-0ubuntu5) ...
Setting up compiz-core (1:0.9.2.1+glibmainloop3-0ubuntu5) ...
Setting up compiz-plugins (1:0.9.2.1+glibmainloop3-0ubuntu5) ...
Setting up compiz-gnome (1:0.9.2.1+glibmainloop3-0ubuntu5) ...
Setting up compiz (1:0.9.2.1+glibmainloop3-0ubuntu5) ...
Setting up jockey-common (0.6-0ubuntu4) ...
Setting up launchpad-integration (0.1.45) ...
Setting up liblaunchpad-integration-common (0.1.45) ...
Setting up liblaunchpad-integration1 (0.1.45) ...
Setting up liblaunchpad-integration1.0-cil (0.1.45) ...
* Installing 1 assembly from liblaunchpad-integration1.0-cil into Mono
Setting up liblpint-bonobo0 (0.1.45) ...
Setting up libxi6 (2:1.3-6) ...
Setting up libxi-dev (2:1.3-6) ...
Setting up nvidia-common (0.2.25) ...
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
dpkg: error processing nvidia-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up openprinting-ppds (20101217-0ubuntu1) ...
Setting up python-launchpad-integration (0.1.45) ...
Setting up ttf-vlgothic (20101218-1) ...
Setting up unity-common (3.2.8-0ubuntu1) ...
Setting up libiw30 (30~pre9-3ubuntu6) ...
Setting up wireless-tools (30~pre9-3ubuntu6) ...
Setting up xinput (1.5.3-1) ...
Setting up foomatic-db (20101217-0ubuntu1) ...
Setting up libxerces-c28 (2.8.0+deb1-2build2) ...
Processing triggers for python-central ...
Setting up python-apport (1.16-0ubuntu5) ...
Setting up jockey-gtk (0.6-0ubuntu4) ...
Processing triggers for python-central ...
Setting up apport (1.16-0ubuntu5) ...
start: Job failed to start
Processing triggers for python-central ...
Setting up apport-gtk (1.16-0ubuntu5) ...
Setting up libstdc++6-4.5-dev (4.5.2-1ubuntu1) ...
Setting up g++-4.5 (4.5.2-1ubuntu1) ...
Setting up g++-4.5-multilib (4.5.2-1ubuntu1) ...
Processing triggers for python-support ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.37-10-generic
 linux-image-2.6.37-9-generic
 linux-image-generic
 linux-generic
 nvidia-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by BicyclerBoy on 2010-12-18
How did you manage to end up with an old grub version (prior to 10.04) ?

I don't know if this would break the kernel updating but I would be very concerned...

I suggest you read/follow through the Ubuntu 10.04 upgrade/release notes regarding the grub update procedure/debugging.
(grub was update/upgraded from 9.10 to 10.04)

Only after you have latest grub installed/sorted continue with original problem.

---

### Post by arpbvn on 2010-12-19
i have downloaded the debien package from "www.package.ubuntu.***".
i opened in package manager. it displays dependency failed error.

what can i do.i have no internet. i want to install offline.
please tell me a solution.

is there any ***mand to over***e dependency error??????

is so plz infom me.

is there any better web for dounloading full package from net and install offline????????

reply to arpbvn@gmail.***

---

### Post by sikander3786 on 2010-12-19
@**rajeeja**:

Seems to be a problem with your Grub and menu.lst. Please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

---

### Post by rajeeja on 2010-12-19
> **sikander3786 said:**
> @**rajeeja**:

Seems to be a problem with your Grub and menu.lst. Please post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)


Please find the results attached.

@question about grub, this happened, because I ran:
sudo aptitude update
sudo aptitude -f install

If you look at my first post all this info is there.

Many thanks,

---

### Post by sikander3786 on 2010-12-19
OP's Results.txt:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 2048. But according to the info from fdisk, 
                       sda1 starts at sector 385478656.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.***

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /boot/bcd /ntldr /NTDETECT.***

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Unknown
    Boot sector info:  
    Operating System:  Ubuntu natty (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *    385,478,656   390,719,487     5,240,832   c W95 FAT32 (LBA)
/dev/sda2             178,176    21,149,695    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,149,696   263,050,185   241,900,490   7 HPFS/NTFS
/dev/sda4         263,064,436   390,719,487   127,655,052   f W95 Ext d (LBA)
/dev/sda5         385,478,656   390,719,487     5,240,832  dd Dell Media Direct
/dev/sda6         263,064,438   380,387,069   117,322,632  83 Linux
/dev/sda7         380,387,133   385,463,609     5,076,477  82 Linux swap / Solaris

/dev/sda1 overlaps with /dev/sda4

blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F469-2D45                              vfat       MEDIADIRECT                   
/dev/sda2        66B86168B86137A7                       ntfs       RECOVERY                      
/dev/sda3        BA86643F8663FA71                       ntfs       OS                            
/dev/sda4: PTTYPE="dos" 
/dev/sda5        F469-2D45                              vfat       MEDIADIRECT                   
/dev/sda6        2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028   ext3                                     
/dev/sda7        dcddd110-a49c-4d86-84a6-7c7eec4b8131   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext3       (rw,relatime,errors=remount-ro,***mit=0)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

================================ sda5/boot.ini: ================================

[boot loader]
timeout=0
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Embedded" /fastdetect /KERNEL=NTOSBOOT.EXE /maxmem=768

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  set matches_file=${prefix}/gfxblacklist.lst
  set class_match=3
  if lua ${prefix}/hwmatch.lua; then
    if [ ${match} = 0 ]; then
      set linux_gfx_mode=keep
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=text
  fi
else
  set linux_gfx_mode=text
fi
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	echo	'Loading Linux 2.6.35-23-generic ...'
	linux	/boot/vmlinuz-2.6.35-23-generic root=UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-23-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-19-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	echo	'Loading Linux 2.6.31-19-generic ...'
	linux	/boot/vmlinuz-2.6.31-19-generic root=UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-19-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos6)'
	search --no-floppy --fs-uuid --set=root 2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f469-2d45
	chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda3)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root BA86643F8663FA71
	drivemap -s (hd0) ${root}
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda5)" --class windows --class os {
	insmod part_msdos
	insmod fat
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root f469-2d45
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this ***ment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=2d1fd00c-d46d-4f3e-8cc8-1f06a87bf028 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=dcddd110-a49c-4d86-84a6-7c7eec4b8131 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 156.7GB: boot/grub/core.img
 156.7GB: boot/grub/grub.cfg
 156.7GB: boot/initrd.img-2.6.31-19-generic
 156.8GB: boot/initrd.img-2.6.35-22-generic
 156.7GB: boot/initrd.img-2.6.35-23-generic
 156.7GB: boot/initrd.img-2.6.37-10-generic
 156.8GB: boot/initrd.img-2.6.37-9-generic
 156.7GB: boot/vmlinuz-2.6.31-19-generic
 156.7GB: boot/vmlinuz-2.6.35-22-generic
 156.7GB: boot/vmlinuz-2.6.35-23-generic
 156.8GB: boot/vmlinuz-2.6.37-10-generic
 156.7GB: boot/vmlinuz-2.6.37-9-generic
 156.8GB: initrd.img
 156.7GB: initrd.img.old
 156.7GB: vmlinuz
 156.8GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda6

00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 a6 68 41 12  |.............hA.|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 24 12  |...<.u........$.|
000001c0  0f 09 00 be bd 7d 31 c0  cd 13 46 8a 0c 80 f9 00  |.....}1...F.....|
000001d0  75 0f be da 7d e8 da ff  eb a4 46 6c 6f 70 70 79  |u...}.....Floppy|
000001e0  00 bb 00 70 b8 01 02 b5  00 b6 00 cd 13 72 d7 b6  |...p.........r..|
000001f0  01 b5 4f e9 03 ff 00 00  00 00 00 00 00 00 55 aa  |..O...........U.|
00000200

```

---

### Post by sikander3786 on 2010-12-19
You are using Grub2 and that seems pretty in tact till now. Did you try removing the Grub Legacy?

```
sudo apt-get remove --purge grub
```

---

### Post by drs305 on 2010-12-20
rajeeja,

One of your system's main problems, if you haven't corrected them, is that your sources.list has references for both natty and maverick. I think your OS is confused as to what it really is and I don't know if it can sort itself out. But you should try anyway. You've indicated to me that lsb_release returns "Natty" so I'd try changing all the references to "natty" and run "sudo apt-get update" to refresh the repository lists.

Your system is also still confused about grub. Yes, I would recommend purging and reinstalling grub, grub-pc and grub-common. If you can boot into your real installation (not LiveCD),

Make sure you have an Internet connection, then:
```
sudo apt-get purge grub          # Will remove grub
sudo apt-get purge grub-common   # Will remove grub-pc and grub-common
sudo apt-get install grub-pc     # Will install grub-common and grub-pc
```

---

### Post by rajeeja on 2010-12-20
I've change my source.list and replaced all maverick to natty.

I'm back to grub rescue prompt>

none of the commands you mentioned went through smoothly. Lilo was deleted in the process, so now nothing works, life has come back to booting from the CD.

Some of the messages I got were:

blcr( 0.8.2) fail

It was looking for nvdia or failing in that step, i have a intel integrated graphics card, so the script finding the graphics is buggy (probably).

Even thought things failed since I had purged grub, i kept on going.

Please let me know.

---

### Post by drs305 on 2010-12-20
You should be able to put lilo back on from the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

A fresh installation normally takes less than an hour. I know you've been trying to salvage this for more than a week. I think it's time to recover anything you need to save from the Ubuntu partition and reformat the partition and try again. I'd stick to either Maverick or Lucid LTS and leave Natty alone until it's released in April. Alpha's are not really meant for anything but testing on a non-production computer/partition.

---

### Post by rajeeja on 2010-12-20
> **drs305 said:**
> You should be able to put lilo back on from the LiveCD:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

A fresh installation normally takes less than an hour. I know you've been trying to salvage this for more than a week. I think it's time to recover anything you need to save from the Ubuntu partition and reformat the partition and try again. I'd stick to either Maverick or Lucid LTS and leave Natty alone until it's released in April. Alpha's are not really meant for anything but testing on a non-production computer/partition.

Cant install lilo

```
ubuntu@ubuntu:~$ 

**ubuntu@ubuntu:~$** sudo mount /dev/sda6 /mnt  # Example: sudo mount /dev/sda5 /mnt 
**ubuntu@ubuntu:~$** sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track..
Installation finished. No error reported.
**ubuntu@ubuntu:~$** sudo mount /dev/sda6 /mnt/temp
**ubuntu@ubuntu:~$ **for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt/temp$i;  done
**ubuntu@ubuntu:~$** sudo cp /etc/resolv.conf /mnt/temp/etc/resolv.conf  # May be required to connect to the Internet.
**ubuntu@ubuntu:~$** sudo chroot /mnt/temp
**root@ubuntu:/# **sudo apt-get install lilo
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
do Suggested packages:
  lilo-doc
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  lilo
0 upgraded, 1 newly installed, 1 to remove and 46 not upgraded.
6 not fully installed or removed.
Need to get 356 kB of archives.
After this operation, 1,487 kB disk space will be freed.
Do you want to continue [YY    
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main lilo i386 1:22.8-9ubuntu1 [356 kB]
Fetched 356 kB in 1s (312 kB/s)
sPreconfiguring packages ...
(Reading database ... 428064 files and directories currently installed.)
Removing grub-pc ...
Processing triggers for man-db ...
Selecting previously deselected package lilo.
(Reading database ... 427826 files and directories currently installed.)
Unpacking lilo (from .../lilo_1%3a22.8-9ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.41) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-23.40 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
 * dkms: running auto installation service for kernel 2.6.35-23-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.37-10-generic (2.6.37-10.24) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
 * dkms: running auto installation service for kernel 2.6.37-10-generic         
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-10-generic /boot/vmlinuz-2.6.37-10-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.37-9-generic (2.6.37-9.23) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.37-9-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
 * dkms: running auto installation service for kernel 2.6.37-9-generic          
 *       virtualbox-ose (3.2.12)...                                      [ OK ] 
 *       blcr (0.8.2)...                                                 [fail] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.37-9-generic /boot/vmlinuz-2.6.37-9-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.37-9-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.37-9-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.37-10-generic; however:
  Package linux-image-2.6.37-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.37.10.12); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-common (0.2.25) ...
No apport report written because MaxReports is reached already
                                                              Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True, verbose=True)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 142, in getData
    driver_version = self.__get_value_from_name(package.name.split('-', 1)[1])
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __get_value_from_name
    return self.__driver_aliases.get(name, int(name))
ValueError: invalid literal for int() with base 10: 'current'
dpkg: error processing nvidia-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Setting up lilo (1:22.8-9ubuntu1) ...
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.37-10-generic
 linux-image-2.6.37-9-generic
 linux-image-generic
 linux-generic
 nvidia-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/# grub -v
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
**root@ubuntu:/# grub-install -v**
The program 'grub-install' can be found in the following packages:
 * grub
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-pc
 * lupin-support
 * grub-coreboot
 * grub-ieee1275
Try: apt-get install <selected package>

```

---

### Post by rajeeja on 2010-12-21
I'm able to boot windows and see a grub menu with new kernels:

2.6.37.10
2.6.37.9

They boot to a blank screen, probably because of graphics card detection issues, not sure why it picked nvdia when its intel integrated.

the old ones are:
2.6.35.23
2.6.35.22
2.6.35.19

these 3 kernels at times boot to a screen without any panel, from the terminal i run gnome-panel to get it to a working state

Oh well, may be give it some more time...:)

---

