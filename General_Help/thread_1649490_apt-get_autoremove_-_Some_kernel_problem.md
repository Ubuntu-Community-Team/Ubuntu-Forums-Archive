---
title: "apt-get autoremove - Some kernel problem"
date: 2010-12-20
forum: General Help
---

### Post by kanishkdudeja on 2010-12-20
when i run:

```
sudo apt-get remove
```

or

```
sudo apt-get autoremove
```..

im presented with the following code..im not able to understand whats the problem..

```
kanishk@Inspiron-1525:~$ sudo apt-get autoremove
[sudo] password for kanishk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       vboxhost (3.2.12)...                                            [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-24-generic; however:
  Package linux-image-2.6.35-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.35-24-generic (2.6.35-24.42) ...
No apport report written because the error message indicates its a followup error from a previous failure.
 No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       vboxhost (3.2.12)...                                            [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-24-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-24-generic; however:
  Package linux-headers-2.6.35-24-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 linux-image-2.6.35-24-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.35-24-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by nebileix on 2010-12-20
What was u doing b4 this? upgrade?

---

### Post by kanishkdudeja on 2010-12-20
yeah.

---

### Post by nebileix on 2010-12-20
can u do [code]sudo apt-get upgrade[\code] again

---

### Post by kanishkdudeja on 2010-12-20
ok..

it shows this..

```
kanishk@Inspiron-1525:~$ sudo apt-get upgrade
[sudo] password for kanishk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       vboxhost (3.2.12)...                                            [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-24-generic; however:
  Package linux-image-2.6.35-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.35-24-generic (2.6.35-24.42) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
 * dkms: running auto installation service for kernel 2.6.35-24-generic         
 *       vboxhost (3.2.12)...                                            [ OK ] 
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-24-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-24-generic; however:
  Package linux-headers-2.6.35-24-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.35-24-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.35-24-generic
 linux-headers-generic

	  You have to configure "localepurge" with the command

	      dpkg-reconfigure localepurge

	  to make /usr/sbin/localepurge actually start to function.

	  Nothing to be done, exiting ...

E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by nebileix on 2010-12-20
hrm... never really encounter these thou... maybe u could try rebooting and use previous kernel to remove the upgrade.

---

### Post by kanishkdudeja on 2010-12-20
okay.. 

let me try it..

---

### Post by kanishkdudeja on 2010-12-20
when i reboot..

i dont see any options..

ubuntu directly boots..

---

### Post by Rednarb on 2010-12-20
Hold shift during boot to bring up grub2 menu.

---

### Post by mcduck on 2010-12-20
You could try this:

Start with:
```
sudo apt-get clean
```
(to remove cached packages, in case you got a corrupted download or something)

then:
```
sudo apt-get update && sudo apt-get upgrade
```
(try downloading the updated packages again and install them)

..and if that doesn't finish without errors then:
```
sudo apt-get -f install
```
(try to fix any install problems)

Also, to access the Grub menu (if it's hidden) you need to hold down the Shift key during boot.

---

### Post by rockfly12 on 2010-12-20
Same problem during a normal update of the system this morning.

I ran apt-get update then apt-get upgrade -f and it seems to have resolved it.

---

### Post by kanishkdudeja on 2010-12-20
the new kernel doesnt seem to have got installed.

in the grub menu only my previous kernel was showing up.

So now shud i run 

```
apt-get upgrade -f
```

or

```
sudo apt-get -f install
```

---

### Post by kanishkdudeja on 2010-12-20
bump.

---

### Post by kanishkdudeja on 2010-12-20
ive tried them both. 

the same error.

ive cleared the cache..

but when i run apt-get update..

it says no updates to be downloaded.

---

### Post by ezsit on 2010-12-20
> You have to configure "localepurge" with the command

	      dpkg-reconfigure localepurge

	  to make /usr/sbin/localepurge actually start to function.

	  Nothing to be done, exiting ...


Did you try doing what was suggested? Run

**sudo dpkg-reconfigure localepurge**

and see if that helps clear the problem.

---

### Post by Exilant on 2010-12-20
I'm suffering from the same problem, occurring since I did a dist-upgrade today.

```
sudo apt-get -f install
[sudo] password for goelzera: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-23-generic linux-headers-2.6.35-23
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-24-generic (2.6.35-24.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-24-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-24-generic; however:
  Package linux-image-2.6.35-24-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.24.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.35-24-generic (2.6.35-24.42) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                               Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-24-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-24-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.35-24-generic; however:
  Package linux-headers-2.6.35-24-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.35-24-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.35-24-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

and I don't have localepurge installed.  Hopefully it will be fixed soon.

---

### Post by Habitual on 2010-12-21
I use Karthick's script EVERY time I run an update and it fixes all my "errors" of a similar nature.

I trust it 100%

```

#!/bin/bash

OLDCONF=$(dpkg -l|grep "^rc"|awk '{print $2}')
CURKERNEL=$(uname -r|sed 's/-*[a-z]//g'|sed 's/-386//g')
LINUXPKG="linux-(image|headers|ubuntu-modules|restricted-modules)"
METALINUXPKG="linux-(image|headers|restricted-modules)-(generic|i386|server|common|rt|xen)"
OLDKERNELS=$(dpkg -l|awk '{print $2}'|grep -E $LINUXPKG |grep -vE $METALINUXPKG|grep -v $CURKERNEL)
YELLOW="\033[1;33m"
RED="\033[0;31m"
ENDCOLOR="\033[0m"

if [ $USER != root ]; then
  echo -e $RED"Error: must be root"
  echo -e $YELLOW"Exiting..."$ENDCOLOR
  exit 0
fi

echo -e $YELLOW"Cleaning apt cache..."$ENDCOLOR
aptitude clean

echo -e $YELLOW"Removing old config files..."$ENDCOLOR
sudo aptitude purge $OLDCONF

echo -e $YELLOW"Removing old kernels..."$ENDCOLOR
sudo aptitude purge $OLDKERNELS

echo -e $YELLOW"Emptying every trashes..."$ENDCOLOR
rm -rf /home/*/.local/share/Trash/*/** &> /dev/null
rm -rf /root/.local/share/Trash/*/** &> /dev/null

echo -e $YELLOW"Script Finished!"$ENDCOLOR

```

Copy the script and paste it in your text editor.And save the file with .sh extension(ie cleaner.sh)Right click the file choose properties>>permissions and check execute.

```

sudo bash /path/to/the/script

```

HTH.

---

### Post by kanishkdudeja on 2010-12-21
thanks a ton mate..:)

it worked.

@exilant..

try what habitual is saying..it works..!

---

### Post by mahdif62 on 2010-12-23
I managed to solve the problem by running this two commands:

sudo apt-get --purge remove nvidia-common
sudo apt-get -f install

---

### Post by Habitual on 2010-12-23
> **kanishkdudeja said:**
> thanks a ton mate..:)

it worked.

@exilant..

try what habitual is saying..it works..!

It's a "keeper" that's for sure!

Glad it worked out.

---

### Post by Exilant on 2010-12-26
> **mahdif62 said:**
> I managed to solve the problem by running this two commands:

sudo apt-get --purge remove nvidia-common
sudo apt-get -f install

that did it for me, too.  The script is certainly nice, however you should be aware of the side effects. If you execute it while an older kernel is installed, it might remove the more recent one, and with it metapackages like linux-image-generic. The result in this specific case of the new kernel failing to install might not be the desired outcome.

---

