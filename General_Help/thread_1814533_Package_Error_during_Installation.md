---
title: "Package Error during Installation"
date: 2011-07-29
forum: General Help
---

### Post by West201 on 2011-07-29
Every time I install package I get the following error, but the package still installs properly, it's just that the errors are started to get annoying. 

> installArchives() failed: Selecting previously deselected package libkonq5-templates.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 313573 files and directories currently installed.)
Unpacking libkonq5-templates (from .../libkonq5-templates_4%3a4.6.2-0ubuntu1_all.deb) ...
Selecting previously deselected package libkonq5a.
Unpacking libkonq5a (from .../libkonq5a_4%3a4.6.2-0ubuntu1_amd64.deb) ...
Selecting previously deselected package ark.
Unpacking ark (from .../ark_4%3a4.6.2-0ubuntu1.1_amd64.deb) ...
Selecting previously deselected package rar.
Unpacking rar (from .../rar_2%3a4.0.b3-1_amd64.deb) ...
Selecting previously deselected package unrar-free.
Unpacking unrar-free (from .../unrar-free_1%3a0.0.1+cvs20071127-1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for python-support ...
Setting up linux-image-2.6.38-11-generic (2.6.38-11.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic

 *       virtualbox-ose (4.0.4)...
   ...done.
 *       fglrx (8.840)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-11-generic; however:
  Package linux-image-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.38-11-generic (2.6.38-11.47) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic

 *       virtualbox-ose (4.0.4)...
   ...done.
 *       fglrx (8.840)...
   ...done.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-11-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.38-11-generic; however:
  Package linux-headers-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Setting up libkonq5-templates (4:4.6.2-0ubuntu1) ...
Setting up libkonq5a (4:4.6.2-0ubuntu1) ...
Setting up ark (4:4.6.2-0ubuntu1.1) ...
Setting up rar (2:4.0.b3-1) ...
Setting up unrar-free (1:0.0.1+cvs20071127-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.38-11-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.38-11-generic
 linux-headers-generic
Setting up linux-headers-2.6.38-11-generic (2.6.38-11.47) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic

 *       virtualbox-ose (4.0.4)...
   ...done.
 *       fglrx (8.840)...
   ...done.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-11-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-11-generic (2.6.38-11.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic

 *       virtualbox-ose (4.0.4)...
   ...done.
 *       fglrx (8.840)...
   ...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-11-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-11-generic; however:
  Package linux-image-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.38-11-generic; however:
  Package linux-headers-2.6.38-11-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured

---

### Post by West201 on 2011-07-29
Anyone knows why I'm getting his error ?

Sorry for bumping the thread

---

### Post by gagalago on 2011-08-06
I have the same error every update or installation with terminal or gui.
The packages are installed or up to date but it takes more time because of the error.
How can I fix this error?
```
&#9484;&#9472;[sigo@sigo-ubuntu:~]-[9:36:04]
&#9492;&#9472;> sudo apt-get upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
0 mis à jour, 0 nouvellement installés, 0 à enlever et 0 non mis à jour.
2 partiellement installés ou enlevés.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer [O/n]*? 
Paramétrage de linux-image-2.6.38-11-generic (2.6.38-11.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic

Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-11.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-11.47 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic         
 *       nvidia-current (270.41.06)...                                   [ OK ] 
 *       bcmwl (5.100.82.38+bdcom)...                                    [ OK ] 
 *       nvidia-173 (173.14.30)...                                       [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-11-generic.postinst line 1010.
dpkg*: erreur de traitement de linux-image-2.6.38-11-generic (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Paramétrage de linux-headers-2.6.38-11-generic (2.6.38-11.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
 * dkms: running auto installation service for kernel 2.6.38-11-generic         
 *       nvidia-current (270.41.06)...                                   [ OK ] 
 *       bcmwl (5.100.82.38+bdcom)...                                    [ OK ] 
 *       nvidia-173 (173.14.30)...                                       [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-11-generic /boot/vmlinuz-2.6.38-11-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-11-generic.postinst line 110.
dpkg*: erreur de traitement de linux-headers-2.6.38-11-generic (--configure)*:
 le sous-processus script post-installation installé a retourné une erreur de sortie d'état 2
Des erreurs ont été rencontrées pendant l'exécution*:
 linux-image-2.6.38-11-generic
 linux-headers-2.6.38-11-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by gagalago on 2011-08-07
the solution is simply : 
```
sudo apt-get remove nvidia-common
sudo apt-get install nvidia-common
```

---

### Post by West201 on 2011-08-14
> **gagalago said:**
> the solution is simply : 
```
sudo apt-get remove nvidia-common
sudo apt-get install nvidia-common
```

I got this script from the terminal 

```
jesse@jesse-vaio:~$ sudo apt-get remove nvidia-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  nvidia-common ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 217 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 365822 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing nvidia-common ...
Setting up dictionaries-common (1.11.5ubuntu1) ...
update-default-wordlist: Question empty but elements installed for class "wordlist"
  dictionaries-common/default-wordlist: return code: "0", value: ""
  Choices: , Manual symlink setting
  shared/packages-wordlist: return code: "10" owners/error: "shared/packages-wordlist doesn't exist"
  Installed elements: american (American English), british (British English)

  Please see "/usr/share/doc/dictionaries-common/README.problems", section
  "Debconf database corruption" for recovery info.

update-default-wordlist: Selected wordlist "" 
does not correspond to any installed package in the system
and no alternative wordlist could be selected.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
Errors were encountered while processing:
 dictionaries-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
jesse@jesse-vaio:~$ sudo apt-get install nvidia-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  nvidia-common
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 11.0 kB of archives.
After this operation, 156 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main nvidia-common amd64 1:0.2.32 [11.0 kB]
Fetched 11.0 kB in 0s (17.3 kB/s)  
Preconfiguring packages ...
Selecting previously deselected package nvidia-common.
(Reading database ... 365796 files and directories currently installed.)
Unpacking nvidia-common (from .../nvidia-common_1%3a0.2.32_amd64.deb) ...
Setting up dictionaries-common (1.11.5ubuntu1) ...
update-default-wordlist: Question empty but elements installed for class "wordlist"
  dictionaries-common/default-wordlist: return code: "0", value: ""
  Choices: , Manual symlink setting
  shared/packages-wordlist: return code: "10" owners/error: "shared/packages-wordlist doesn't exist"
  Installed elements: american (American English), british (British English)

  Please see "/usr/share/doc/dictionaries-common/README.problems", section
  "Debconf database corruption" for recovery info.

update-default-wordlist: Selected wordlist "" 
does not correspond to any installed package in the system
and no alternative wordlist could be selected.
dpkg: error processing dictionaries-common (--configure):
 subprocess installed post-installation script returned error exit status 255
Setting up nvidia-common (1:0.2.32) ...
Errors were encountered while processing:
 dictionaries-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

