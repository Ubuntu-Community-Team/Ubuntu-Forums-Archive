---
title: "Fix broken packages first"
date: 2010-12-18
forum: General Help
---

### Post by DeMus on 2010-12-18
HI, I have some updates waiting to be installed, but can't install them because of: "Fix broken packages first".
I searched the forum for answers but until now nothing seems to work.
I used:
```
Fix broken packages in Synaptic
sudo apt-get check
sudo apt-get autoremove
sudo apt-get install -f
sudo dpkg --configure -a
```
I uninstalled the latest update I received yesterday (Google-Chrome) but still nothing works.
Who can help me?

---

### Post by karthick87 on 2010-12-18
Can you post the complete output of,

```
sudo apt-get install -f
```
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```

---

### Post by DeMus on 2010-12-18
Here it is:


```
sudo apt-get update
Ign file: binary/ Release.gpg
Ign file:/usr/share/local-repository/ binary/ Translation-en_US                
Ign file: binary/ Release                                                      
Ign file: binary/ Packages                                                     
Ign file: binary/ Packages                                                     
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:1 http://packages.linuxmint.com isadora Release.gpg [198B]                 
Hit http://archive.canonical.com lucid Release                                 
Ign http://packages.linuxmint.com/ isadora/main Translation-en_US              
Ign http://packages.linuxmint.com/ isadora/upstream Translation-en_US          
Ign http://packages.linuxmint.com/ isadora/import Translation-en_US            
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid/partner Packages                        
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://packages.linuxmint.com isadora Release [7,235B]                   
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://www.ftd4linux.nl lucid Release.gpg                                  
Ign http://www.ftd4linux.nl/releases/ubuntu/ lucid/main Translation-en_US      
Hit http://www.ftd4linux.nl lucid Release                                      
Hit http://security.ubuntu.com lucid-security/main Packages                    
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Ign http://www.ftd4linux.nl lucid/main Packages                                
Ign http://packages.linuxmint.com isadora/main Packages                        
Ign http://www.ftd4linux.nl lucid/main Packages                                
Ign http://packages.linuxmint.com isadora/upstream Packages                    
Hit http://www.ftd4linux.nl lucid/main Packages                                
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/lottanzb/ppa/ubuntu/ lucid/main Translation-en_US 
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://packages.linuxmint.com isadora/import Packages                      
Ign http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/n-muench/vlc/ubuntu/ lucid/main Translation-en_US 
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/onestone/vlc/ubuntu/ lucid/main Translation-en_US 
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://packages.linuxmint.com isadora/main Packages                        
Ign http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/rvm/ppa/ubuntu/ lucid/main Translation-en_US      
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Ign http://packages.linuxmint.com isadora/upstream Packages                    
Hit http://archive.ubuntu.com lucid Release.gpg                                
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/ripps818/coreavc/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/banshee-team/banshee-daily/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Get:3 http://dl.google.com stable Release.gpg [197B]                           
Ign http://packages.linuxmint.com isadora/import Packages                      
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Hit http://archive.ubuntu.com lucid-updates Release.gpg                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US     
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US 
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid Release                                    
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Ign http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://dl.google.com stable Release.gpg [189B]                           
Ign http://dl.google.com/linux/deb/ stable/main Translation-en_US              
Hit http://packages.linuxmint.com isadora/main Packages                        
Hit http://archive.ubuntu.com lucid-updates Release                            
Get:5 http://dl.google.com stable Release [1,347B]                             
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Get:6 http://dl.google.com stable Release [2,544B]                             
Hit http://archive.ubuntu.com lucid/main Packages                              
Hit http://archive.ubuntu.com lucid/restricted Packages                        
Hit http://archive.ubuntu.com lucid/universe Packages                          
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.ubuntu.com lucid/multiverse Packages                        
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.ubuntu.com lucid-updates/main Packages                      
Hit http://archive.ubuntu.com lucid-updates/restricted Packages                
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://packages.linuxmint.com isadora/upstream Packages                    
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:7 http://dl.google.com stable/main Packages [1,091B]                       
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://archive.ubuntu.com lucid-updates/universe Packages                  
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Hit http://packages.medibuntu.org lucid Release.gpg                            
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Sources                                
Get:8 http://dl.google.com stable/main Packages [1,104B]                       
Hit http://packages.linuxmint.com isadora/import Packages                      
Ign http://packages.medibuntu.org/ lucid/free Translation-en_US                
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US            
Hit http://packages.medibuntu.org lucid Release       
Hit http://packages.medibuntu.org lucid/free Packages
Hit http://packages.medibuntu.org lucid/non-free Packages
Hit http://archive.getdeb.net lucid-getdeb Release.gpg   
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/apps Translation-en_US
Ign http://archive.getdeb.net/ubuntu/ lucid-getdeb/games Translation-en_US
Hit http://archive.getdeb.net lucid-getdeb Release
Hit http://archive.getdeb.net lucid-getdeb/apps Packages
Hit http://archive.getdeb.net lucid-getdeb/games Packages
Fetched 13.9kB in 4s (3,108B/s)
Reading package lists... Done
```

---

### Post by katykat on 2010-12-18
Ubuntu's installer programs, all related, sometimes get putzed up and none of their utilities will remove or unblock a broken package. 

To completely remove a package from the system edit:
/var/lib/dpkg/status

And completely remove the first blocked package. 
(That may allow the others to be installed or removed. If not, repeat)

But...
I *believe* that then the  only way to reinstall the removed package would be manually, or by compiling from source.

---

### Post by DeMus on 2010-12-18
What am I looking for in the file status? I have no idea. Could you help me with that please? I send the file with this post.

---

### Post by karthick87 on 2010-12-18
Try the following,

```
sudo rm /var/lib/dpkg/lock 
```

```
sudo apt-get update
```

---

### Post by DeMus on 2010-12-18
> **karthick87 said:**
> Try the following,

```
sudo rm /var/lib/dpkg/lock 
```

```
sudo apt-get update
```

Didn't work, I still have the same problem. But thank you for helping me.

---

### Post by DeMus on 2010-12-18
I am one step further at the moment. I had 9 updates waiting, 5 of them belong to the XBMC media player package. I un-ticked those 5 and could update the other packages.
Trying to do the same with the XBMC packages gave me the same error message again, so something must be wrong with the XBMC updates. But what?

---

### Post by Linyx on 2010-12-18
[SIZE="2"]If you can identify the broken package from the above given code...... this code will very forcefully remove it.[/SIZE]

```
sudo dpkg --remove -force --force-remove-reinstreq package name
```

---

### Post by sikander3786 on 2010-12-18
Please post the output of this one as well.

```
sudo apt-get upgrade
```

---

### Post by Elfy on 2010-12-18
It might well help to post the results of these as you only posted the update output earlier :)

```

sudo apt-get install -f
sudo dpkg --configure -a
```

---

### Post by DeMus on 2010-12-18
@Sikander and @Forestpiskie. I did what you asked me to do and this is the result.

```
sudo apt-get upgrade
[sudo] password for jan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  xbmc xbmc-bin xbmc-data xbmc-skin-confluence
The following packages will be upgraded:
  linux-headers-2.6.32-26 linux-headers-2.6.32-26-generic linux-image-2.6.32-26-generic linux-libc-dev xserver-xorg-core xserver-xorg-video-ati xserver-xorg-video-intel
  xserver-xorg-video-radeon
8 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 47.2MB of archives.
After this operation, 479kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  linux-image-2.6.32-26-generic linux-headers-2.6.32-26 linux-headers-2.6.32-26-generic linux-libc-dev xserver-xorg-core xserver-xorg-video-radeon
  xserver-xorg-video-ati xserver-xorg-video-intel
Authentication warning overridden.
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main xserver-xorg-video-radeon 1:6.13.1-1ubuntu1~xup3~lucid [668kB]
Get:2 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-image-2.6.32-26-generic 2.6.32-26.48 [31.7MB]
Get:3 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main xserver-xorg-video-ati 1:6.13.1-1ubuntu1~xup3~lucid [245kB]
Get:4 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main xserver-xorg-video-intel 2:2.11.0-1ubuntu1~xup [549kB]
Get:5 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-26 2.6.32-26.48 [9,900kB]                                                                
Get:6 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-headers-2.6.32-26-generic 2.6.32-26.48 [786kB]                                                          
Get:7 http://archive.ubuntu.com/ubuntu/ lucid-updates/main linux-libc-dev 2.6.32-26.48 [820kB]                                                                           
Get:8 http://archive.ubuntu.com/ubuntu/ lucid-updates/main xserver-xorg-core 2:1.7.6-2ubuntu7.4 [2,553kB]                                                                
Fetched 47.2MB in 17s (2,733kB/s)                                                                                                                                        
(Reading database ... 223847 files and directories currently installed.)
Preparing to replace linux-image-2.6.32-26-generic 2.6.32-26.47 (using .../linux-image-2.6.32-26-generic_2.6.32-26.48_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.32-26-generic ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.37-6-generic
Found initrd image: /boot/initrd.img-2.6.37-6-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Preparing to replace linux-headers-2.6.32-26 2.6.32-26.47 (using .../linux-headers-2.6.32-26_2.6.32-26.48_all.deb) ...
Unpacking replacement linux-headers-2.6.32-26 ...
Preparing to replace linux-headers-2.6.32-26-generic 2.6.32-26.47 (using .../linux-headers-2.6.32-26-generic_2.6.32-26.48_amd64.deb) ...
Unpacking replacement linux-headers-2.6.32-26-generic ...
Preparing to replace linux-libc-dev 2.6.32-26.47 (using .../linux-libc-dev_2.6.32-26.48_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace xserver-xorg-core 2:1.7.6-2ubuntu7.3 (using .../xserver-xorg-core_2%3a1.7.6-2ubuntu7.4_amd64.deb) ...
Unpacking replacement xserver-xorg-core ...
Preparing to replace xserver-xorg-video-radeon 1:6.13.0-1ubuntu5 (using .../xserver-xorg-video-radeon_1%3a6.13.1-1ubuntu1~xup3~lucid_amd64.deb) ...
Unpacking replacement xserver-xorg-video-radeon ...
Preparing to replace xserver-xorg-video-ati 1:6.13.0-1ubuntu5 (using .../xserver-xorg-video-ati_1%3a6.13.1-1ubuntu1~xup3~lucid_amd64.deb) ...
Unpacking replacement xserver-xorg-video-ati ...
Preparing to replace xserver-xorg-video-intel 2:2.9.1-3ubuntu5 (using .../xserver-xorg-video-intel_2%3a2.11.0-1ubuntu1~xup_amd64.deb) ...
Unpacking replacement xserver-xorg-video-intel ...
Processing triggers for man-db ...
Setting up linux-image-2.6.32-26-generic (2.6.32-26.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-26-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.32-26.47 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.32-26.47 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found Debian background: linuxmint.png
Found linux image: /boot/vmlinuz-2.6.37-6-generic
Found initrd image: /boot/initrd.img-2.6.37-6-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-26-generic /boot/vmlinuz-2.6.32-26-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-26-generic /boot/vmlinuz-2.6.32-26-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.32-26-generic /boot/vmlinuz-2.6.32-26-generic

Setting up linux-headers-2.6.32-26 (2.6.32-26.48) ...
Setting up linux-headers-2.6.32-26-generic (2.6.32-26.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-26-generic /boot/vmlinuz-2.6.32-26-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-26-generic /boot/vmlinuz-2.6.32-26-generic

Setting up linux-libc-dev (2.6.32-26.48) ...
Setting up xserver-xorg-core (2:1.7.6-2ubuntu7.4) ...

Setting up xserver-xorg-video-radeon (1:6.13.1-1ubuntu1~xup3~lucid) ...

Setting up xserver-xorg-video-ati (1:6.13.1-1ubuntu1~xup3~lucid) ...
Setting up xserver-xorg-video-intel (2:2.11.0-1ubuntu1~xup) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jan@LinuxMint ~ $ 
jan@LinuxMint ~ $ 
jan@LinuxMint ~ $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
jan@LinuxMint ~ $ 
jan@LinuxMint ~ $ 
jan@LinuxMint ~ $ sudo dpkg --configure -a
jan@LinuxMint ~ $ 

```


But still I have the same error message coming up when trying to update XBMC.

---

### Post by sikander3786 on 2010-12-18
There are no errors in that output. No broken packages at all.

That might be a dependency issue with XBMC. XBMC updates are not coming from the ppa repositories? apt-get upgrade should have included those and we should've see the error message there :confused:

Anyhow, can you post a screenshot of the updates that are related to XBMC?

---

### Post by DeMus on 2010-12-18
> **sikander3786 said:**
> There are no errors in that output. No broken packages at all.

That might be a dependency issue with XBMC. XBMC updates are not coming from the ppa repositories? apt-get upgrade should have included those and we should've see the error message there :confused:

Anyhow, can you post a screenshot of the updates that are related to XBMC?

Sorry, can't do. I tried but when I looked in the update manager I saw several updates, 5 of them being XBMC updates. I unticked, what I thought were all of them, but apparently I missed 2: XBMC-BIN and XBMC-data. So they were installed and now I don't have any more broken packages. I also don't have any more updates waiting. Somehow my mistake cured it all. Don't know if I have updated XBMC now or not, but when it's still working, and it does, then it's good enough for me.
Thank you for you help, you time and effort. It was great.:P

---

