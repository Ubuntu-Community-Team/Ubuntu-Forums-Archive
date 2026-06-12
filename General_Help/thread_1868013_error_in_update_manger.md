---
title: "error in update manger"
date: 2011-10-23
forum: General Help
---

### Post by hani270 on 2011-10-23
hello

thats error in update manager

[IMG]http://www.linuxac.org/forum/attachment.php?attachmentid=15289&d=1319399705[/IMG]

and i have problem to found good **ATI card Driver** for ubuntu 10.4 LTS 64bit :(

:(

---

### Post by hani270 on 2011-10-25
up .......................

---

### Post by Rubi1200 on 2011-10-25
Please post the output of the following commands:

```
sudo apt-get update

cat /etc/apt/sources.list
```

---

### Post by hani270 on 2011-10-25
> **Rubi1200 said:**
> Please post the output of the following commands:

```
sudo apt-get update

cat /etc/apt/sources.list
```

_*sudo apt-get update :*_
```

Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:2 http://security.ubuntu.com lucid-security Release [44.7kB]               
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/andrewfenn/ogredev/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://ly.archive.ubuntu.com lucid Release.gpg                             
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US  
Get:3 http://ly.archive.ubuntu.com lucid-updates Release.gpg [198B]          
Ign http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/stuntrally-team/stable/ubuntu/ lucid/main Translation-en_US
Get:4 http://ppa.launchpad.net lucid Release.gpg [316B]                        
Ign http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US                                                                                          
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US                                                                                    
Hit http://ppa.launchpad.net lucid Release                                                                                                                             
Get:5 http://ppa.launchpad.net lucid Release [14.0kB]                                                                                                                  
Hit http://ppa.launchpad.net lucid Release                                                                                                                             
Ign http://ppa.launchpad.net lucid Release                                                                                                                             
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US                                                                                      
Ign http://ly.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US                                                                                    
Hit http://ly.archive.ubuntu.com lucid Release                                                                                                                         
Get:6 http://security.ubuntu.com lucid-security/main Packages [217kB]                                                                                                  
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                       
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                       
Hit http://ppa.launchpad.net lucid/main Sources                                                                                                                        
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                       
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                       
Hit http://ppa.launchpad.net lucid/main Packages                                                                                                                       
Get:7 http://ly.archive.ubuntu.com lucid-updates Release [44.7kB]                                                                                                      
Hit http://ly.archive.ubuntu.com lucid/main Packages                                                                                                                   
Hit http://ly.archive.ubuntu.com lucid/restricted Packages                                                                                                             
Hit http://ly.archive.ubuntu.com lucid/main Sources                                                                                                                    
Hit http://ly.archive.ubuntu.com lucid/restricted Sources                                                                                                              
Hit http://ly.archive.ubuntu.com lucid/universe Packages                                                                                                               
Hit http://ly.archive.ubuntu.com lucid/universe Sources                                                                                                                
Hit http://ly.archive.ubuntu.com lucid/multiverse Packages                                                                                                             
Hit http://ly.archive.ubuntu.com lucid/multiverse Sources                                                                                                              
Get:8 http://ly.archive.ubuntu.com lucid-updates/main Packages [524kB]                                                                                                 
Get:9 http://security.ubuntu.com lucid-security/restricted Packages [14B]                                                                                              
Get:10 http://security.ubuntu.com lucid-security/main Sources [65.9kB]                                                                                                 
Get:11 http://security.ubuntu.com lucid-security/restricted Sources [14B]                                                                                              
Get:12 http://security.ubuntu.com lucid-security/universe Packages [90.5kB]                                                                                            
Get:13 http://security.ubuntu.com lucid-security/universe Sources [26.2kB]                                                                                             
Get:14 http://security.ubuntu.com lucid-security/multiverse Packages [4,417B]                                                                                          
Get:15 http://security.ubuntu.com lucid-security/multiverse Sources [1,742B]                                                                                           
Get:16 http://ly.archive.ubuntu.com lucid-updates/restricted Packages [4,011B]                                                                                         
Get:17 http://ly.archive.ubuntu.com lucid-updates/main Sources [203kB]                                                                                                 
Get:18 http://ly.archive.ubuntu.com lucid-updates/restricted Sources [1,850B]                                                                                          
Get:19 http://ly.archive.ubuntu.com lucid-updates/universe Packages [233kB]                                                                                            
Get:20 http://ly.archive.ubuntu.com lucid-updates/universe Sources [81.3kB]                                                                                            
Get:21 http://ly.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB]                                                                                         
Get:22 http://ly.archive.ubuntu.com lucid-updates/multiverse Sources [5,070B]                                                                                          
Fetched 1,558kB in 9min 42s (2,677B/s)
Reading package lists... Done
**W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9**

```


_*cat /etc/apt/sources.list :*_
```

# deb cdrom:[Ubuntu 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110720.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ly.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ly.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ly.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid universe
deb http://ly.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ly.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://ly.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ly.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://ly.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse


```

---

### Post by drs305 on 2011-10-25
You can correct this message:
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9

By running this command to import the correct key:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
sudo apt-get update
```

---

### Post by hani270 on 2011-10-27
[B]thank you so much :)


now when i have installed any package , i see this errors :(

[IMG]http://imup.se/i/oLgaVXwaQP.png[/IMG]

[IMG]http://imup.se/i/T8kAD0tYhk.png[/IMG]
[/B]

---

### Post by drs305 on 2011-10-27
The first message may be a result of the dependency problems of the second.

The package installed but there was a problem with the post-installation script. Since we don't know what the problem with the script is, I would first try to reinstall. 
```

sudo apt-get clean # Removes stored packages from /var/cache/apt/archives
sudo apt-get install --reinstall fglrx
sudo dpkg --configure -a  # Attempt to complete configurations

```

If that doesn't solve the problem, try purging and reinstalling the entire package. 
```
sudo apt-get purge fglrx
sudo apt-get install fglrx
```

---

### Post by hani270 on 2011-10-30
same problem :(

this is the results from each command :
i see the word "error" "error" "error"  
:((



```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up fglrx (2:8.801-0ubuntu1~xup~lucid) ...
Removing old fglrx-8.801 DKMS files...

-------- Uninstall Beginning --------
Module:  fglrx
Version: 8.801
Kernel:  2.6.32-34-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 8.801
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.801 DKMS files...
Building for 2.6.32-34-generic and 3.1.0-0301rc9-generic
Building for architecture x86_64
Building initial module for 2.6.32-34-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-34-generic/updates/dkms/

depmod....

DKMS: install Completed.
Building initial module for 3.1.0-0301rc9-generic

Error! Bad return status for module build on kernel: 3.1.0-0301rc9-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.801/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

Setting up fglrx (2:8.801-0ubuntu1~xup~lucid) ...
Removing old fglrx-8.801 DKMS files...

-------- Uninstall Beginning --------
Module:  fglrx
Version: 8.801
Kernel:  2.6.32-34-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

fglrx.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.32-34-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.

------------------------------
Deleting module version: 8.801
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.801 DKMS files...
Building for 2.6.32-34-generic and 3.1.0-0301rc9-generic
Building for architecture x86_64
Building initial module for 2.6.32-34-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-34-generic/updates/dkms/

depmod....

DKMS: install Completed.
Building initial module for 3.1.0-0301rc9-generic

Error! Bad return status for module build on kernel: 3.1.0-0301rc9-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.801/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  fglrx* fglrx-amdcccle*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 121MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 201025 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for fglrx ...
update-initramfs: deferring update (trigger activated)
dpkg: warning: while removing fglrx, directory '/usr/lib32/fglrx' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc/ati' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx/etc' not empty so not removed.
dpkg: warning: while removing fglrx, directory '/usr/lib/fglrx' not empty so not removed.
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.1.0-0301rc9-generic
Processing triggers for python-support ...

```

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 37.7MB of archives.
After this operation, 121MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  fglrx fglrx-amdcccle
Install these packages without verification [y/N]? y
Get:1 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main fglrx 2:8.801-0ubuntu1~xup~lucid [32.4MB]
Get:2 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ lucid/main fglrx-amdcccle 2:8.801-0ubuntu1~xup~lucid [5,295kB]
Fetched 37.7MB in 3h 1min 28s (3,461B/s)                                       
Selecting previously deselected package fglrx.
(Reading database ... 200818 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.801-0ubuntu1~xup~lucid_amd64.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.801-0ubuntu1~xup~lucid_amd64.deb) ...
Processing triggers for ureadahead ...
Processing triggers for man-db ...
Setting up fglrx (2:8.801-0ubuntu1~xup~lucid) ...
Loading new fglrx-8.801 DKMS files...
First Installation: checking all kernels...
Building for 2.6.32-34-generic and 3.1.0-0301rc9-generic
Building for architecture x86_64
Building initial module for 2.6.32-34-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-34-generic/updates/dkms/

depmod....

DKMS: install Completed.
Building initial module for 3.1.0-0301rc9-generic

Error! Bad return status for module build on kernel: 3.1.0-0301rc9-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.801/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

am now (purged) the package and tried to resume the center ati driver from 
main menu -> System -> Administration -> Hardware Drivers

i have this error
```

**SystemError: installArchives() failed**

```

i cant enable desktop effects :((


and thanks for support :)

---

### Post by drs305 on 2011-10-31
Some of output in the last section refers to kernel 3.1 as well as 2.6.32-34-generic but when downloading the ubuntu-x-swat ppa it references 'lucid'. 

I'm not an expert at building kernels, but I would strongly suspect your issue is the dependency issues relating to the 3.1 kernel. It looks like the 2.6.32 operations are completing but the commands fail when trying to deal with 3.1.  It would make sense that if you have the lucid libraries/repositories it could have dependency problems with a much more advanced kernel.

---

### Post by hani270 on 2011-10-31
[COLOR=DarkRed]thanks again :)


i'm using "2.6.32-34-generic" now
i want to remove the new kernal

i installed it for test only

i want to restore the desktop effects.....

---
sorry for my bad english :|
[/COLOR]

---

### Post by drs305 on 2011-11-01
An easy way to removed kernels is with the Ubuntu Tweak app. It does a lot of things - cleaning up old configuration files and kernels is very easy with Ubuntu Tweak.

Here is a link. Make sure you download the correct version. It's available to me in Synaptic / Software Center but I may have added repositories to get it.
[http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

Once installed and opened, go to Package Cleaner, unlock with the lower right button, Clean Kernels.

---

### Post by hani270 on 2011-11-03
[COLOR=DarkRed][B]very very very thanks :)

ubuntuTweak tools is so cooooooooool
+
i have restored the default ATI driver wooow !

thank u so much :)
[/B][/COLOR]

---

