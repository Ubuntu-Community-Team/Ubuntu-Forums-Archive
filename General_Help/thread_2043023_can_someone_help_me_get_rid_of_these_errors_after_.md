---
title: "can someone help me get rid of these errors after installs and removals"
date: 2012-08-15
forum: General Help
---

### Post by walker195 on 2012-08-15
```
installArchives() failed: Selecting previously unselected package stellarium-data.
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
(Reading database ... 364111 files and directories currently installed.)
Unpacking stellarium-data (from .../stellarium-data_0.11.0-1_all.deb) ...
Selecting previously unselected package stellarium.
Unpacking stellarium (from .../stellarium_0.11.0-1_amd64.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for menu ...
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up stellarium-data (0.11.0-1) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up stellarium (0.11.0-1) ...
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by sienile on 2012-08-15
What command gave that output?

---

### Post by walker195 on 2012-08-15
> **sienile said:**
> What command gave that output?

i installed stellarium from ubuntu software center it installed ok but gave that error its annoying and happens every time

---

### Post by oldos2er on 2012-08-16
Try ```
sudo apt-get clean

sudo apt-get update && sudo apt-get dist-upgrade
```
If there are more errors please post them here.

---

### Post by walker195 on 2012-08-16
this was my output i saw some errors in it.

```


alec@AlecsUbuntuBook:~$ sudo apt-get clean
[sudo] password for alec: 
alec@AlecsUbuntuBook:~$ sudo apt-get update && sudo apt-get dist-upgrade
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg                           
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release                               
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease [7,096 B]                
Get:5 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [1,229 B]                
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:9 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,222 B]                 
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release                     
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages                   
Ign [http://deb.opera.com](http://deb.opera.com) stable InRelease                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg [316 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [156 kB]      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources/DiffIndex               
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:13 [http://www.fbriere.net](http://www.fbriere.net) ./ InRelease [28.9 kB]                           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                                        
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release [11.9 kB]                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources/DiffIndex           
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free amd64 Packages                        
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [3,285 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [47.2 kB] 
Get:17 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release.gpg [836 B]            
Ign [http://www.fbriere.net](http://www.fbriere.net) ./ InRelease                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [39.7 kB]      
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [3,108 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [371 kB]
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free i386 Packages                         
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free TranslationIndex                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages/DiffIndex        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [1,950 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [10.2 kB]  
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,386 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [156 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:25 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources [8,484 B]                 
Get:26 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages [5,273 B]          
Get:27 [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages [5,273 B]           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages/DiffIndex    
Get:28 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb Release [7,244 B]              
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [6,755 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [122 kB]
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [8,677 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [375 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages/DiffIndex         
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Get:33 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [3,969 B]
Get:34 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [39.4 kB]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages/DiffIndex     
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [6,732 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [123 kB]
Get:37 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [2,180 B]
Get:38 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [160 kB] 
Get:39 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Sources [66.0 kB]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free TranslationIndex                
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [8,810 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US                     
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [180 kB]
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free TranslationIndex            
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en                        
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en [4,988 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [73.5 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en     
Get:48 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [3,968 B]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [39.6 kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Sources                         
Get:50 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,369 B]
Get:51 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [71 B]
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:55 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [74.2 kB]
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Sources                     
Get:56 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games amd64 Packages [78.0 kB] 
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free amd64 Packages                  
Get:57 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [24.5 kB]
Get:58 [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games i386 Packages [78.8 kB]  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free amd64 Packages              
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games TranslationIndex            
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free i386 Packages                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free i386 Packages               
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Err [http://www.fbriere.net](http://www.fbriere.net) ./ Sources                                          
  404  Not Found [IP: 208.94.116.178 80]
Err [http://www.fbriere.net](http://www.fbriere.net) ./ Packages                                         
  Error reading from server. Remote end closed connection [IP: 208.94.116.178 80]
Ign [http://www.fbriere.net](http://www.fbriere.net) ./ Translation-en_US                                
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Ign [http://www.fbriere.net](http://www.fbriere.net) ./ Translation-en                                   
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise InRelease                        
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg                      
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release                          
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en_US               
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Ign [http://archive.getdeb.net](http://archive.getdeb.net) precise-getdeb/games Translation-en              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/free Translation-en                  
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en_US           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) precise/non-free Translation-en              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages               
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex            
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages              
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main amd64 Packages
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main i386 Packages
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main TranslationIndex
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en_US
Ign [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise/main Translation-en
Fetched 2,464 kB in 59s (41.5 kB/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://www.fbriere.net](http://www.fbriere.net) ./ InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 479C9B0FD0E6E19C
W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://www.fbriere.net/debian/dists/unstable/./Sources](http://www.fbriere.net/debian/dists/unstable/./Sources)  404  Not Found [IP: 208.94.116.178 80]

W: Failed to fetch [http://www.fbriere.net/debian/dists/unstable/./Packages](http://www.fbriere.net/debian/dists/unstable/./Packages)  Error reading from server. Remote end closed connection [IP: 208.94.116.178 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
alec@AlecsUbuntuBook:~$
```

---

### Post by plucky on 2012-08-17
Open a terminal and post output for ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```

All the PPA's you have in your Software Sources do not have repositories for Precise Pangolin.Try disabling them and see what errors you now get.

Good luck

---

### Post by walker195 on 2012-08-17
this was my terminal output.



```
alec@AlecsUbuntuBook:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120425)]/ precise main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb [http://ppa.launchpad.net/openclonkdevteam/release/ubuntu](http://ppa.launchpad.net/openclonkdevteam/release/ubuntu) precise main
deb-src [http://ppa.launchpad.net/openclonkdevteam/release/ubuntu](http://ppa.launchpad.net/openclonkdevteam/release/ubuntu) precise main
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games
deb [http://www.fbriere.net/debian/dists/unstable](http://www.fbriere.net/debian/dists/unstable) ./
deb-src [http://www.fbriere.net/debian/dists/unstable](http://www.fbriere.net/debian/dists/unstable) ./
alec@AlecsUbuntuBook:~$ cat /etc/apt/sources.list.d/*.list
deb [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
deb-src [http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu](http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu) precise main
deb [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) precise main
deb-src [http://ppa.launchpad.net/ferramroberto/java/ubuntu](http://ppa.launchpad.net/ferramroberto/java/ubuntu) precise main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu - Ubuntu 12.04 "precise pangolin"
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) precise free non-free #Medibuntu (source) - Ubuntu 12.04 "precise pangolin"
deb [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main
deb-src [http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu](http://ppa.launchpad.net/mefrio-g/plymouthmanager/ubuntu) precise main
deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) precise main
deb-src [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) precise main
# This file makes sure that Opera Browser is kept up-to-date
# as part of regular system upgrades

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases)

# The line above will make sure you get all final public releases.
# Uncomment the following line if you want to get alpha and beta
# releases, too.

# deb [http://deb.opera.com/opera-beta/](http://deb.opera.com/opera-beta/) stable non-free #Opera Browser (beta releases)
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) precise-getdeb games
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/bionightmarelite/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/crossover-trial/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/crossover-trial/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-59/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-59/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-60/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/fullcircle-issue-60/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/lordofultima/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/lordofultima/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/spheres/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/spheres/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/tiberiumalliances/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/tiberiumalliances/ubuntu) precise main #Added by software-center; credentials stored in /etc/apt/auth.conf
deb [http://ppa.launchpad.net/sgringwe/beatbox/ubuntu](http://ppa.launchpad.net/sgringwe/beatbox/ubuntu) precise main
deb-src [http://ppa.launchpad.net/sgringwe/beatbox/ubuntu](http://ppa.launchpad.net/sgringwe/beatbox/ubuntu) precise main
deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) precise main
deb [http://ppa.launchpad.net/wallch/version-3-ppa/ubuntu](http://ppa.launchpad.net/wallch/version-3-ppa/ubuntu) precise main
deb-src [http://ppa.launchpad.net/wallch/version-3-ppa/ubuntu](http://ppa.launchpad.net/wallch/version-3-ppa/ubuntu) precise main
alec@AlecsUbuntuBook:~$
``` 



>this is the error i got after i tried to install assault cube same problem?...


```
installArchives() failed: Selecting previously unselected package assaultcube-data.
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
(Reading database ... 365672 files and directories currently installed.)
Unpacking assaultcube-data (from .../assaultcube-data_1.1.0.4+repack1-2_all.deb) ...
Selecting previously unselected package assaultcube.
Unpacking assaultcube (from .../assaultcube_1.1.0.4+dfsg2-1_amd64.deb) ...
Processing triggers for doc-base ...
Processing 1 added doc-base file...
Registering documents with scrollkeeper...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up assaultcube-data (1.1.0.4+repack1-2) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Setting up assaultcube (1.1.0.4+dfsg2-1) ...
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
```

---

### Post by plucky on 2012-08-17
Have you disabled the non-working repositories?

```
deb http://ppa.launchpad.net/mefrio-g/pl...manager/ubuntu precise main
deb-src http://ppa.launchpad.net/mefrio-g/pl...manager/ubuntu precise main
deb http://ppa.launchpad.net/noobslab/themes/ubuntu precise main
deb-src http://ppa.launchpad.net/noobslab/themes/ubuntu precise main
```

After you have done that,run ```
sudo apt-get clean
sudo apt-get update
sudo apt-get install -f
``` and post back any errors.

Post the output between [noparse]```
Your text
```[/noparse] brackets.

Good Luck

---

### Post by walker195 on 2012-08-17
this is what the terminal did



```
alec@AlecsUbuntuBook:~$ sudo apt-get clean
[sudo] password for alec: 
alec@AlecsUbuntuBook:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Ign http://archive.canonical.com precise InRelease                             
Ign http://extras.ubuntu.com precise InRelease                                 
Get:2 http://dl.google.com stable Release                                      
Ign http://security.ubuntu.com precise-security InRelease                      
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:3 http://packages.medibuntu.org precise InRelease [7,096 B]                
Ign http://deb.opera.com stable InRelease                                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Get:4 http://dl.google.com stable/main amd64 Packages [1,231 B]                
Get:5 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://archive.canonical.com precise Release.gpg                           
Get:6 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Get:7 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Ign http://packages.medibuntu.org precise InRelease                            
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://ppa.launchpad.net precise InRelease                                 
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:8 http://dl.google.com stable/main i386 Packages [1,235 B]                 
Hit http://deb.opera.com stable Release.gpg                                    
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                 
Ign http://dl.google.com stable/main TranslationIndex                          
Ign http://archive.getdeb.net precise-getdeb InRelease                         
Hit http://us.archive.ubuntu.com precise Release                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://archive.canonical.com precise Release                               
Get:9 http://security.ubuntu.com precise-security Release [49.6 kB]            
Ign http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Get:10 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Hit http://deb.opera.com stable Release                                        
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://archive.canonical.com precise/partner Sources                       
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Ign http://packages.medibuntu.org precise/free Sources/DiffIndex               
Hit http://us.archive.ubuntu.com precise-backports Release                     
Get:11 http://www.fbriere.net ./ InRelease [28.9 kB]                           
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise Release                                   
Hit http://deb.opera.com stable/non-free amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:12 http://us.archive.ubuntu.com precise-updates/main Sources [156 kB]      
Ign http://packages.medibuntu.org precise/non-free Sources/DiffIndex           
Hit http://deb.opera.com stable/non-free i386 Packages                         
Ign http://deb.opera.com stable/non-free TranslationIndex                      
Ign http://www.fbriere.net ./ InRelease                                        
Get:13 http://archive.getdeb.net precise-getdeb Release.gpg [836 B]            
Get:14 http://security.ubuntu.com precise-security/main Sources [39.7 kB]      
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:15 http://us.archive.ubuntu.com precise-updates/restricted Sources [3,285 B]
Get:16 http://us.archive.ubuntu.com precise-updates/universe Sources [47.6 kB] 
Ign http://packages.medibuntu.org precise/free amd64 Packages/DiffIndex        
Ign https://private-ppa.launchpad.net precise InRelease                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse Sources [3,108 B]
Get:18 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [371 kB]
Get:19 http://security.ubuntu.com precise-security/restricted Sources [1,950 B]
Get:20 http://security.ubuntu.com precise-security/universe Sources [10.2 kB]  
Get:21 http://security.ubuntu.com precise-security/multiverse Sources [1,386 B]
Get:22 http://security.ubuntu.com precise-security/main amd64 Packages [156 kB]
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Ign http://packages.medibuntu.org precise/non-free amd64 Packages/DiffIndex    
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:23 http://archive.getdeb.net precise-getdeb Release [7,244 B]              
Get:24 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:25 http://security.ubuntu.com precise-security/universe amd64 Packages [39.4 kB]
Get:26 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,180 B]
Get:27 http://security.ubuntu.com precise-security/main i386 Packages [160 kB] 
Get:28 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [6,755 B]
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex         
Get:29 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [123 kB]
Ign https://private-ppa.launchpad.net precise InRelease                        
Get:30 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Get:31 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,677 B]
Get:32 http://us.archive.ubuntu.com precise-updates/main i386 Packages [375 kB]
Get:33 http://security.ubuntu.com precise-security/universe i386 Packages [39.6 kB]
Get:34 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Ign http://extras.ubuntu.com precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://deb.opera.com stable/non-free Translation-en_US                     
Ign http://deb.opera.com stable/non-free Translation-en                        
Ign https://private-ppa.launchpad.net precise InRelease                        
Get:35 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [6,732 B]
Get:36 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [123 kB]
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Get:37 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [8,810 B]
Get:38 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:39 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:40 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:41 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://us.archive.ubuntu.com precise-backports/main Sources                
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources          
Hit http://us.archive.ubuntu.com precise-backports/universe Sources            
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources          
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages         
Err http://ppa.launchpad.net precise/main Sources                              
  404  Not Found
Err http://ppa.launchpad.net precise/main amd64 Packages                       
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages                        
  404  Not Found
Hit http://packages.medibuntu.org precise/free Sources                         
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Get:42 http://us.archive.ubuntu.com precise-updates/main Translation-en [180 kB]
Hit http://packages.medibuntu.org precise/non-free Sources                     
Ign https://private-ppa.launchpad.net precise InRelease                        
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Get:43 http://us.archive.ubuntu.com precise-updates/universe Translation-en [73.7 kB]
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign https://private-ppa.launchpad.net precise InRelease                        
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Ign https://private-ppa.launchpad.net precise InRelease                        
Err http://www.fbriere.net ./ Sources                                          
  404  Not Found [IP: 208.94.117.25 80]
Err http://www.fbriere.net ./ Packages                                         
  Error reading from server. Remote end closed connection [IP: 208.94.117.25 80]
Ign http://www.fbriere.net ./ Translation-en_US                  
Err http://www.fbriere.net ./ Translation-en                                   
  Error reading from server. Remote end closed connection [IP: 208.94.117.25 80]
Ign https://private-ppa.launchpad.net precise InRelease                        
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:44 http://archive.getdeb.net precise-getdeb/games Sources [65.9 kB]        
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Get:45 https://private-ppa.launchpad.net precise Release.gpg [316 B]           
Hit https://private-ppa.launchpad.net precise Release.gpg                      
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Hit https://private-ppa.launchpad.net precise Release                          
Get:46 http://archive.getdeb.net precise-getdeb/games amd64 Packages [78.1 kB] 
Hit https://private-ppa.launchpad.net precise Release                          
Get:47 https://private-ppa.launchpad.net precise Release [11.9 kB]             
Hit https://private-ppa.launchpad.net precise Release                          
Get:48 http://archive.getdeb.net precise-getdeb/games i386 Packages [78.9 kB]  
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Ign http://archive.getdeb.net precise-getdeb/games TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign http://packages.medibuntu.org precise/free Translation-en                  
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://packages.medibuntu.org precise/non-free Translation-en_US           
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Ign http://archive.getdeb.net precise-getdeb/games Translation-en_US           
Get:49 https://private-ppa.launchpad.net precise/main amd64 Packages [629 B]   
Get:50 https://private-ppa.launchpad.net precise/main i386 Packages [931 B]    
Ign http://archive.getdeb.net precise-getdeb/games Translation-en              
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
Hit https://private-ppa.launchpad.net precise/main amd64 Packages              
Hit https://private-ppa.launchpad.net precise/main i386 Packages               
Ign https://private-ppa.launchpad.net precise/main TranslationIndex            
100% [Working]                                                       257 B/s 0s^100% [Working]                                                       257 B/s 0s^Ign https://private-ppa.launchpad.net precise/main Translation-en_US           
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Ign https://private-ppa.launchpad.net precise/main Translation-en_US
Ign https://private-ppa.launchpad.net precise/main Translation-en
Fetched 2,345 kB in 1min 9s (33.8 kB/s)
W: GPG error: http://packages.medibuntu.org precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://www.fbriere.net ./ InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 479C9B0FD0E6E19C
W: Failed to fetch http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/ferramroberto/java/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://www.fbriere.net/debian/dists/unstable/./Sources  404  Not Found [IP: 208.94.117.25 80]

W: Failed to fetch http://www.fbriere.net/debian/dists/unstable/./Packages  Error reading from server. Remote end closed connection [IP: 208.94.117.25 80]

W: Failed to fetch http://www.fbriere.net/debian/dists/unstable/./en  Error reading from server. Remote end closed connection [IP: 208.94.117.25 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
alec@AlecsUbuntuBook:~$ sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ubuntu/ precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
alec@AlecsUbuntuBook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
alec@AlecsUbuntuBook:~$ 

```

---

### Post by plucky on 2012-08-17
> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
  404  Not Found

and > Err [http://www.fbriere.net](http://www.fbriere.net) ./ Sources                                          
  404  Not Found [IP: 208.94.117.25 80]
Err [http://www.fbriere.net](http://www.fbriere.net) ./ Packages                                         
  Error reading from server. Remote end closed connection [IP: 208.94.117.25 80]
Ign [http://www.fbriere.net](http://www.fbriere.net) ./ Translation-en_US                  
Err [http://www.fbriere.net](http://www.fbriere.net) ./ Translation-en                                   
  Error reading from server. Remote end closed connection [IP: 208.94.117.25 80]

You need to get rid of those errors by removing the appropiate repositories in Software Sources before running the three commands above.

Good Luck

---

### Post by walker195 on 2012-08-17
i still get errors during package install and removals

---

### Post by walker195 on 2012-08-17
the newest errors
  


```
alec@AlecsUbuntuBook:~$ sudo apt-get install -f
[sudo] password for alec: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                            No apport report written because the error message indicates its a followup error from a previous failure.
                                                        Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
alec@AlecsUbuntuBook:~$ sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                      Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
alec@AlecsUbuntuBook:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                      Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
alec@AlecsUbuntuBook:~$ 

```

---

### Post by oldos2er on 2012-08-18
Try ```
sudo dpkg --configure -a
```

---

### Post by walker195 on 2012-08-18
```
alec@AlecsUbuntuBook:~$ sudo dpkg --configure -a
[sudo] password for alec: 
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Writing config for /boot/vmlinuz-3.2.0-24-generic...
P: Writing config for /boot/vmlinuz-3.2.0-23-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-29-generic; however:
  Package linux-image-3.2.0-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.29.31); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic
alec@AlecsUbuntuBook:~$ 
```

---

### Post by bodhi.zazen on 2012-08-19
See my blog post here:

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by walker195 on 2012-08-19
> **bodhi.zazen said:**
> See my blog post here:

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

thats not what i need to fix can you help with my error?

---

### Post by ribongen777 on 2012-08-19
In case, if you want to install whenever you like a program, to make sure before sudo apt-get update, then install a program, or if to check have PPA, then it would be great, it will be not have a problem.

---

### Post by walker195 on 2012-08-19
thanks i do that but i still get errors they install ok but it says they dont

---

### Post by bodhi.zazen on 2012-08-19
> **walker195 said:**
> thats not what i need to fix can you help with my error?

Did read my blog?

The packages that are giving you errors are :

> Errors were encountered while processing:
 linux-image-3.2.0-29-generic
 linux-image-generic
 linux-generic

So ...

```
# Become root
sudo -i 

#Follow the instructions for your broken packages

cd /var/lib/dpkg/info
sudo rm linux-image-3.2.0-29-generic linux-image-generic linux-generic
```

continue with the tutorial

```
sudo dpkg --remove --force-remove-reinstreq linux-image-3.2.0-29-generic
```

Run that command for each of the 3 packages.

You will then find apt-get is working. You will almost certainly want to then re-install linux-image-generic

```
sudo apt-get install linux-image-generic
```

---

### Post by walker195 on 2012-08-19
ill try that and post my results

---

### Post by walker195 on 2012-08-19
WTF my computer is even worse now i got this error after i tried to install tremulus

```
 installArchives() failed: (Reading database ... 
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
(Reading database ... 313358 files and directories currently installed.)
Removing linux-image-3.2.0-23-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-23-generic /boot/vmlinuz-3.2.0-23-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-23-generic.postrm line 328.
dpkg: error processing linux-image-3.2.0-23-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.2.0-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postrm line 328.
dpkg: error processing linux-image-3.2.0-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.2.0-29-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-29-generic
run-parts: executing /etc/kernel/postrm.d/zz-extlinux 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-25-generic...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic
/usr/sbin/grub-mkconfig: 35: /etc/default/grub: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postrm line 328.
dpkg: error processing linux-image-3.2.0-29-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.2.0-23-generic
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-29-generic
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bodhi.zazen on 2012-08-20
re-install linux-image-generic

```
sudo apt-get install linux-image-generic
```

---

### Post by walker195 on 2012-08-20
thank you for your time ive got it fixed thanks to every one on my  thread:D

---

### Post by bodhi.zazen on 2012-08-21
\o/

---

