---
title: "installing blender 2.6 problems"
date: 2012-06-21
forum: General Help
---

### Post by gandalf3 on 2012-06-21
i was following the instructions on this page for installing the latest version of blender using a ppa,

but when i tried ```

sudo apt-get blender
```it asked as usual "this will take up ___ amount of space. continue? [Y/n]"
i pressed "y" then enter, and it said "abort."
it doesn't make any difference if it's capital, and i even tried "n" too...

here's the output from the terminal for the whole attempt.

```

username@ubuntu01:~$ sudo add-apt-repository ppa:cheleb/blender-svn
[sudo] password for username: 
stty: unknown mode: doofus
[sudo] password for username: 
You are about to add the following PPA to your system:
 Blender SVN
 This PPA contains fresh (mostly daily) Blender SVN trunk builds. Please note that these are development builds and may contain bugs.

The current build configuration is:
===================================
WITH_AUDASPACE ON
WITH_BLENDER ON
WITH_BUILDINFO ON
WITH_BUILTIN_GLEW ON
WITH_BULLET ON
WITH_CODEC_FFMPEG ON
WITH_CODEC_SNDFILE ON
WITH_CXX_GUARDEDALLOC OFF
WITH_CYCLES ON
WITH_CYCLES_CUDA_BINARIES OFF
WITH_CYCLES_TEST OFF
WITH_FFTW3 ON
WITH_GAMEENGINE ON
WITH_GHOST_DEBUG OFF
WITH_GHOST_SDL OFF
WITH_HEADLESS OFF
WITH_IK_ITASC ON
WITH_IMAGE_CINEON ON
WITH_IMAGE_DDS ON
WITH_IMAGE_FRAMESERVER ON
WITH_IMAGE_HDR ON
WITH_IMAGE_OPENEXR ON
WITH_IMAGE_OPENJPEG ON
WITH_IMAGE_REDCODE ON
WITH_IMAGE_TIFF ON
WITH_INPUT_NDOF ON
WITH_INSTALL_PORTABLE OFF
WITH_INTERNATIONAL ON
WITH_JACK ON
WITH_LIBMV ON
WITH_LZMA ON
WITH_LZO ON
WITH_MEM_JEMALLOC OFF
WITH_MOD_BOOLEAN ON
WITH_MOD_CLOTH_ELTOPO OFF
WITH_MOD_DECIMATE ON
WITH_MOD_FLUID ON
WITH_MOD_OCEANSIM ON
WITH_MOD_REMESH ON
WITH_MOD_SMOKE ON
WITH_OPENAL ON
WITH_OPENCOLLADA ON
WITH_OPENMP ON
WITH_PLAYER ON
WITH_PYTHON ON
WITH_PYTHON_INSTALL ON
WITH_PYTHON_MODULE OFF
WITH_PYTHON_SAFETY OFF
WITH_PYTHON_SECURITY OFF
WITH_RAYOPTIMIZATION ON
WITH_SDL ON
WITH_X11_XF86VMODE ON
WITH_X11_XINPUT ON
WITH_XDG_USER_DIRS OFF
 More info: https://launchpad.net/~cheleb/+archive/blender-svn
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.TmQzJ3zOPt --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 4D85A105373204F2AFDE7483048A1684108A879C
gpg: requesting key 108A879C from hkp server keyserver.ubuntu.com
gpg: key 108A879C: public key "Launchpad Cheleb's PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
username@ubuntu01:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Ign http://dl.google.com stable InRelease                                      
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Get:2 http://dl.google.com stable Release.gpg [198 B]                          
Get:3 http://dl.google.com stable Release [1,347 B]                            
Ign http://archive.getdeb.net oneiric-getdeb InRelease                         
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Ign http://security.ubuntu.com oneiric-security InRelease                      
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.canonical.com oneiric InRelease                             
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://apt.rigsofrods.com  InRelease                                       
Get:4 http://us.archive.ubuntu.com oneiric Release.gpg [198 B]                 
Ign http://ppa.launchpad.net oneiric InRelease                                 
Get:5 http://security.ubuntu.com oneiric-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Get:6 http://us.archive.ubuntu.com oneiric-updates Release.gpg [198 B]         
Hit http://archive.canonical.com oneiric Release.gpg                           
Ign http://ppa.launchpad.net oneiric InRelease                                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.getdeb.net oneiric-getdeb Release.gpg                       
Get:7 http://dl.google.com stable Release [1,347 B]                            
Hit http://deb.playonlinux.com oneiric InRelease                               
Get:8 http://security.ubuntu.com oneiric-security Release [40.8 kB]            
Get:9 http://us.archive.ubuntu.com oneiric-backports Release.gpg [198 B]       
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://archive.canonical.com oneiric Release                               
Get:10 http://ppa.launchpad.net oneiric Release.gpg [316 B]                    
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Ign http://apt.rigsofrods.com  Release.gpg                                     
Hit http://deb.playonlinux.com oneiric/main i386 Packages                      
Get:11 http://us.archive.ubuntu.com oneiric Release [40.8 kB]                  
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.canonical.com oneiric/partner i386 Packages                 
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://archive.getdeb.net oneiric-getdeb Release                           
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Get:12 http://us.archive.ubuntu.com oneiric-updates Release [40.8 kB]          
Ign http://archive.canonical.com oneiric/partner TranslationIndex              
Hit http://ppa.launchpad.net oneiric Release                                   
Get:13 http://ppa.launchpad.net oneiric Release [9,744 B]                      
Ign http://apt.rigsofrods.com  Release                                         
Get:14 http://us.archive.ubuntu.com oneiric-backports Release [40.8 kB]        
Ign http://deb.playonlinux.com oneiric/main TranslationIndex                   
Get:15 http://dl.google.com stable/main i386 Packages [1,243 B]                
Hit http://ppa.launchpad.net oneiric Release                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Get:16 http://us.archive.ubuntu.com oneiric/main Sources [877 kB]              
Hit http://archive.getdeb.net oneiric-getdeb/games i386 Packages               
Get:17 http://dl.google.com stable/main i386 Packages [769 B]                  
Get:18 http://security.ubuntu.com oneiric-security/main Sources [41.7 kB]      
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:19 http://security.ubuntu.com oneiric-security/restricted Sources [1,959 B]
Get:20 http://security.ubuntu.com oneiric-security/universe Sources [18.6 kB]  
Get:21 http://security.ubuntu.com oneiric-security/multiverse Sources [1,641 B]
Get:22 http://security.ubuntu.com oneiric-security/main i386 Packages [129 kB] 
Ign http://archive.getdeb.net oneiric-getdeb/games TranslationIndex            
Get:23 http://ppa.launchpad.net oneiric/main Sources [854 B]                   
Get:24 http://ppa.launchpad.net oneiric/main i386 Packages [1,337 B]           
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Get:25 http://security.ubuntu.com oneiric-security/restricted i386 Packages [3,939 B]
Get:26 http://security.ubuntu.com oneiric-security/universe i386 Packages [42.7 kB]
Get:27 http://security.ubuntu.com oneiric-security/multiverse i386 Packages [3,380 B]
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex          
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex    
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex      
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com oneiric-security/main Translation-en            
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://archive.canonical.com oneiric/partner Translation-en_US             
Ign http://dl.google.com stable/main Translation-en                            
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en      
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en                       
Ign http://archive.canonical.com oneiric/partner Translation-en                
Hit http://security.ubuntu.com oneiric-security/universe Translation-en        
Ign http://deb.playonlinux.com oneiric/main Translation-en_US                  
Ign http://deb.playonlinux.com oneiric/main Translation-en                     
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:28 http://us.archive.ubuntu.com oneiric/restricted Sources [5,351 B]       
Get:29 http://us.archive.ubuntu.com oneiric/universe Sources [4,677 kB]        
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en_US           
Ign http://archive.getdeb.net oneiric-getdeb/games Translation-en              
Err http://apt.rigsofrods.com  Sources                                         
  404  File not found
Err http://apt.rigsofrods.com  Packages                                        
  404  File not found
Ign http://apt.rigsofrods.com  Translation-en_US                               
Ign http://apt.rigsofrods.com  Translation-en                                  
Get:30 http://us.archive.ubuntu.com oneiric/multiverse Sources [149 kB]        
Get:31 http://us.archive.ubuntu.com oneiric/main i386 Packages [1,226 kB]      
Get:32 http://us.archive.ubuntu.com oneiric/restricted i386 Packages [8,216 B] 
Get:33 http://us.archive.ubuntu.com oneiric/universe i386 Packages [4,468 kB]  
Get:34 http://us.archive.ubuntu.com oneiric/multiverse i386 Packages [119 kB]  
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Get:35 http://us.archive.ubuntu.com oneiric-updates/main Sources [144 kB]      
Get:36 http://us.archive.ubuntu.com oneiric-updates/restricted Sources [3,347 B]
Get:37 http://us.archive.ubuntu.com oneiric-updates/universe Sources [56.0 kB] 
Get:38 http://us.archive.ubuntu.com oneiric-updates/multiverse Sources [3,666 B]
Get:39 http://us.archive.ubuntu.com oneiric-updates/main i386 Packages [359 kB]
Get:40 http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages [6,631 B]
Get:41 http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages [120 kB]
Get:42 http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,371 B]
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Get:43 http://us.archive.ubuntu.com oneiric-backports/main Sources [2,742 B]   
Get:44 http://us.archive.ubuntu.com oneiric-backports/restricted Sources [14 B]
Get:45 http://us.archive.ubuntu.com oneiric-backports/universe Sources [9,019 B]
Get:46 http://us.archive.ubuntu.com oneiric-backports/multiverse Sources [14 B]
Get:47 http://us.archive.ubuntu.com oneiric-backports/main i386 Packages [3,296 B]
Get:48 http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages [14 B]
Get:49 http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages [13.4 kB]
Get:50 http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages [14 B]
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric/main Translation-en                   
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en             
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Fetched 12.7 MB in 50s (249 kB/s)                                              
W: Failed to fetch http://apt.rigsofrods.com/Sources  404  File not found

W: Failed to fetch http://apt.rigsofrods.com/Packages  404  File not found

E: Some index files failed to download. They have been ignored, or old ones used instead.
username@ubuntu01:~$ sudo apt-get install blender
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  simgear2.0.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libspnav0 spacenavd
The following NEW packages will be installed:
  libspnav0 spacenavd
The following packages will be upgraded:
  blender
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0 MB of archives.
After this operation, 63.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
username@ubuntu01:~$ sudo apt-get install blender
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  simgear2.0.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libspnav0 spacenavd
The following NEW packages will be installed:
  libspnav0 spacenavd
The following packages will be upgraded:
  blender
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0 MB of archives.
After this operation, 63.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
username@ubuntu01:~$ sudo apt-get install blender
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  simgear2.0.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libspnav0 spacenavd
The following NEW packages will be installed:
  libspnav0 spacenavd
The following packages will be upgraded:
  blender
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0 MB of archives.
After this operation, 63.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
username@ubuntu01:~$ sudo apt-get install blender
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  simgear2.0.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libspnav0 spacenavd
The following NEW packages will be installed:
  libspnav0 spacenavd
The following packages will be upgraded:
  blender
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0 MB of archives.
After this operation, 63.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
username@ubuntu01:~$ sudo apt-get install blender
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  simgear2.0.0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libspnav0 spacenavd
The following NEW packages will be installed:
  libspnav0 spacenavd
The following packages will be upgraded:
  blender
1 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 39.0 MB of archives.
After this operation, 63.7 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Abort.
username@ubuntu01:~$ 

```
this has only happened this once so far. (i tried installing some other stuff and it worked fine)

---

### Post by gandalf3 on 2012-06-23
well, when i installed some updates later, it updated blender to 2.6.
still no idea why sudo apt-get blender didn't work..
i removed the blender svn repository from  etc/apt/sources.list
so it will not keep updating (took a while to download)
all's well that ends well.. :)

---

### Post by gandalf3 on 2012-06-26
well.. actually maybe not.. 
it seems i would be better off for now with 2.62 instead of 2.63 because the addons haven't caught up yet..
but i don't know how to install an earlier version of a software from a PPA if thats even possible..
is there some way i can tell the software center that i want the previous version of blender?
thanks..

---

### Post by davidvandoren on 2012-06-26
Strange I did not have to install it.
Just download the file untar it into the home folder and open Blender.

---

### Post by gandalf3 on 2012-06-26
hmm when i tried to run the executable in the extracted folder, nothing happened.. do i have to uninstall the other version?

---

### Post by davidvandoren on 2012-06-26
> **gandalf3 said:**
> hmm when i tried to run the executable in the extracted folder, nothing happened.. do i have to uninstall the other version?

I don't know but I do have the older version installed.

Maybe you rightclick the executable and see if it is set to run as a program.

---

### Post by josephmills on 2012-06-26
If you are sure that is what you want to install you could always tell apt that before you run the command like so 
```
sudo apt-get -y install <name of package>
```
That tells apt to answer Yes to all. best to do dry runs. 
what version of Ubuntu are you using as blender is in the repos.

```
~$ apt-cache show blender
Package: blender
Priority: optional
Section: universe/graphics
Installed-Size: 56789
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Multimedia Maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
Architecture: amd64
[COLOR="Red"]Version: 2.63a-1[/COLOR]
Depends: python3.2, fonts-droid, libavcodec53 (>= 4:0.8-1~) | libavcodec-extra-53 (>= 4:0.8-1~), libavdevice53 (>= 4:0.8-1~) | libavdevice-extra-53 (>= 4:0.8-1~), libavformat53 (>= 4:0.8-1~) | libavformat-extra-53 (>= 4:0.8-1~), libavutil51 (>= 4:0.8-1~) | libavutil-extra-51 (>= 4:0.8-1~), libc6 (>= 2.15), libfftw3-3, libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgl1-mesa-glx | libgl1, libglew1.7 (>= 1.7.0), libglu1-mesa | libglu1, libgomp1 (>= 4.2.1), libilmbase6 (>= 1.0.1), libjack-jackd2-0 (>= 1.9.5~dfsg-14) | libjack-0.116, libjpeg8 (>= 8c), libopenal1 (>= 1:1.13), libopenexr6 (>= 1.6.1), libopenjpeg2, libpng12-0 (>= 1.2.13-4), libpython3.2 (>= 3.2~a4), libsdl1.2debian (>= 1.2.10-1), libsndfile1 (>= 1.0.20), libstdc++6 (>= 4.6), libswscale2 (>= 4:0.8-1~) | libswscale-extra-2 (>= 4:0.8-1~), libtiff4, libx11-6, libxi6, zlib1g (>= 1:1.2.3.3.dfsg)
Suggests: yafaray
Filename: pool/universe/b/blender/blender_2.63a-1_amd64.deb
Size: 22149644
MD5sum: 13324adf704ab78903843a6ed77c5d47
SHA1: 5bb95c538bec1d09ec4defb62ef3e75df8bcc8d1
SHA256: d836f2464dd938f9fa2280244a2a07f7bb2546d2eb3a98f8ef5fd29de4d39d1b
Description-en: Very fast and versatile 3D modeller/renderer
 Blender is an integrated 3d suite for modelling, animation, rendering,
 post-production, interactive creation and playback (games). Blender has its
 own particular user interface, which is implemented entirely in OpenGL and
 designed with speed in mind. Python bindings are available for scripting;
 import/export features for popular file formats like 3D Studio and Wavefront
 Obj are implemented as scripts by the community. Stills, animations, models
 for games or other third party engines and interactive content in the form of
 a standalone binary are common products of Blender use.
Homepage: http://blender.org
Description-md5: 90b4f36fda45432800e6a278de5b06b4
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Task: ubuntustudio-video, ubuntustudio-graphics


```


[https://launchpad.net/ubuntu/precise/+source/blender](https://launchpad.net/ubuntu/precise/+source/blender)

---

### Post by gandalf3 on 2012-06-26
im using blender 11.10
the version of blender in the repository is 2.63, and i want to install 2.62. (some addons stopped working)
so i can just do something like ```
 sudo apt-get -y install blender 2.62 
```?
or is there someplace i can download the .deb file and install it with that?

---

### Post by gandalf3 on 2012-08-10
i just upgraded to 12.04, so now everything should work.
Thanks!

---

