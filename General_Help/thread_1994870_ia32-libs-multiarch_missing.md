---
title: "ia32-libs-multiarch missing?"
date: 2012-06-03
forum: General Help
---

### Post by maxwinkler on 2012-06-03
Hi, so after searching for a solution for my predicament for a few days now, I'll put my hopes here. 
To properly run nvflash some 32 bit libraries need to be available (I have ubuntu 12.04 64 bit installed, fresh install + everything updated as of today). At first I attempted to install ia32-libs, but that seems deprecated and replaced by ia32-libs-multiarch. Anyhow, I can't install that package either, nor does it even show up in synaptic. When attempting to install ia32-libs-multiarch I get the unmet dependencies (those seem to be different from post to post that I looked up, mine mostly revolve around libqt4 and gtk2 packages.)

here's the output of my failed attempt to install multiarch:
The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libgettextpo0:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gtk2-engines:i386 but it is not going to be installed
                            Depends: gtk2-engines-murrine:i386 but it is not going to be installed
                            Depends: gtk2-engines-pixbuf:i386 but it is not going to be installed
                            Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libdbus-glib-1-2:i386 but it is not going to be installed
                            Depends: libgail-common:i386 but it is not going to be installed
                            Depends: libgconf-2-4:i386 but it is not going to be installed
                            Depends: libgtk2.0-0:i386 but it is not going to be installed
                            Depends: libpulse-mainloop-glib0:i386 but it is not going to be installed
                            Depends: libqt4-dbus:i386 but it is not going to be installed
                            Depends: libqt4-network:i386 but it is not going to be installed
                            Depends: libqt4-opengl:i386 but it is not going to be installed
                            Depends: libqt4-qt3support:i386 but it is not going to be installed
                            Depends: libqt4-script:i386 but it is not going to be installed
                            Depends: libqt4-scripttools:i386 but it is not going to be installed
                            Depends: libqt4-sql:i386 but it is not going to be installed
                            Depends: libqt4-svg:i386 but it is not going to be installed
                            Depends: libqt4-test:i386 but it is not going to be installed
                            Depends: libqt4-xml:i386 but it is not going to be installed
                            Depends: libqt4-xmlpatterns:i386 but it is not going to be installed
                            Depends: libqtcore4:i386 but it is not going to be installed
                            Depends: libqtgui4:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: librsvg2-common:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

here's the output of the failed attempt to start nvflash:

root@max-ThinkPad-T410:/home/max/Downloads/Android/wheelie# ./nvflash 
-su: ./nvflash: No such file or directory

Attached is the list of all installed packages.

How can I get ia32-libs-multiarch installed or is there a better workaround to get 32 bit SW running?

Thanks
Max

---

### Post by oldos2er on 2012-06-03
Do you have the universe repository enabled? Run ```
sudo apt-get update && sudo apt-get install ia32-libs-multiarch
``` and if there are errors, please copy and paste them here.

---

### Post by maxwinkler on 2012-06-04
Yes, I have all repositories enabled (incl. universe) and the error message is :

max@max-ThinkPad-T410:~$ sudo apt-get install ia32-libs-multiarch
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs-multiarch:i386 : Depends: libgettextpo0:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-base:i386 but it is not going to be installed
                            Depends: gstreamer0.10-plugins-good:i386 but it is not going to be installed
                            Depends: gtk2-engines:i386 but it is not going to be installed
                            Depends: gtk2-engines-murrine:i386 but it is not going to be installed
                            Depends: gtk2-engines-pixbuf:i386 but it is not going to be installed
                            Depends: gtk2-engines-oxygen:i386 but it is not going to be installed
                            Depends: gvfs:i386 but it is not going to be installed
                            Depends: ibus-gtk:i386 but it is not going to be installed
                            Depends: libcanberra-gtk-module:i386 but it is not going to be installed
                            Depends: libdbus-glib-1-2:i386 but it is not going to be installed
                            Depends: libgail-common:i386 but it is not going to be installed
                            Depends: libgconf-2-4:i386 but it is not going to be installed
                            Depends: libgtk2.0-0:i386 but it is not going to be installed
                            Depends: libpulse-mainloop-glib0:i386 but it is not going to be installed
                            Depends: libqt4-dbus:i386 but it is not going to be installed
                            Depends: libqt4-network:i386 but it is not going to be installed
                            Depends: libqt4-opengl:i386 but it is not going to be installed
                            Depends: libqt4-qt3support:i386 but it is not going to be installed
                            Depends: libqt4-script:i386 but it is not going to be installed
                            Depends: libqt4-scripttools:i386 but it is not going to be installed
                            Depends: libqt4-sql:i386 but it is not going to be installed
                            Depends: libqt4-svg:i386 but it is not going to be installed
                            Depends: libqt4-test:i386 but it is not going to be installed
                            Depends: libqt4-xml:i386 but it is not going to be installed
                            Depends: libqt4-xmlpatterns:i386 but it is not going to be installed
                            Depends: libqtcore4:i386 but it is not going to be installed
                            Depends: libqtgui4:i386 but it is not going to be installed
                            Depends: libqtwebkit4:i386 but it is not going to be installed
                            Depends: librsvg2-common:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by oldos2er on 2012-06-04
How about ```
sudo apt-get update
``` ?

---

### Post by maxwinkler on 2012-06-05
apt-get update works fine..
```
max@max-ThinkPad-T410:~$ sudo apt-get update
[sudo] password for max: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner amd64 Packages                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [13.7 kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [4,935 B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [696 B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [43.9 kB]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [11.2 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,142 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [45.2 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [11.2 kB]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main amd64 Packages [1,273 kB]
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted amd64 Packages [8,452 B]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe amd64 Packages [4,786 kB]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse amd64 Packages [119 kB] 
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                  
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [96.4 kB]                                          
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]                                    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [19.6 kB]                                      
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,053 B]                                    
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [228 kB]                                    
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [2,417 B]                             
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [57.0 kB]                               
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,823 B]                             
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [229 kB]                                     
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]                              
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [57.5 kB]                                
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,046 B]                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex                                          
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [700 B]                                          
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]                                     
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [6,109 B]                                    
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]                                  
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [559 B]                                   
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]                              
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [5,200 B]                             
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [996 B]                             
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [559 B]                                    
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]                               
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [5,227 B]                              
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main TranslationIndex                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse TranslationIndex                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted TranslationIndex                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe TranslationIndex                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en                                          
Fetched 19.6 MB in 18s (1,063 kB/s)                                                                                 
Reading package lists... Done
```

---

### Post by oldos2er on 2012-06-05
> E: Unable to correct problems, you have held broken packages.

Have you tried fixing the broken packages? ```
sudo apt-get install -f
```

---

### Post by v6ak on 2012-06-05
It seems that I've exactly the same problem. The apt-get install -f does not solve it.

It seems that *any* amd64 package works, but *any* i386 does not.

maxwinkler, do you use apt-build? I do. I wonder if apt-build affects the problem.

---

### Post by IWantFroyo on 2012-06-05
```
sudo apt-get install ia32-libs
```
 
At least, I think that's what it's called. You may want to double check with an "apt-cache search".
 
It should allow you to use i386 applications.

---

### Post by v6ak on 2012-06-05
Maybe maxwinkler has the same issue, which pointed him to installing ia32-libs-multiarch:

```
$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Depends: ia32-libs-multiarch
E: Unable to correct problems, you have held broken packages.
```

---

### Post by IWantFroyo on 2012-06-05
Oops. Didn't see that he already tried installing ia32-libs.
 
What is the Terminal output if you run oldos2er's suggestion?
```
sudo apt-get install -f
```

---

### Post by v6ak on 2012-06-05
```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
```

There is probably nothing interresting except "7 not upgraded". All of them (i.e.: libobrender27 linux-generic linux-image linux-image-generic openbox-dev xserver-xorg-core xvfb) are comming from apt-build. Neither apt-get upgrade not update-manager say the reason.

---

### Post by IWantFroyo on 2012-06-05
I did some research on apt-build. It appears to compile from source.
 
Maybe you should try removing it?
 
```
sudo apt-get remove apt-build
```

---

### Post by v6ak on 2012-06-05
I've tried to remove it from /etc/apt/sources.d, but with no effect.

---

### Post by maxwinkler on 2012-06-05
I haven't knowingly used apt-build. This is a clean 12.04 install + all updates.

---

### Post by v6ak on 2012-06-05
You probably can't use apt-build accidentaly (e.g. as a dependency). If you had it installed, you would know it.

So I hope this is not caused by apt-build.

---

### Post by v6ak on 2012-06-07
I've heard from my friend that it works, so I've tried it in a clean install (in VirtualBox) and it really works.

But if I don't want to reinstall the system, I don't know how to fix it. Is there a way to save something like world file (yes, I've been using Gentoo) and regenerate everything other from apt/dpkg?

I've tried following command, but without any change:
```
sudo apt-get clean && sudo apt-get update && sudo apt-get install -f && sudo apt-get install ia32-libs
```

---

### Post by john_abq on 2012-06-07
Hi

I'm having the same problems with the i32-libs when I upgraded to 11.04 last night. 

I tried the command

 sudo apt-get update && sudo apt-get install ia32-libs-multiarch

The error messages I got at the end are as follows:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ia32-libs : Recommends: ia32-libs-multiarch but it is not installable
             Breaks: nspluginwrapper (< 1.4.4-0ubuntu2) but 1.2.2-0ubuntu9 is to be installed
E: Broken packages


This not a problem limited to 12.04

---

### Post by v6ak on 2012-06-08
It is very strange. I've tried to install ia32-libs from Synaptic. It wants to remove many (all?) packages and install few extra packages. I was able to install the few extra packages manually, but some new packages appeared.

See [http://public.v6ak.com/ia32-synaptic.png](http://public.v6ak.com/ia32-synaptic.png)

BTW, is there any explanation what does the message exactly mean? I'd like to recognize the problem, but I've only found that I should write some commangs (like apt-get clean, apt-get -f install etc.). Well, these commands are innocent (I can simply RTFM them, they generaly clears an odd state), but when they don't help, they are useless. I'd like to know the problem. I'd like to read an error report like from emerge tool, which is sometimes large, but understandable. Is there any way with APT?

BTW2: Some change:
```
$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 apache2.2-bin : Depends: libapr1 (>= 1.4.2) but it is not going to be installed
                 Depends: libaprutil1 (>= 1.3.2+dfsg) but it is not going to be installed
                 Depends: libaprutil1-dbd-sqlite3 but it is not going to be installed or
                          libaprutil1-dbd-mysql but it is not going to be installed or
                          libaprutil1-dbd-odbc but it is not going to be installed or
                          libaprutil1-dbd-pgsql but it is not going to be installed or
                          libaprutil1-dbd-freetds but it is not going to be installed
                 Depends: libaprutil1-ldap but it is not going to be installed
                 Depends: libcap2 (>= 2.10) but it is not going to be installed
                 Depends: libldap-2.4-2 (>= 2.4.7) but it is not going to be installed
 apache2.2-common : Depends: apache2-utils but it is not going to be installed
                    Depends: procps
                    Depends: perl but it is not going to be installed
 ia32-libs : Depends: ia32-libs-multiarch
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

---

### Post by v6ak on 2012-06-13
john_abq: Try dist-upgrade.

I'v figured out that the problem was definitely caused by using apt-build.
* When apt-build compiles something, it adds some suffix to version.
* APT uses the aptbuild's version as a newer version.
* Some libraries have some dependencies with exact version. In this case, the dependency is broken.
* It seems that i386 libraries usually somehow depend on amd64 variants or binaries.
* I had of course recompiled libraries such as libstdc++6 etc.
* APT was able to neither reinstall nor download these packages (and replace with clean versions), since they were 'newer'.

I've downloaded the packages from mirrors and installed via dpkg -i:

```
name=xaw3dg; arch=amd64; wget "http://packages.ubuntu.com/precise/$arch/$name/download" -O - | grep -o 'http://mirror.anl.gov/.*\.deb' | xargs wget
```

There is the list:
```
apache2-utils_2.2.22-1ubuntu1_amd64.deb # probably extra package
bzip2_1.0.6-1_amd64.deb
cpp-4.6_4.6.3-1ubuntu5_amd64.deb
g++-4.6_4.6.3-1ubuntu5_amd64.deb
gcc-4.6_4.6.3-1ubuntu5_amd64.deb
gcc-4.6-base_4.6.3-1ubuntu5_amd64.deb
libaprutil1-ldap_1.3.12+dfsg-3_amd64.deb # probably extra package
libarchive12_3.0.3-6ubuntu1_amd64.deb
libasound2_1.0.25-1ubuntu10_amd64.deb
libasound2-dev_1.0.25-1ubuntu10_amd64.deb
libbz2-1.0_1.0.6-1_amd64.deb
libbz2-dev_1.0.6-1_amd64.deb
libc6_2.15-0ubuntu10_amd64.deb
libc6-dev_2.15-0ubuntu10_amd64.deb
libc-bin_2.15-0ubuntu10_amd64.deb
libc-dev-bin_2.15-0ubuntu10_amd64.deb
libdbus-1-3_1.4.18-1ubuntu1_amd64.deb
libgcc1_4.6.3-1ubuntu5_amd64.deb
libgomp1_4.6.3-1ubuntu5_amd64.deb
libquadmath0_4.6.3-1ubuntu5_amd64.deb
libstdc++6_4.6.3-1ubuntu5_amd64.deb
libstdc++6-4.6-dev_4.6.3-1ubuntu5_amd64.deb
xaw3dg_1.5+E-18.1ubuntu1_amd64.deb
zlib1g_1.2.3.4.dfsg-3ubuntu4_amd64.deb
zlib1g-dev_1.2.3.4.dfsg-3ubuntu4_amd64.deb
```

---

### Post by baijea on 2012-09-18
Hi,

the solution to a similar problem I had is listed in [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7).

Hope this helps!

---

### Post by Lucky Dragon on 2013-01-20
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install ia32-libs
```Will allow you to install the i386 package :D

---

### Post by MiD-AwE on 2013-02-10
> **Lucky Dragon said:**
> ```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install ia32-libs
```Will allow you to install the i386 package :D

I have the same problem with identical error output as listed above. I need the ia32-libs for install of BricsCAD on Ubuntu 12.04 64bit. :(

I tried the information (quoted here) and still no luck. Is there anything else that I can do besides new clean install. (Additional information: I am running the CUDA drivers on NVIDIA GTX 560 ti to get full acceleration of Blender 2.65. I Was told to blacklist several pacages in order to install the CUDA drivers. I would check that blacklist, but I do not remember how to look it up.)

Thank you for any help.

---

