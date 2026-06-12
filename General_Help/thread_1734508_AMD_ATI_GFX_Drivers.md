---
title: "AMD ATI GFX Drivers"
date: 2011-04-20
forum: General Help
---

### Post by hemmjonny on 2011-04-20
Hi all,

I have messed up, I thought i would try and be a smart *** and download the latest drivers from AMD.

so i downloaded them and installed them. then i ended up with 2 ATI Catalyst control centers and the GFX was very jerky. so i think i uninstantiated them and the rest of the ATI stuff from synaptic package manager.  then i rebooted i opened update manager  now when i try and install them from there it says:

The Package system is broken

if you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

details:
fglrx-amdcccle

I really don't know what to do now can anyone help i have only been useing Ubuntu for about a week or so and i really really like cant believe i have messed it up :(

---

### Post by hemmjonny on 2011-04-20
tried installed the ATI drivers again from the AMD website but still not working right i really need this fixed by tomorrow as i have a load of design work to do :(  i am so angry with myself why did i have to do that.

---

### Post by Jechem on 2011-04-20
What release do you have? 10.04 or 10.10?

10.04 ATI installation:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Updating_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Updating_the_Driver)

10.10 ATI installation:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_the_Driver)

---

### Post by hemmjonny on 2011-04-20
running 10.10 thanks for your reply.

i am getting this at the end after i run create .dep packages

0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.m81IbH'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.dBSDBo


any ideas?

Thanks

Jonathan

---

### Post by Jechem on 2011-04-20
I assume you are running 10.10 32bit. You can purge the fglrx and start again. Have you tried the PPA? It's much easier than having to manually build the driver. Have you installed the prerequisites before building the .debs? I'm not an expert on this but I think there are missing dependencies for it to finish building the .deb package. You can try fixing the broken dependencies in Synaptic Package Manager>Edit>Fix Broken Packages.

You can purge the drivers or what is left of it and install the one from the PPA or activate the default in System>Administration>Hardware Drivers.

I'm not sure if this can help:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> I assume you are running 10.10 32bit. You can purge the fglrx and start again. Have you tried the PPA? It's much easier than having to manually build the driver. Have you installed the prerequisites before building the .debs? I'm not an expert on this but I think there are missing dependencies for it to finish building the .deb package. You can try fixing the broken dependencies in Synaptic Package Manager>Edit>Fix Broken Packages.

You can purge the drivers or what is left of it and install the one from the PPA or activate the default in System>Administration>Hardware Drivers.

I'm not sure if this can help:
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)


Sorry my bad i am running 64bit 10.10.

What does PPA stand for?

I have tried  Fix Broken Packages and it gives me this error "E: /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb: subprocess new pre-installation script returned error exit status 1"

also i have tried the additional drivers and that gives me this error "SystemError: installArchives() failed"

then that send me to update manager that give me this error "The package system is broken

If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f
Details:
fglrx-amdcccle

I have tried removing everything from the commands in the links you sent me but still does the same when i reinstall them. i just want it back to how it was lol just with the standard drivers that Ubuntu get me. 

think i have a lot to learn about Ubuntu i thought i was doing really well till this point i could do every thing i needed to install apps remove apps all was going really good.

Thanks again

Jonathan

---

### Post by hemmjonny on 2011-04-21
Anyone got any ideas how to fix this (I think the G/F will take my balls if i have to spend another day Installing everything)

---

### Post by hemmjonny on 2011-04-21
My be this would be better in "Installation and Upgrades" could a mob move it for me please. i put it in here as i thought it would be an easy one to fix but its not looking like that now :(

---

### Post by hemmjonny on 2011-04-21
Ok i will now pay if that helps to get this fixed :)

---

### Post by hemmjonny on 2011-04-21
Tried  apt-get install -f and got this error:

hemmjonny@pro-net-laptop:~$ sudo apt-get install -f
[sudo] password for hemmjonny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/31.7MB of archives.
After this operation, 108MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 147965 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu2_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


the log 

*** ATI Catalyst(TM) Proprietary Driver Uninstall Log 2011-04-21 10:40:35 ***
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_cs.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_da_DK.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_de.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_el_GR.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_es_ES.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_fi_FI.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_fr_FR.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_hu_HU.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_it_IT.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_ja.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_ko_KR.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_nl_NL.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_no.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_pl.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_pt_BR.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_ru_RU.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_sv_SE.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_th.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_tr_TR.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_zh_CN.qm.
md5sum integrity check failed for /usr/share/ati/amdcccle/amdcccle_zh_TW.qm.
File is missing from system /usr/bin/amdcccle.
File is missing from system /usr/bin/amdxdg-su.
File is missing from system /usr/lib64/xorg/modules/drivers/fglrx_drv.so.
File is missing from system /usr/lib32/libaticalcl.so.
File is missing from system /usr/lib32/libaticalrt.so.
File is missing from system /usr/lib32/fglrx/libGL.so.1.2.
File is missing from system /usr/lib64/libAMDXvBA.cap.
File is missing from system /usr/lib64/libaticalcl.so.
File is missing from system /usr/lib64/libaticalrt.so.
File is missing from system /usr/lib64/fglrx/libGL.so.1.2.
File is missing from system /usr/lib64/dri/fglrx_dri.so.
File is missing from system /usr/bin/fgl_glxgears.
File is missing from system /usr/bin/fglrxinfo.
File is missing from system /usr/bin/aticonfig.
File is missing from system /usr/bin/atiodcli.
File is missing from system /usr/bin/atiode.
File is missing from system /etc/ati/amdpcsdb.default.
File is missing from system /etc/ati/atiogl.xml.
File is missing from system /etc/ati/authatieventsd.sh.
File is missing from system /etc/ati/control.
File is missing from system /etc/ati/logo.xbm.example.
File is missing from system /etc/ati/logo_mask.xbm.example.
File is missing from system /etc/ati/signature.
/usr/bin/md5sum: /usr/X11R6/lib64/modules/dri/fglrx_dri.so: No such file or directory
md5sum integrity check failed for /usr/X11R6/lib64/modules/dri/fglrx_dri.so.
File is missing from system /etc/modprobe.d/blacklist-fglrx.conf.
File has been removed, //usr/lib64/libGL.so.1.2, since last install.
One or more files have been altered since installation.
Uninstall will not be completed.

To force uninstall, removing all installed files without verification,
run /usr/share/ati/amd-uninstall.sh --force.

Forcing uninstall is not recommended and may cause system corruption.

---

### Post by Jechem on 2011-04-21
Sorry to hear that you still have not sorted out the problem about your ATI Driver.

You can run this in terminal to purge the existing installation:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

---

### Post by hemmjonny on 2011-04-21
did that and got this:

hemmjonny@pro-net-laptop:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
[sudo] password for hemmjonny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-modaliases' for regex 'fglrx_*'
Note, selecting 'fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx_*'
Note, selecting 'fglrx-driver' for regex 'fglrx_*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-control' for regex 'fglrx_*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx_*'
Note, selecting 'fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx-dev*'
Virtual packages like 'xorg-driver-fglrx' can't be removed
Package fglrx is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  fglrx-amdcccle* fglrx-modaliases*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9,712kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 147964 files and directories currently installed.)
Removing fglrx-amdcccle ...
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/lib/fglrx' not empty so not removed.
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/share/ati' not empty so not removed.
Removing fglrx-modaliases ...
hemmjonny@pro-net-laptop:~$

---

### Post by mastablasta on 2011-04-21
this removed the packages and driver. you shoul dbe able to reinstall it form scratch. though i am not sure this is a good sign of removal:
 
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/lib/fglrx' not empty so not removed.
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/share/ati' not empty so not removed.

---

### Post by hemmjonny on 2011-04-21
Tried to install the driver from additional drivers again but still does that same :(

---

### Post by Jechem on 2011-04-21
Let's get back to the start. I think we've messed up somewhere with the driver downloads.

let's do it again step by step.

purge the fglrx driver with the previous command. check?

install build essential:
```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0

```
check?
```
sudo apt-get install ia32-libs
```
check?

make catalyst directory
```
cd ~/; mkdir catalyst11.3; cd catalyst11.3/
```
check?

download driver:
```
wget http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run
```
check?

make executable:
```
chmod +x ati-driver-installer-11-3-x86.x86_64.run
```
check?

remove other radeon drivers possibly installed:
```
sudo apt-get remove --purge xserver-xorg-video-radeon
```
check?

build .deb files:
```
sh ati-driver-installer-11-3-x86.x86_64.run --buildpkg Ubuntu/maverick
```
check?

install .deb files:
```
sudo dpkg -i fglrx*.deb
```
check?

if this doesn't install it then try:
```
sudo dpkg -i --force-overwrite fglrx*.deb
```

configure ATI:
```
sudo aticonfig --initial -f
```
check?

---

### Post by mastablasta on 2011-04-21
yes it appears the non working version has not been removed completelly.
 
you never mentioned your graphics card or i overlooked it. Not all ATI cards are supported by proprietary drivers.

---

### Post by Jechem on 2011-04-21
Have you tried this to get back the original open source drivers?

> If you plan on using open-source drivers, you will need to reinstall some packages because Catalyst overwrites or diverts some key 3D libraries with proprietary versions. For more information on this issue, see this Ubuntu wiki page
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

### Post by hemmjonny on 2011-04-21
OK it went wrong :( 
----------
hemmjonny@pro-net-laptop:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx-modaliases' for regex 'fglrx_*'
Note, selecting 'fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx_*'
Note, selecting 'fglrx-driver' for regex 'fglrx_*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-control' for regex 'fglrx_*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx_*'
Note, selecting 'fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx-dev*'
Virtual packages like 'xorg-driver-fglrx' can't be removed
Package fglrx-modaliases is not installed, so not removed
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hemmjonny@pro-net-laptop:~$ 


------------------
hemmjonny@pro-net-laptop:~$ sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libqtgui4 wget execstack libelfg0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
cdbs is already the newest version.
debconf is already the newest version.
debhelper is already the newest version.
dh-make is already the newest version.
execstack is already the newest version.
fakeroot is already the newest version.
libelfg0 is already the newest version.
libstdc++6 is already the newest version.
wget is already the newest version.
dkms is already the newest version.
libqtgui4 is already the newest version.
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hemmjonny@pro-net-laptop:~$ 


------------

hemmjonny@pro-net-laptop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hemmjonny@pro-net-laptop:~$ 


----------

hemmjonny@pro-net-laptop:~$ cd ~/; mkdir catalyst11.3; cd catalyst11.3/
mkdir: cannot create directory `catalyst11.3': File exists
hemmjonny@pro-net-laptop:~/catalyst11.3$

--------

hemmjonny@pro-net-laptop:~$ wget [http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)
--2011-04-21 14:47:01--  [http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-11-3-x86.x86_64.run)
Resolving www2.ati.com... 62.41.85.112, 62.41.85.98
Connecting to www2.ati.com|62.41.85.112|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 72899696 (70M) [application/octet-stream]
Saving to: `ati-driver-installer-11-3-x86.x86_64.run'

100%[======================================>] 72,899,696   817K/s   in 87s     

2011-04-21 14:48:29 (814 KB/s) - `ati-driver-installer-11-3-x86.x86_64.run' saved [72899696/72899696]

hemmjonny@pro-net-laptop:~$


--------

hemmjonny@pro-net-laptop:~$ chmod +x ati-driver-installer-11-3-x86.x86_64.run
hemmjonny@pro-net-laptop:~$ 


----

hemmjonny@pro-net-laptop:~$ sudo apt-get remove --purge xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  xserver-xorg-video-ati* xserver-xorg-video-radeon*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 1,470kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 147924 files and directories currently installed.)
Removing xserver-xorg-video-ati ...
Removing xserver-xorg-video-radeon ...
Purging configuration files for xserver-xorg-video-radeon ...
Processing triggers for man-db ...
hemmjonny@pro-net-laptop:~$ 


--------

hemmjonny@pro-net-laptop:~$ sh ati-driver-installer-11-3-x86.x86_64.run --buildpkg Ubuntu/maverick
Created directory fglrx-install.ygN5ly
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.831.2.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Generating package: Ubuntu/maverick
Package build failed!
Package build utility output:
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package fglrx-installer
dpkg-buildpackage: source version 2:8.831-0ubuntu1
dpkg-buildpackage: source changed by ATI Technologies Inc. <http://ati.amd.com/support/driver.html>
 dpkg-source --before-build fglrx.VEFcb5
dpkg-buildpackage: host architecture amd64
 debian/rules build
#Create important strings
for i in 10fglrx \
             dkms.conf \
             fglrx.install \
             fglrx-dev.install \
             fglrx-amdcccle.install \
             overrides/fglrx; do \
        sed -e "s|#XMODDIR#|usr/lib/fglrx/xorg/modules|"     \
            -e "s|#XMODDIR32#||" \
            -e "s|#DRIDIR32#|usr/lib32/fglrx|"   \
            -e "s|#LIBDIR#|lib64|"       \
            -e "s|#DRIDIR#|usr/lib/fglrx|"       \
            -e "s|#CVERSION#|8.831|"   \
            -e "s|#XARCH#|xpic_64a|"   \
            -e "s|#ARCH#|x86_64|"   \
            debian/$i.in > debian/$i;      \
    done
# remove exec bit on everything
find arch \
        etc \
        lib \
        module \
        usr \
        xpic_64a     -type f | xargs chmod -x
find: `module': No such file or directory
# set executable on user apps
find arch/x86_64/usr/sbin \
        arch/x86_64/usr/X11R6/bin \
        usr/sbin/ -type f | xargs chmod a+x
# set exec bit on scripts
find lib etc debian -name "*.sh" -type f | xargs chmod +x
# Generate modaliases
sh -e debian/modaliases/fglrx_supported \
        lib/modules/fglrx/build_mod/fglrxko_pci_ids.h > \
        debian/modaliases/fglrx-modules.alias.override
dh build
   dh_testdir
   dh_auto_configure
   dh_auto_build
   dh_auto_test
 fakeroot debian/rules binary
#Steps that we can't easily represent in debhelper files or .in files yet
dh_install -pfglrx    "arch/x86/usr/X11R6/lib/libAMD*.so*"           "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/*.so*"           "usr/lib32/fglrx"
dh_installdirs -pfglrx "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/X11R6/lib/modules/dri"     "usr/lib32/fglrx"
dh_install -pfglrx "arch/x86/usr/lib/*"                     "usr/lib32/fglrx"
for i in \
            debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib32/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib32/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib32/fglrx/libGL.so.1.2
#they don't provide the symlink for us (starting at 8.699)
dh_link -pfglrx usr/lib32/fglrx/libatiuki.so.1.0 usr/lib32/fglrx/libatiuki.so.1
dh_installdocs -pfglrx usr/share/doc/fglrx/* --exclude ATI_LICENSE.TXT
dh_installinit -pfglrx --name="atieventsd" --no-start --update-rcd-params="defaults 31"
Duplicate specification "O=s" for option "O"
#remove executable bits from stack
dh_install -pfglrx-amdcccle
execstack -c debian/fglrx-amdcccle/usr/lib/fglrx/bin/amdcccle
dh_install -pfglrx
for i in \
            debian/fglrx/usr/lib/fglrx/bin/atiode \
            debian/fglrx/usr/lib/fglrx/bin/amdnotifyui \
            debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so \
            debian/fglrx/usr/lib/fglrx/libGL.so.* \
            ; do execstack -q $i; execstack -c $i; done
- debian/fglrx/usr/lib/fglrx/bin/atiode
- debian/fglrx/usr/lib/fglrx/bin/amdnotifyui
- debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so
- debian/fglrx/usr/lib/fglrx/libGL.so.1
- debian/fglrx/usr/lib/fglrx/libGL.so.1.2
# Make some additional scripts executable
find debian/fglrx-amdcccle/usr/lib/fglrx/bin/ \
        -type f | xargs chmod a+x
# Blacklist any other driver that udev may want to load instead of fglrx
printf "blacklist radeon\n" > /tmp/fglrx.VEFcb5/debian/fglrx/lib/fglrx/modprobe.conf
#ld.so.conf
echo "/usr/lib/fglrx" >    "/tmp/fglrx.VEFcb5/debian/fglrx/usr/lib/fglrx/ld.so.conf"
echo "/usr/lib32/fglrx" >>    "/tmp/fglrx.VEFcb5/debian/fglrx/usr/lib/fglrx/ld.so.conf"
#Run the normal stuff
dh binary-arch
   dh_testroot -a -Nfglrx -Nfglrx-amdcccle
   dh_prep -a -Nfglrx -Nfglrx-amdcccle
   dh_installdirs -a -Nfglrx -Nfglrx-amdcccle
   dh_auto_install -a -Nfglrx -Nfglrx-amdcccle
   dh_install -a -Nfglrx -Nfglrx-amdcccle
   dh_installdocs -a -Nfglrx
   dh_installchangelogs -a
   dh_installexamples -a
   dh_installman -a
   dh_installcatalogs -a
   dh_installcron -a
   dh_installdebconf -a
   dh_installemacsen -a
   dh_installifupdown -a
   dh_installinfo -a
   dh_pysupport -a
   dh_installinit -a -Nfglrx
Duplicate specification "O=s" for option "O"
   dh_installmenu -a
   dh_installmime -a
   dh_installmodules -a
   dh_installlogcheck -a
   dh_installlogrotate -a
   dh_installpam -a
   dh_installppp -a
   dh_installudev -a
   dh_installwm -a
   dh_installxfonts -a
   dh_bugfiles -a
   dh_lintian -a
   dh_gconf -a
   dh_icons -a
   dh_perl -a
   dh_usrlocal -a
   dh_link -a -Nfglrx
   dh_compress -a
   dh_fixperms -a
   dh_strip -a
   dh_makeshlibs -a
objdump: debian/fglrx/usr/lib/fglrx/ld.so.conf: File format not recognized
   debian/rules override_dh_shlibdeps
make[1]: Entering directory `/tmp/fglrx.VEFcb5'
dh_shlibdeps -l/tmp/fglrx.VEFcb5/debian/fglrx/usr/lib/fglrx:/tmp/fglrx.VEFcb5/debian/fglrx/usr/lib32/fglrx -Xlib32
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 contains an unresolvable reference to symbol dlsym: it's probably a plugin.
dpkg-shlibdeps: warning: 22 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/bin/atieventsd contains an unresolvable reference to symbol XauFileName: it's probably a plugin.
dpkg-shlibdeps: warning: debian/fglrx/usr/lib/fglrx/libGL.so.1.2 contains an unresolvable reference to symbol XOpenDisplay: it's probably a plugin.
dpkg-shlibdeps: warning: 33 other similar warnings have been skipped (use -v to see them all).
dpkg-shlibdeps: error: no dependency information found for /usr/share/ati/lib64/libQtCore.so.4 (used by debian/fglrx/usr/lib/fglrx/bin/amdnotifyui).
dh_shlibdeps: dpkg-shlibdeps -Tdebian/fglrx.substvars debian/fglrx/usr/lib/fglrx/libatiadlxx.so debian/fglrx/usr/lib/fglrx/libaticaldd.so debian/fglrx/usr/lib/fglrx/libatiuki.so.1.0 debian/fglrx/usr/lib/fglrx/libfglrx_dm.so.1.0 debian/fglrx/usr/lib/fglrx/bin/fglrxinfo debian/fglrx/usr/lib/fglrx/bin/fgl_glxgears debian/fglrx/usr/lib/fglrx/bin/atiodcli debian/fglrx/usr/lib/fglrx/bin/amdnotifyui debian/fglrx/usr/lib/fglrx/bin/atieventsd debian/fglrx/usr/lib/fglrx/bin/atiode debian/fglrx/usr/lib/fglrx/bin/aticonfig debian/fglrx/usr/lib/fglrx/libaticalrt.so debian/fglrx/usr/lib/fglrx/libaticalcl.so debian/fglrx/usr/lib/fglrx/xorg/modules/linux/libfglrxdrm.so debian/fglrx/usr/lib/fglrx/xorg/modules/drivers/fglrx_drv.so debian/fglrx/usr/lib/fglrx/xorg/modules/amdxmm.so debian/fglrx/usr/lib/fglrx/xorg/modules/glesx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/fglrx/libglx.so debian/fglrx/usr/lib/fglrx/xorg/modules/extensions/libglx.so debian/fglrx/usr/lib/fglrx/libGL.so.1.2 debian/fglrx/usr/lib/fglrx/dri/fglrx_dri.so debian/fglrx/usr/lib/fglrx/libAMDXvBA.so.1.0 debian/fglrx/usr/lib/fglrx/libXvBAW.so.1.0 returned exit code 2
make[1]: *** [override_dh_shlibdeps] Error 9
make[1]: Leaving directory `/tmp/fglrx.VEFcb5'
make: *** [binary-arch] Error 2
dpkg-buildpackage: error: fakeroot debian/rules binary gave error exit status 2
Removing temporary directory: fglrx-install.ygN5ly
hemmjonny@pro-net-laptop:~$ 



------------------

hemmjonny@pro-net-laptop:~$ sudo dpkg -i fglrx*.deb
dpkg: error processing fglrx*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx*.deb
hemmjonny@pro-net-laptop:~$ sudo dpkg -i --force-overwrite fglrx*.deb
dpkg: error processing fglrx*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 fglrx*.deb
hemmjonny@pro-net-laptop:~$

---

### Post by hemmjonny on 2011-04-21
> **mastablasta said:**
> yes it appears the non working version has not been removed completelly.
 
you never mentioned your graphics card or i overlooked it. Not all ATI cards are supported by proprietary drivers.

Hi there, my card is:
Manhattan [Mobility Radeon HD 5000 Series]

I just want the driver back that ubuntu install by its self  they worked really well i don't know why i had to mess with it :S

Thanks

Jonathan

---

### Post by Jechem on 2011-04-21
there's something wrong with your dependencies during the building of the .deb files.

you can purge your fglrx again just to make sure that there is nothing left with the old driver installation with:
```
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev* xorg-driver-fglrx
```

and run the following to install the open drivers ( the ones you used before):

```
$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
$ sudo apt-get install xserver-xorg-video-ati
$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by hemmjonny on 2011-04-21
All good until the last one:

hemmjonny@pro-net-laptop:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backupmv: cannot stat `/etc/X11/xorg.conf': No such file or directory
hemmjonny@pro-net-laptop:~$ 


Thanks for helping mate

---

### Post by Jechem on 2011-04-21
That's ok it just means you still have no xorg config file. After that's installed, check System>Administration>Hardware Drivers
activate it if necessary.

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> That's ok it just means you still have no xorg config file. After that's installed, check System>Administration>Hardware Drivers
activate it if necessary.

Clicked activate now back to the beginning 

came up with the error:
SystemError: installArchives() failed

Then the update manager pops up and puts this error up:
If you are using third party repositories then disable them, since they are a common source of problems.
Now run the following command in a terminal: apt-get install -f

then will have to go to the synaptic package manager to fix but then that gives an error:
An error occurred

The following details are provided:

E: /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb: subprocess new pre-installation script returned error exit status 1

---

### Post by Jechem on 2011-04-21
run sudo apt-get -f install

---

### Post by Jechem on 2011-04-21
run 
```
sudo dpkg --configure -a
```
this corrects the broken synaptic manager

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> run sudo apt-get -f install


hemmjonny@pro-net-laptop:~$ sudo apt-get -f install
[sudo] password for hemmjonny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fglrx
The following NEW packages will be installed
  fglrx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/31.7MB of archives.
After this operation, 108MB of additional disk space will be used.
Do you want to continue [Y/n]? Y   
(Reading database ... 147961 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu2_amd64.deb) ...
One or more files have been altered since installation.
Uninstall will not be completed. See /etc/ati/fglrx-uninstall.log for details.
dpkg: error processing /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
hemmjonny@pro-net-laptop:~$

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> run 
```
sudo dpkg --configure -a
```this corrects the broken synaptic manager

hemmjonny@pro-net-laptop:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fglrx-amdcccle
hemmjonny@pro-net-laptop:~$

---

### Post by Jechem on 2011-04-21
We're just going around in circles mate.:P

If you don't have anything important on your box then you can do a complete reinstall of Ubuntu 10.10. It's much easier than figuring out what has messed up your dependencies and packages.:D

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> We're just going around in circles mate.:P

If you don't have anything important on your box then you can do a complete reinstall of Ubuntu 10.10. It's much easier than figuring out what has messed up your dependencies and packages.:D


I think it is going to come down to that :(  it took me ages setting everything up how i want it lol ah well if thats that only answer :( Think my G/F is gonna kill me as i spent all of last weekend setting it up and looks like i will be doing the same this weekend 

ah well

Thanks very very much for your time and help.

---

### Post by Jechem on 2011-04-21
Last ditch effort before doing a reinstall:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo apt-get install --reinstall xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> Last ditch effort before doing a reinstall:

sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo apt-get install --reinstall xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg


hemmjonny@pro-net-laptop:~$ sudo apt-get remove --purge xorg-driver-fglrx fglrx*[sudo] password for hemmjonny: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'xorg-driver-fglrx' can't be removed
Note, selecting 'fglrx-modaliases' for regex 'fglrx*'
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx*'
Note, selecting 'fglrx-driver' for regex 'fglrx*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-control' for regex 'fglrx*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx*'
Note, selecting 'fglrx-dev' for regex 'fglrx*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx*'
Package fglrx-modaliases is not installed, so not removed
Package fglrx is not installed, so not removed
Package fglrx-dev is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  fglrx-amdcccle*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9,642kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 147960 files and directories currently installed.)
Removing fglrx-amdcccle ...
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/lib/fglrx' not empty so not removed.
dpkg: warning: while removing fglrx-amdcccle, directory '/usr/share/ati' not empty so not removed.
hemmjonny@pro-net-laptop:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libswscale0 libavutil50 libexo-0.3-0 xfce4-panel libexo-common
  libboost-date-time1.42.0 libxfcegui4-4 xfce-keyboard-shortcuts libavcodec52
  gstreamer0.10-ffmpeg libgif4 libgtkglext1 libboost-thread1.42.0
  libglib2.0-bin libpostproc51 libglib2.0-dev zlib1g-dev libavformat52
  exo-utils libva1
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  fglrx-modaliases
0 upgraded, 1 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/3,440kB of archives.
After this operation, 69.6kB of additional disk space will be used.
(Reading database ... 147925 files and directories currently installed.)
Preparing to replace libgl1-mesa-dri 7.9~git20100924-0ubuntu2 (using .../libgl1-mesa-dri_7.9~git20100924-0ubuntu2_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 7.9~git20100924-0ubuntu2 (using .../libgl1-mesa-glx_7.9~git20100924-0ubuntu2_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Selecting previously deselected package fglrx-modaliases.
Unpacking fglrx-modaliases (from .../fglrx-modaliases_2%3a8.780-0ubuntu2_amd64.deb) ...
Setting up libgl1-mesa-dri (7.9~git20100924-0ubuntu2) ...
Setting up libgl1-mesa-glx (7.9~git20100924-0ubuntu2) ...
Setting up fglrx-modaliases (2:8.780-0ubuntu2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
hemmjonny@pro-net-laptop:~$ sudo dpkg-reconfigure xserver-xorg
hemmjonny@pro-net-laptop:~$

---

### Post by Jechem on 2011-04-21
you may want to do this before reinstall. backup your configurations.
[http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-files-and-settings-backup-861702/](http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-files-and-settings-backup-861702/)

---

### Post by Jechem on 2011-04-21
try activating in hardware drivers

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> you may want to do this before reinstall. backup your configurations.
[http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-files-and-settings-backup-861702/](http://www.linuxquestions.org/questions/linux-software-2/ubuntu-10-10-files-and-settings-backup-861702/)


Would that not copy the problem?

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> try activating in hardware drivers


Nope no good still the same Error

---

### Post by Jechem on 2011-04-21
run the following to get compiz working:
sudo apt-get install --reinstall xserver-xorg-core

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> run the following to get compiz working:
sudo apt-get install --reinstall xserver-xorg-core


hemmjonny@pro-net-laptop:~$ sudo apt-get install --reinstall xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 fglrx-amdcccle : Depends: fglrx but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
hemmjonny@pro-net-laptop:~$

---

### Post by Jechem on 2011-04-21
> **hemmjonny said:**
> Nope no good still the same Error

Reinstall is the best option then. Sorry.;)

> Would that not copy the problem?
Just backup your important files.
/home

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> Reinstall is the best option then. Sorry.;)


Just backup your important files.
/home

Thanks for trying mate :) lol thats 1 +  for windows i can always fix that on my own.

Thanks again

Jonathan

---

### Post by Jechem on 2011-04-21
Reinstall will be a better fix based on the roundabout problems encountered. You can configure your settings quickly because you've done that before, you know everything you need done. Don't install the new ATI drivers though. ;)

edit: Good luck with the G/F.

---

### Post by hemmjonny on 2011-04-21
> **Jechem said:**
> Reinstall will be a better fix based on the roundabout problems encountered. You can configure your settings quickly because you've done that before, you know everything you need done. Don't install the new ATI drivers though. ;)
yeah lol i thought they would be better as there more upto date and they said they worked with Linux (need to remember the old rule if its not broken don't fix it)

you would not think that 1 driver could make so much mess.

well there is 1 + i am a little bit more confident with the terminal now lol.

Thanks again

Jonathan

LOL cheers think i will need it

Might have to wait till next weekend got so much to do :(

---

### Post by fungi on 2012-03-17
So i woke up this morning and xorg failing at boot with:

```
(EE) fglrx(0): atiddxDriScreenInit failed, GPS not been initialized.
```

So i tried a new catalyst driver from [http://support.amd.com](http://support.amd.com) but it kept failing with:

```
dpkg-shlibdeps: error: no dependency information found for /usr/share
/ati/lib64/libQtCore.so.4
```

So i purged and un-installed everything i could think or find in the numerous threads that turned up in google but still kept getting the libQtCore.so.4 error.

On a whim i:

```
sudo rm -R /usr/share/ati/
```

And now

```
sudo sh amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/lucid

```

Runs clean and produces working .debs :D

Still i dont know why the thing died in the first place or why it wouldn't build, but hopefully this saves somebody some time.

Lucid 10.04, ATI HD 6670

---

