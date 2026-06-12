---
title: "Update and Installation ERROR"
date: 2011-02-24
forum: General Help
---

### Post by Jerriy on 2011-02-24
Currently whenever the auto-update comes and I let it go ahead I get the message that the update has failed to finish successfully.

I also get a similar problem when I try to install programmes: the synaptic starts the installation process but then I get a fail message that is similar to the one I get when the update manager fails to do it's work 

Here below is an image of the "fail" message

How does that get fixed? 

Thanks in advance

---

### Post by plucky on 2011-02-24
Try from a terminal ```
sudo apt-get update
sudo apt-get install -f
```

Post back any errors to the forum from each command.

Good luck

---

### Post by dino99 on 2011-02-24
sudo rm /var/cache/apt/archives/*

then update upgrade again

---

### Post by Jerriy on 2011-02-24
> **plucky said:**
> Try from a terminal ```
sudo apt-get update
sudo apt-get install -f
```Post back any errors to the forum from each command.

Good luckSudo apt-get update results:

```
:~$ sudo apt-get update
Hit http://be.archive.ubuntu.com lucid-backports Release.gpg
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://be.archive.ubuntu.com lucid-backports Release
Hit http://archive.ubuntu.com lucid Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                       
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Hit http://archive.ubuntu.com lucid-security Release.gpg             
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages
Hit http://archive.ubuntu.com lucid-updates Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-backports Release.gpg
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Hit http://be.archive.ubuntu.com lucid-backports/main Sources        
Hit http://archive.canonical.com lucid/partner Sources               
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Hit http://be.archive.ubuntu.com lucid-backports/restricted Sources
Hit http://be.archive.ubuntu.com lucid-backports/universe Sources
Hit http://archive.ubuntu.com lucid Release    
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid-updates Release                  
Hit http://archive.ubuntu.com lucid-backports Release                
Hit http://be.archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-backports/restricted Packages
Hit http://archive.ubuntu.com lucid-backports/main Packages
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/universe Packages
Reading package lists... Done

```

Sudo apt-get install -f results:

```
:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-tagpy python-pyasn1 libpackagekit-glib2-12 kpackagekit
  python-clientform libboost-program-options1.40.0 libswt-cairo-gtk-3.5-jni
  libkleo4 phonon mysql-client-core-5.1 libswt-mozilla-gtk-3.5-jni
  python-mechanize python-utidylib kdesudo python-configobj
  libpackagekit-qt-12 python-beautifulsoup libakonadiprivate1
  mysql-server-core-5.1 install-package libmono-messaging2.0-cil
  libtidy-0.99-0 libkpgp4 libmono-system-messaging2.0-cil libkdepim4
  python-twisted-conch python-louie python-feedparser python-nevow
  python-packagekit python-epsilon libgdata6 packagekit gdebi-kde python-axiom
  software-properties-kde kdepimlibs5 python-coherence gromit akonadi-server
  update-manager-kde packagekit-backend-apt libswt-gnome-gtk-3.5-jni
  python-chardet kdepimlibs-data python-kde4 libgdata-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 18 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.32-28-generic (2.6.32-28.55) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-28-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-28-generic
Found kernel: /boot/vmlinuz-2.6.32-27-generic
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-28-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-28-generic; however:
  Package linux-image-2.6.32-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.28.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-28-generic (2.6.32-28.55) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                            Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-28-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-28-generic; however:
  Package linux-headers-2.6.32-28-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-28-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-28-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Jerriy on 2011-02-24
> **dino99 said:**
> sudo rm /var/cache/apt/archives/*

then update upgrade again```
...:~$ sudo rm /var/cache/apt/archives/*

rm: cannot remove `/var/cache/apt/archives/partial': Is a directory
```

---

### Post by Jerriy on 2011-02-24
What does that all mean?

That files or directories are missing?

---

### Post by plucky on 2011-02-24
> **Jerriy said:**
> What does that all mean?

That files or directories are missing?

That command will not delete directories but will delete the files in the archives directory.Don't worry about it.

Try from the terminal ```
sudo apt-get remove linux-image-2.6.32-28-generic
``` and if that works and only if it works try ```
sudo apt-get update
sudo apt-get upgrade
``` and see if it still gives the same error.


Good Luck

---

### Post by Jerriy on 2011-02-24
> **plucky said:**
> That command will not delete directories but will delete the files in the archives directory.Don't worry about it.

Try from the terminal ```
sudo apt-get remove linux-image-2.6.32-28-generic
``` and if that works...That didn't seem to work:

```
...:~$ sudo apt-get remove linux-image-2.6.32-28-generic
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic linux-image-2.6.32-28-generic linux-image-generic
0 upgraded, 0 newly installed, 3 to remove and 18 not upgraded.
5 not fully installed or removed.
After this operation, 99.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 305701 files and directories currently installed.)
Removing linux-generic ...
Removing linux-image-generic ...
Removing linux-image-2.6.32-28-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
Uninstalling: nvidia-current 195.36.24 (2.6.32-28-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 195.36.24
Kernel:  2.6.32-28-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia-current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-28-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.
run-parts: executing /etc/kernel/prerm.d/last-good-boot 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-27-generic
Found kernel: /boot/vmlinuz-2.6.32-26-generic
Found kernel: /boot/vmlinuz-2.6.32-25-generic
Found kernel: /boot/vmlinuz-2.6.32-24-generic
Found kernel: /boot/vmlinuz-2.6.32-23-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Setting up linux-headers-2.6.32-28-generic (2.6.32-28.55) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-28-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-28-generic; however:
  Package linux-headers-2.6.32-28-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 linux-headers-2.6.32-28-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by plucky on 2011-02-25
> Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.32-28-generic

Seems the kernel did actually install.

> Removing linux-image-2.6.32-28-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 2.6.32-28-generic /boot/vmlinuz-2.6.32-28-generic

and you are running with the latest kernel.

Can you select the -27 kernel from the Grub list and boot into that?

Then run ```
sudo apt-get install -f
``` and post output.

---

