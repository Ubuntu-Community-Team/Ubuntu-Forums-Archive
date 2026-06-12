---
title: "basic pakage broken"
date: 2010-11-20
forum: General Help
---

### Post by richlyn9 on 2010-11-20
I have messed up my Ubuntu **32 bit 9.10** by uninstalling the python 2.6 and its dependencies accidentally or rather foolishly.I marked it for complete removal and aplied it in synaptic

ow i am unable to boot in to the dist 
have tried using my remastersys back up live cd and also the live cd
but am unable to see what to do
i also have a **10.4 64 bit** but doing a chroot and installing seems to be a problem with the build difference.
so i am kinda stuck and i don't want to reinstall from the back up but rather want to fix it
Kindly guide me

---

### Post by richlyn9 on 2010-11-21
me thinks that chroot is the best way to fix this but am at loss as to what needs be exactly done.

---

### Post by richlyn9 on 2010-11-21
i did chroot in to the karmic system from a karmic live cd
and ran
*dpkg-reconfigure pytho*n
which returned[I]
python is broken or not fully installed[/I]

how do i fix it

---

### Post by Quackers on 2010-11-21
From your chroot have you tried
```
apt-get install python
```
and if so what is shown?

---

### Post by sikander3786 on 2010-11-21
To fix dependency problem, you need to do these commands.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Good Luck!

---

### Post by richlyn9 on 2010-11-21
i did try those commands and it gave me some error 
however right now i have started synaptic within chroot
it gave me option to install some pakages and i pressed "g" to do the same 

but am not sure what those packages (since its taking too long) are however its downloading python as i type this.

---

### Post by sikander3786 on 2010-11-21
> i did try those commands and it gave me some error 

Please post the complete output of those commands.

Also try to upgrade your install by

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by richlyn9 on 2010-11-21
[B]heres what i did hope it fixes the issue 

now to reboot[/B]


To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

custom@custom:~$ mkdir /mount/point
mkdir: cannot create directory `/mount/point': No such file or directory
custom@custom:~$ sudo mkdir /mount/point
mkdir: cannot create directory `/mount/point': No such file or directory
custom@custom:~$ clear

custom@custom:~$ sudo mount /dev/sda9 /mnt
custom@custom:~$ sudo mount –bind /dev /mnt/dev
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo mount --bind /proc /mnt/proc
custom@custom:~$ sudo mount --bind /dev/pts /mnt/disk/dev/pts
mount: mount point /mnt/disk/dev/pts does not exist
custom@custom:~$ sudo mount --bind /dev/pts /mnt/sda09/dev/pts
mount: mount point /mnt/sda09/dev/pts does not exist
custom@custom:~$ sudo mount --bind /dev/pts /mnt/dev/pts
custom@custom:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
custom@custom:~$ sudo chroot /mnt
root@custom:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@custom:/# dpkg
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@custom:/# dpkg --configure -a
root@custom:/# apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg [198B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN          
Get:2 [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg [198B]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN              
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                          
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Translation-en_IN                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release [51.3kB]              
Get:4 [http://archive.canonical.com](http://archive.canonical.com) karmic Release [9,359B]                     
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN                 
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Get:5 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages [5,164B]            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN           
Hit [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Get:6 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources [2,634B]             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN           
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages [193kB]         
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg [198B]           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN         
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release                                
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release [51.3kB]             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources                           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources                     
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages [310kB]       
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages [14B]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources [116kB]         
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages [1,631B]
Get:14 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources [156kB]        
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources [14B]     
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages [90.1kB]   
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources [31.6kB]    
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages [4,713B] 
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources [1,425B]  
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources [878B]   
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages [182kB]   
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources [61.9kB]   
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages [11.4kB]
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources [5,628B] 
Fetched 1,288kB in 6min 59s (3,068B/s)
Reading package lists... Done
root@custom:/# dpkg-reconfigure python
/usr/sbin/dpkg-reconfigure: python is broken or not fully installed
root@custom:/# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  casper libfreebob0 menu libwildmidi0 libntfs10 x11proto-xext-dev
  libdmraid1.0.0.rc15 libdc1394-22 libatk1.0-dev libgtksourceview2.0-dev
  libglib2.0-dev libsoundtouch1c2 libdiscover2 x11proto-xinerama-dev libsvga1
  libpango1.0-dev x11proto-render-dev libdca0 libopenspc0 libxi-dev
  java-common libxrender-dev libfftw3-3 libcairo2-dev libass3 libsysfs-dev
  libdirectfb-extra python2.5 libdebian-installer4 squashfs-tools xresprobe
  discover libpng12-dev libdvbpsi5 user-setup libggi-target-x ubiquity-casper
  kpartx libfontconfig1-dev cryptsetup libdirectfb-dev x11proto-composite-dev
  libecryptfs0 reiserfsprogs libx264-67 rdate libxcursor-dev libcelt0 libggi2
  bogl-bterm libqtcore4 x11proto-randr-dev x11proto-damage-dev libgii1
  libxcb-render-util0-dev libgtk2.0-dev libxext-dev libjpeg62-dev freepats
  libxdamage-dev localechooser-data zlib1g-dev libxml2-dev libffado1
  libfreetype6-dev libgii1-target-x x11proto-fixes-dev libiso9660-5 libkate1
  libcdaudio1 libxcomposite-dev libmimic0 ntfsprogs ecryptfs-utils
  libxml++2.6-2 ubiquity-ubuntu-artwork libxrandr-dev libexpat1-dev libqtgui4
  liblua5.1-0 libdebconfclient0 libdb4.6 libdirac0c2a imagemagick
  libmodplug0c2 discover-data libpixman-1-dev libxft-dev libtar dmraid
  libxcb-render0-dev libxfixes-dev watershed libxinerama-dev libvcdinfo0
  libebml0 discover1 libmpcdec3 keyutils libmatroska0 libofa0 libmms0
  libiptcdata0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# sudo apt-get -f install
sudo: unable to resolve host custom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  casper libfreebob0 menu libwildmidi0 libntfs10 x11proto-xext-dev
  libdmraid1.0.0.rc15 libdc1394-22 libatk1.0-dev libgtksourceview2.0-dev
  libglib2.0-dev libsoundtouch1c2 libdiscover2 x11proto-xinerama-dev libsvga1
  libpango1.0-dev x11proto-render-dev libdca0 libopenspc0 libxi-dev
  java-common libxrender-dev libfftw3-3 libcairo2-dev libass3 libsysfs-dev
  libdirectfb-extra python2.5 libdebian-installer4 squashfs-tools xresprobe
  discover libpng12-dev libdvbpsi5 user-setup libggi-target-x ubiquity-casper
  kpartx libfontconfig1-dev cryptsetup libdirectfb-dev x11proto-composite-dev
  libecryptfs0 reiserfsprogs libx264-67 rdate libxcursor-dev libcelt0 libggi2
  bogl-bterm libqtcore4 x11proto-randr-dev x11proto-damage-dev libgii1
  libxcb-render-util0-dev libgtk2.0-dev libxext-dev libjpeg62-dev freepats
  libxdamage-dev localechooser-data zlib1g-dev libxml2-dev libffado1
  libfreetype6-dev libgii1-target-x x11proto-fixes-dev libiso9660-5 libkate1
  libcdaudio1 libxcomposite-dev libmimic0 ntfsprogs ecryptfs-utils
  libxml++2.6-2 ubiquity-ubuntu-artwork libxrandr-dev libexpat1-dev libqtgui4
  liblua5.1-0 libdebconfclient0 libdb4.6 libdirac0c2a imagemagick
  libmodplug0c2 discover-data libpixman-1-dev libxft-dev libtar dmraid
  libxcb-render0-dev libxfixes-dev watershed libxinerama-dev libvcdinfo0
  libebml0 discover1 libmpcdec3 keyutils libmatroska0 libofa0 libmms0
  libiptcdata0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# sudo apt-get reinstall python2.6
sudo: unable to resolve host custom
E: Invalid operation reinstall
root@custom:/# sudo apt-get reinstall python
sudo: unable to resolve host custom
E: Invalid operation reinstall
root@custom:/# sudo apt-get -f install
sudo: unable to resolve host custom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  casper libfreebob0 menu libwildmidi0 libntfs10 x11proto-xext-dev
  libdmraid1.0.0.rc15 libdc1394-22 libatk1.0-dev libgtksourceview2.0-dev
  libglib2.0-dev libsoundtouch1c2 libdiscover2 x11proto-xinerama-dev libsvga1
  libpango1.0-dev x11proto-render-dev libdca0 libopenspc0 libxi-dev
  java-common libxrender-dev libfftw3-3 libcairo2-dev libass3 libsysfs-dev
  libdirectfb-extra python2.5 libdebian-installer4 squashfs-tools xresprobe
  discover libpng12-dev libdvbpsi5 user-setup libggi-target-x ubiquity-casper
  kpartx libfontconfig1-dev cryptsetup libdirectfb-dev x11proto-composite-dev
  libecryptfs0 reiserfsprogs libx264-67 rdate libxcursor-dev libcelt0 libggi2
  bogl-bterm libqtcore4 x11proto-randr-dev x11proto-damage-dev libgii1
  libxcb-render-util0-dev libgtk2.0-dev libxext-dev libjpeg62-dev freepats
  libxdamage-dev localechooser-data zlib1g-dev libxml2-dev libffado1
  libfreetype6-dev libgii1-target-x x11proto-fixes-dev libiso9660-5 libkate1
  libcdaudio1 libxcomposite-dev libmimic0 ntfsprogs ecryptfs-utils
  libxml++2.6-2 ubiquity-ubuntu-artwork libxrandr-dev libexpat1-dev libqtgui4
  liblua5.1-0 libdebconfclient0 libdb4.6 libdirac0c2a imagemagick
  libmodplug0c2 discover-data libpixman-1-dev libxft-dev libtar dmraid
  libxcb-render0-dev libxfixes-dev watershed libxinerama-dev libvcdinfo0
  libebml0 discover1 libmpcdec3 keyutils libmatroska0 libofa0 libmms0
  libiptcdata0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# sudo apt-get update && sudo apt-get upgrade
sudo: unable to resolve host custom
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN          
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                          
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Translation-en_IN                    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN 
Hit [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
sudo: unable to resolve host custom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adobe-flashplugin libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libssl0.9.8
  linux-headers-2.6.31-22 linux-headers-2.6.31-22-generic linux-libc-dev
  mesa-utils openssl tzdata tzdata-java xserver-xorg-video-intel
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.2MB of archives.
After this operation, 24.6kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main libssl0.9.8 0.9.8g-16ubuntu3.4 [2,923kB]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) karmic/partner adobe-flashplugin 10.1.102.65-2karmic1 [4,887kB]
9% [1 libssl0.9.8 1195802/2,923kB 40%] [2 adobe-flashplugin 1079890/4,887kB 22%^C
root@custom:/# sudo dpkg --configure -a

sudo: unable to resolve host custom
root@custom:/# 
root@custom:/# dpkg --configure -a
root@custom:/# apt-get clean
root@custom:/# sudo apt-get update
sudo: unable to resolve host custom
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN              
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                          
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Translation-en_IN                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN           
Hit [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN             
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN    
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                      
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
root@custom:/# sudo dpkg --configure -a --force-all
sudo: unable to resolve host custom
root@custom:/# dpkg --configure -a --force-all
root@custom:/# sudo aptitude
sudo: unable to resolve host custom
root@custom:/# apt-get install python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 libdca0 java-common libass3 python2.5 libdvbpsi5 libggi-target-x
  libggi2 libgii1 libgii1-target-x libiso9660-5 liblua5.1-0 libdb4.6 libmodplug0c2
  libvcdinfo0 libebml0 libmpcdec3 libmatroska0 libfaad0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  python2.6
Suggested packages:
  python-doc python-tk python-profiler python2.6-doc python2.6-profiler
The following NEW packages will be installed:
  python python2.6
0 upgraded, 2 newly installed, 0 to remove and 13 not upgraded.
Need to get 0B/2,585kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package python2.6.
(Reading database ... 225832 files and directories currently installed.)
Unpacking python2.6 (from .../python2.6_2.6.4-0ubuntu3_i386.deb) ...
Selecting previously deselected package python.
Unpacking python (from .../python_2.6.4-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Processing triggers for doc-base ...
Processing 1 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up python2.6 (2.6.4-0ubuntu3) ...

Setting up python (2.6.4-0ubuntu1) ...

Processing triggers for menu ...
root@custom:/# sudo apt-get install -f
sudo: unable to resolve host custom
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsvga1 libdca0 java-common libass3 python2.5 libdvbpsi5 libggi-target-x
  libggi2 libgii1 libgii1-target-x libiso9660-5 liblua5.1-0 libdb4.6 libmodplug0c2
  libvcdinfo0 libebml0 libmpcdec3 libmatroska0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# sudo dpkg --configure -a
sudo: unable to resolve host custom
root@custom:/# apt-get build-essential
E: Invalid operation build-essential
root@custom:/# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libdca0 java-common libass3 python2.5 libdvbpsi5 libggi-target-x
  libggi2 libgii1 libgii1-target-x libiso9660-5 liblua5.1-0 libdb4.6 libmodplug0c2
  libvcdinfo0 libebml0 libmpcdec3 libmatroska0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# apt-get install build-dep python 2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-dep
root@custom:/# apt-get install build-dep python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-dep
root@custom:/# apt-get install build-dep python2.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-dep
root@custom:/# sudo aptitute install python2.6
sudo: unable to resolve host custom
sudo: aptitute: command not found
root@custom:/# sudo aptitute install python 2.6
sudo: unable to resolve host custom
sudo: aptitute: command not found
root@custom:/# rm /sbin/initctl
root@custom:/# dpkg-divert –local –remove /sbin/initctl
dpkg-divert: --add needs a single argument

Usage: dpkg-divert [<option> ...] <command>

Commands:
  [--add] <file>           add a diversion.
  --remove <file>          remove the diversion.
  --list [<glob-pattern>]  show file diversions.
  --listpackage <file>     show what package diverts the file.
  --truename <file>        return the diverted file.

Options:
  --package <package>      name of the package whose copy of <file> will not
                             be diverted.
  --local                  all packages' versions are diverted.
  --divert <divert-to>     the name used by other packages' versions.
  --rename                 actually move the file aside (or back).
  --admindir <directory>   set the directory with the diversions file.
  --test                   don't do anything, just demonstrate.
  --quiet                  quiet operation, minimal output.
  --help                   show this help message.
  --version                show the version.

When adding, default is --local and --divert <original>.distrib.
When removing, --package or --local and --divert must match if specified.
Package preinst/postrm scripts should always specify --package and --divert.
root@custom:/# dpkg-divert --local --remove /sbin/initctl
Removing `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# exit
exit
custom@custom:~$ sudo umount /mnt/disk/dev/pts
umount: /mnt/disk/dev/pts: not found
custom@custom:~$ sudo umount /mnt/dev/pts
custom@custom:~$ sudo umount /mnt/dev
custom@custom:~$ sudo umount /mnt/proc
custom@custom:~$ sudo umount /mnt
custom@custom:~$

---

### Post by sikander3786 on 2010-11-21
> sudo: unable to resolve host custom

You are aleary in the root shell so you don't need sudo. But I can't see any broken packages either.

Try once more with

```
apt-get install -f
```

Reboot and see what is happening there now.

---

### Post by richlyn9 on 2010-11-21
rebooted and now it give me some more errors


init:job_process.c:529 unhandeled error from job_process_spawn:no such file or directory
failed to spawn ufw prestart process
failed to spawn ufw poststart process
...
unreadahead other main process (809)terminated with error4

?????

---

### Post by sikander3786 on 2010-11-21
> **richlyn9 said:**
> rebooted and now it give me some more errors


init:job_process.c:529 unhandeled error from job_process_spawn:no such file or directory
failed to spawn ufw prestart process
failed to spawn ufw poststart process
...
unreadahead other main process (809)terminated with error4

?????
Instead of putting that much efforts in restoring that, it would be better to save your data and reinstall if possible.

---

### Post by richlyn9 on 2010-11-21
> **sikander3786 said:**
> Instead of putting that much efforts in restoring that, it would be better to save your data and reinstall if possible.


the challenge in troubleshooting and finding resolutions is what drives me.
Reinstalling would ofcourse my last option.

BTY is there a way i can upgrade to the latest merkat though this is broken using a cd or iso file

---

### Post by sikander3786 on 2010-11-21
> 
BTY is there a way i can upgrade to the latest merkat though this is broken using a cd or iso file

I don't think it would be possible without booting into your actual install.

You can use alternate disc but that too from your original install. I don't know if it would be successful from chroot environment.

[https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/MaverickUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)

---

### Post by richlyn9 on 2010-11-21
am gonnay chroot again and try fix this 
not sure though whats missing...

from the last effort to fix it i think python must be now installed however it seems that some deps are still missing
hmmm wonder whats the command to install missing deps.

---

### Post by richlyn9 on 2010-11-21
[B]chrooted to my broken install band checked but everything seems to be fine
[/B]

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

custom@custom:~$ sudo mount /dev/sda9 /mnt
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo mount --bind /proc /mnt/proc
custom@custom:~$ udo mount --bind /dev/pts /mnt/dev/pts
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
udo: command not found
custom@custom:~$ sudo mount --bind /dev/pts /mnt/dev/pts
custom@custom:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
custom@custom:~$ sudo chroot /mnt
root@custom:/# dpkg-divert --local --rename --add /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# ln -s /bin/true /sbin/initctl
root@custom:/# apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_IN          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release.gpg                            
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_IN              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_IN    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_IN      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_IN    
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release.gpg                          
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Translation-en_IN                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources                
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Ign [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Translation-en_IN
Hit [http://www.geekconnection.org](http://www.geekconnection.org) karmic/ Packages                            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Translation-en_IN          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic Release         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates Release                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Packages                        
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/main Sources    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
root@custom:/# aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  aisleriot{a} alacarte alsa-utils apport{a} apport-gtk{a} aptdaemon{a} 
  apturl{a} apturl-common{a} at-spi{a} brasero capplets-data{a} checkbox{a} 
  checkbox-gtk compiz compiz-fusion-plugins-extra{a} 
  compiz-fusion-plugins-main{a} compiz-gnome{a} computer-janitor{a} 
  computer-janitor-gtk couchdb-bin{a} desktopcouch{a} empathy eog espeak 
  evince evolution evolution-couchdb evolution-data-server{a} 
  evolution-documentation-en{a} evolution-exchange evolution-indicator 
  evolution-plugins{a} evolution-webcal{a} f-spot file-roller firefox 
  firefox-branding{a} firefox-gnome-support gcalctool gconf-editor 
  gconf2{a} gdb{a} gdebi gdebi-core{a} gdm gdm-guest-session gedit gimp 
  gksu{a} glchess{a} glines{a} gnect{a} gnibbles{a} gnobots2{a} 
  gnome-about{a} gnome-applets{a} gnome-applets-data{a} gnome-blackjack{a} 
  gnome-bluetooth gnome-codec-install gnome-control-center{a} 
  gnome-doc-utils{a} gnome-games gnome-keyring{a} gnome-mahjongg{a} 
  gnome-media{a} gnome-media-common{a} gnome-menus{a} gnome-orca 
  gnome-panel{a} gnome-panel-data{a} gnome-pilot{a} gnome-pilot-conduits{a} 
  gnome-power-manager gnome-screensaver gnome-session{a} 
  gnome-session-bin{a} gnome-session-canberra gnome-settings-daemon{a} 
  gnome-sudoku{a} gnome-system-monitor{a} gnome-system-tools gnome-terminal 
  gnome-terminal-data{a} gnome-user-guide{a} gnome-utils gnometris{a} 
  gnomine{a} gnotravex{a} gnotski{a} gstreamer0.10-alsa 
  gstreamer0.10-plugins-good{a} gtali{a} gucharmap hpijs{a} hplip 
  hplip-data{a} iagno{a} ibus ibus-m17n ibus-table indicator-applet{a} 
  indicator-applet-session indicator-messages{a} indicator-session{a} 
  jockey-common{a} jockey-gtk language-selector language-selector-common{a} 
  launchpad-integration libasound2{a} libasound2-plugins{a} 
  libbonoboui2-0{a} libcanberra-gtk-module{a} libcanberra-gtk0{a} 
  libcanberra-pulse{a} libcanberra0{a} libempathy-gtk-common{a} 
  libempathy-gtk28{a} libempathy30{a} libesd-alsa0{a} libespeak1{a} 
  libgail-gnome-module{a} libgegl-0.0-0{a} libgksu2-0{a} libgnome-media0{a} 
  libgnome-pilot2{a} libgnome-vfs2.0-cil{a} libgnome2-0{a} 
  libgnome2-common{a} libgnome2-perl{a} libgnome2-vfs-perl{a} 
  libgnome2.24-cil{a} libgnomekbd-common{a} libgnomekbd4{a} 
  libgnomekbdui4{a} libgnomepanel2.24-cil{a} libgnomeui-0{a} 
  libgnomevfs2-0{a} libgnomevfs2-common{a} libgnomevfs2-extra{a} 
  libgstfarsight0.10-0{a} libgweather-common{a} libgweather1{a} 
  liblpint-bonobo0{a} libmetacity0{a} libpanel-applet2-0{a} 
  libportaudio2{a} libpurple-bin{a} libpurple0{a} libpython2.6{a} 
  libsdl1.2debian{a} libsdl1.2debian-alsa{a} libtelepathy-farsight0{a} 
  lsb-release{a} metacity{a} metacity-common{a} mousetweaks{a} nautilus{a} 
  nautilus-data{a} nautilus-sendto nautilus-share network-manager{a} 
  network-manager-gnome nvidia-common{a} onboard openoffice.org-gnome 
  pulseaudio{a} pulseaudio-esound-compat{a} pulseaudio-module-bluetooth 
  pulseaudio-module-gconf pulseaudio-module-udev{a} 
  pulseaudio-module-x11{a} python-apport{a} python-apt{a} 
  python-aptdaemon{a} python-aptdaemon-gtk{a} python-avahi{a} 
  python-brlapi{a} python-cairo{a} python-central{a} python-configglue{a} 
  python-couchdb{a} python-crypto{a} python-cups{a} python-cupshelpers{a} 
  python-dbus{a} python-debian{a} python-desktopcouch{a} 
  python-desktopcouch-records{a} python-fstab{a} python-gconf{a} 
  python-gdbm{a} python-glade2{a} python-gmenu{a} python-gnome2{a} 
  python-gnomeapplet{a} python-gnomecanvas{a} python-gnomekeyring{a} 
  python-gnupginterface{a} python-gobject{a} python-gst0.10{a} 
  python-gtk2{a} python-gtkhtml2{a} python-gtksourceview2{a} 
  python-httplib2{a} python-ibus{a} python-imaging{a} 
  python-launchpad-integration{a} python-launchpadlib{a} 
  python-lazr-restfulclient{a} python-lazr-uri{a} python-libxml2{a} 
  python-louis{a} python-notify{a} python-oauth{a} python-openssl{a} 
  python-pam{a} python-papyon{a} python-pkg-resources{a} 
  python-problem-report{a} python-protobuf{a} python-pyatspi{a} 
  python-pyinotify{a} python-pyorbit{a} python-rdflib{a} python-rsvg{a} 
  python-serial{a} python-sexy{a} python-simplejson{a} python-smbc{a} 
  python-software-properties{a} python-speechd{a} python-support{a} 
  python-telepathy{a} python-twisted-bin{a} python-twisted-core{a} 
  python-twisted-names{a} python-twisted-web{a} python-ubuntuone-client{a} 
  python-ubuntuone-storageprotocol{a} python-virtkey{a} python-vte{a} 
  python-wadllib{a} python-webkit{a} python-xapian{a} python-xdg{a} 
  python-xkit{a} python-zope.interface{a} rdesktop{a} rhythmbox 
  same-gnome{a} screen-resolution-extra{a} seahorse software-center 
  software-properties-gtk speech-dispatcher{a} 
  system-config-printer-common{a} system-config-printer-gnome 
  system-config-printer-udev{a} telepathy-butterfly{a} telepathy-haze{a} 
  tomboy totem totem-common{a} totem-mozilla{a} totem-plugins{a} tsclient 
  ubufox{a} ubuntu-artwork ubuntu-desktop ubuntu-docs 
  ubuntu-system-service{a} ubuntu-wallpapers{a} ubuntuone-client{a} 
  ubuntuone-client-gnome unattended-upgrades{a} update-manager 
  update-manager-core{a} update-notifier update-notifier-common{a} 
  usb-creator-common{a} usb-creator-gtk vinagre vino xulrunner-1.9.1{a} 
  yelp{a} 
The following packages will be REMOVED:
  java-common{u} libass3{u} libdca0{u} libdvbpsi5{u} libebml0{u} 
  libfaad0{u} libggi-target-x{u} libggi2{u} libgii1{u} libgii1-target-x{u} 
  libiso9660-5{u} liblua5.1-0{u} libmatroska0{u} libmodplug0c2{u} 
  libmpcdec3{u} libsvga1{u} libvcdinfo0{u} 
0 packages upgraded, 287 newly installed, 17 to remove and 13 not upgraded.
Need to get 124MB/125MB of archives. After unpacking 910MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
root@custom:/# apt-get install -f python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libdca0 java-common libass3 python2.5 libdvbpsi5 libggi-target-x
  libggi2 libgii1 libgii1-target-x libiso9660-5 liblua5.1-0 libdb4.6
  libmodplug0c2 libvcdinfo0 libebml0 libmpcdec3 libmatroska0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# dpkg --configure python -a
dpkg: error processing python (--configure):
 package python is already installed and configured
dpkg: error processing -a (--configure):
 no package named `-a' is installed, cannot configure
Errors were encountered while processing:
 python
 -a
root@custom:/# dpkg --configure python
dpkg: error processing python (--configure):
 package python is already installed and configured
Errors were encountered while processing:
 python
root@custom:/# apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libsvga1 libdca0 java-common libass3 python2.5 libdvbpsi5 libggi-target-x
  libggi2 libgii1 libgii1-target-x libiso9660-5 liblua5.1-0 libdb4.6
  libmodplug0c2 libvcdinfo0 libebml0 libmpcdec3 libmatroska0 libfaad0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  java-common libass3 libdb4.6 libdca0 libdvbpsi5 libebml0 libfaad0
  libggi-target-x libggi2 libgii1 libgii1-target-x libiso9660-5 liblua5.1-0
  libmatroska0 libmodplug0c2 libmpcdec3 libsvga1 libvcdinfo0 python2.5
0 upgraded, 0 newly installed, 19 to remove and 13 not upgraded.
After this operation, 18.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 226399 files and directories currently installed.)
Removing java-common ...
Removing libass3 ...
Removing python2.5 ...
Removing libdb4.6 ...
Removing libdca0 ...
Removing libdvbpsi5 ...
Removing libmatroska0 ...
Removing libebml0 ...
Removing libfaad0 ...
Removing libggi-target-x ...
Removing libggi2 ...
Removing libgii1-target-x ...
Removing libgii1 ...
Removing libvcdinfo0 ...
Removing libiso9660-5 ...
Removing liblua5.1-0 ...
Removing libmodplug0c2 ...
Removing libmpcdec3 ...
Removing libsvga1 ...
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
root@custom:/# apt-get reinstall python2.6
E: Invalid operation reinstall
root@custom:/# apt-get install python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.6 is already the newest version.
python2.6 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
root@custom:/# 

**Can someone tell me what seems wrong?**

---

### Post by richlyn9 on 2010-11-22
I googled for init:job_process.c:529 unhandled error from job_process_spawn and found a couple of threads
from which i found out that there may be some issues with my fsab


what say should i look up that angle?

---

### Post by sikander3786 on 2010-11-22
The problem lies with the syntax of your commands.

```
dpkg --configure python -a
```

It should be

```
dpkg --configure python
```

or

```
dpkg --configure -a
```

The 2nd one was successful so all the packages are configured properly on your system.

```
apt-get reinstall python2.6
```

This should look like,

```
apt-get install --reinstall python2.6
```

I doubt if it is an issue with your fstab. But you can let us check that by posting the output of

```
cat /etc/fstab
```

and

```
sudo blkid
```

---

### Post by richlyn9 on 2010-11-22
will try this tomorrow and let you know as i am not at my pc now.

Thanks much....

---

### Post by richlyn9 on 2010-11-22
tried this and the reinstall did not work

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

custom@custom:~$ sudo mount /dev/sda9 /mnt
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo mount --bind /proc /mnt/proc
custom@custom:~$ sudo mount --bind /dev/pts /mnt/dev/pts
custom@custom:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
custom@custom:~$ sudo chroot /mnt
root@custom:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# ln -s /bin/true /sbin/initctl
root@custom:/# dpkg --configure python
dpkg: error processing python (--configure):
 package python is already installed and configured
Errors were encountered while processing:
 python
root@custom:/# dpkg --configure -a
root@custom:/# apt-get --reinstall python2.6
E: Invalid operation python2.6
root@custom:/# apt-get --reinstall python
E: Invalid operation python
root@custom:/# apt-get --reinstall python 2.6
E: Invalid operation python
root@custom:/# cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=2f1cb3a7-9be0-4faa-be09-102e6a7566b5 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb1 during installation
UUID=ac04653b-0c68-469f-b8a9-9bb1b00b2eac /home           ext3    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=a50ea22f-7003-461e-9bff-72457bd9b3b5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
root@custom:/# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="84F48DC0F48DB548" TYPE="ntfs" 
/dev/sda2: UUID="3A341BC3341B80D5" LABEL="data" TYPE="ntfs" 
/dev/sda5: UUID="E8CC2B97CC2B5F56" LABEL="media" TYPE="ntfs" 
/dev/sda6: UUID="3A6C4D436C4CFAE1" LABEL="Lit" TYPE="ntfs" 
/dev/sda7: UUID="4CD8642DD864180A" TYPE="ntfs" 
/dev/sda8: UUID="a50ea22f-7003-461e-9bff-72457bd9b3b5" TYPE="swap" 
/dev/sda9: UUID="2f1cb3a7-9be0-4faa-be09-102e6a7566b5" TYPE="ext3" 
/dev/sda10: LABEL="Lucid" UUID="b4d8e3fc-dec6-4c2a-9ba0-5235552f88fe" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: LABEL="Burg" UUID="4589a57e-f0a2-4fef-b1f0-63a82a374d56" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="ac04653b-0c68-469f-b8a9-9bb1b00b2eac" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="b89b6e02-fa26-488c-879f-e2f122d45b13" SEC_TYPE="ext2" TYPE="ext3" 
root@custom:/#

---

### Post by sikander3786 on 2010-11-23
Your fstab entries looks fine. No problem there.

Remember, re-install is the last option ;-)

---

### Post by richlyn9 on 2010-11-23
:cry::cry::cry::cry::???

---

### Post by mc4man on 2010-11-23
When you removed python2.6 you probably also removed 300 or so add. packages. Sorta of curious why you didn't go ahead and install ubuntu-desktop in post 15
If I had a karmic install I'd show you basically what happened, attached is what would happen here on MY maverick

(if you're trying to reinstall a package look a bit closer at a previous post, you need to use a command, install, and the option --reinstall

---

### Post by richlyn9 on 2010-11-24
i did try that but i said that it would be installing so many number of packages amounting to some  900 mb which is as good as the basic install
so i thought logically that it dosen't seem right hence said no
and BTY i have a dial up connection and would take almost a week to get it done hence the initial hesitation.

---

### Post by richlyn9 on 2010-11-24
but i installed python 2.6 again which installed fine.
so you mean that seem deps are not installed?
is there some way i can just install the basic packages needed to boot up

BTY i did try the python reinstall

[I]root@custom:/# apt-get --reinstall python2.6
E: Invalid operation python2.6
root@custom:/# apt-get --reinstall python
E: Invalid operation python
root@custom:/# apt-get --reinstall python 2.6
E: Invalid operation python[/I]

---

### Post by sikander3786 on 2010-11-24
Regarding the error in your above post,

> root@custom:/# apt-get --reinstall python2.6
E: Invalid operation python2.6

Please take a look at post # 17 and see what command should be used.

[http://ubuntuforums.org/showpost.php?p=10148778&postcount=17](http://ubuntuforums.org/showpost.php?p=10148778&postcount=17)

**mc4man** also advised in post # 22 that,

> (if you're trying to reinstall a package look a bit closer at a previous post, you need to use a command, install, and the option --reinstall

Please read the previous posts thoroughly instead of posting the same query again and again.

Thanks.

---

### Post by richlyn9 on 2010-11-24
> **sikander3786 said:**
> 

Please read the previous posts thoroughly instead of posting the same query again and again.


:redface::oops:
I have been acting Dumb...Sorry people

i get it

---

### Post by sikander3786 on 2010-11-24
> **richlyn9 said:**
> :redface::oops:
I have been acting Dumb...Sorry people

i get it
No problem at all :-)

You are welcome for any further "New" queries :D

If you'd done that from the start, we would have got more closer to the solution to your problem rather than wondering here and there :P

---

### Post by richlyn9 on 2010-11-25
all right did that

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

custom@custom:~$ sudo mount /dev/sda9 /mnt
custom@custom:~$ sudo mount --bind /dev /mnt/dev
custom@custom:~$ sudo mount --bind /proc /mnt/proc
custom@custom:~$ sudo mount --bind /dev/pts /mnt/dev/pts
custom@custom:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
custom@custom:~$ sudo chroot /mnt
root@custom:/# dpkg-divert --local --rename --add /sbin/initctl
Leaving `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@custom:/# ln -s /bin/true /sbin/initctl
ln: creating symbolic link `/sbin/initctl': File exists
root@custom:/# apt-get install --reinstall python2.6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 13 not upgraded.
Need to get 0B/2,444kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 225438 files and directories currently installed.)
Preparing to replace python2.6 2.6.4-0ubuntu3 (using .../python2.6_2.6.4-0ubuntu3_i386.deb) ...
Unpacking replacement python2.6 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for menu ...
Setting up python2.6 (2.6.4-0ubuntu3) ...

Processing triggers for menu ...
root@custom:/#

---

### Post by richlyn9 on 2010-11-25
i rebooted and it went past the grub but gave me an error of the resoloution
i selected to boot up the session in low resoloution mode but that did not happen 

am wondering how can i chroot from my **64 bit Lucid into the broken 32 bit karmic** and then probably i can mount and add the live cd as source and get the basic packages installed...can that be done???

---

### Post by richlyn9 on 2010-11-25
> **richlyn9 said:**
> 

 can i chroot from my **64 bit Lucid into the broken 32 bit karmic**

i came across with this [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
 but am not sure
as when i tried this [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) it actually downloading the basic packages for the target system in my 64 bit install.

---

### Post by sikander3786 on 2010-11-25
> **richlyn9 said:**
> i came across with this [http://ubuntuforums.org/showthread.php?t=24575](http://ubuntuforums.org/showthread.php?t=24575)
 but am not sure
as when i tried this [https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot) it actually downloading the basic packages for the target system in my 64 bit install.
I am reading all your posts and will try to help where ever I can.

I mentioned earlier that I have no experience with chroot, so can't help :-(

Just posting so you don't feel alone here :P

Some other mate needs to jump in for that.

---

### Post by richlyn9 on 2010-11-25
> **sikander3786 said:**
> I am reading all your posts and will try to help where ever I can.

I mentioned earlier that I have no experience with chroot, so can't help :-(

Just posting so you don't feel alone here :P



Hey Mate Thanks!!!! I appreciate your concern.:P
I will keep on posting so that this will catch someones eye...

---

### Post by richlyn9 on 2010-11-25
MAy i know what this will do
[B]
sudo debootstrap --arch i386 karmic /chroot/ [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)[/B]

will it download the entire karmic build on my system?

---

### Post by richlyn9 on 2010-11-27
I tried 
sudo debootstrap --arch i386 karmic /chroot/
[http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

and looks like its downloading the entire repository again.....:(

---

### Post by richlyn9 on 2010-11-29
still trying to  figure out how i can fix this...(dont want to reinstall)

---

### Post by richlyn9 on 2010-12-02
I am looking at possiblities using an alternate CD and somehow trying to get it fixed

---

### Post by richlyn9 on 2010-12-09
I finally installed The Ubuntu Maverick 10.10 and fixed my issue.Though i was unable to solve it.

---

