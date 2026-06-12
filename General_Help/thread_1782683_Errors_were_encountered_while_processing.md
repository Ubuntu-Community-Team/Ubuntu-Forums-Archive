---
title: "Errors were encountered while processing:"
date: 2011-06-14
forum: General Help
---

### Post by cadogan32 on 2011-06-14
I keep getting this error when trying to install this new update:


Preparing to replace language-pack-gnome-de 1:10.10+20110315 (using .../language-pack-gnome-de_1%3a10.10+20110531_all.deb) ... 
Unpacking replacement language-pack-gnome-de ... 
Replacing files in old package language-pack-gnome-de-base ... 
dpkg: error processing /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb (--unpack): 
 trying to overwrite '/usr/share/locale-langpack/de/LC_MESSAGES/app-install-data.mo', which is also in package language-pack-de 1:10.10+20110531 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Processing triggers for software-center ... 
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display 
  warnings.warn(str(e), _gtk.Warning) 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb 

Its for a german language pack that i don't need but update manager keeps popping up and i don't know how to block it.I usually just install it to get rid of it.any fixes?thanks

---

### Post by ChipOManiac on 2011-06-14
What are you using to install?

---

### Post by wildmanne39 on 2011-06-14
> **cadogan32 said:**
> I keep getting this error when trying to install this new update:


Preparing to replace language-pack-gnome-de 1:10.10+20110315 (using .../language-pack-gnome-de_1%3a10.10+20110531_all.deb) ... 
Unpacking replacement language-pack-gnome-de ... 
Replacing files in old package language-pack-gnome-de-base ... 
dpkg: error processing /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb (--unpack): 
 trying to overwrite '/usr/share/locale-langpack/de/LC_MESSAGES/app-install-data.mo', which is also in package language-pack-de 1:10.10+20110531 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
Processing triggers for software-center ... 
/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py:57: GtkWarning: could not open display 
  warnings.warn(str(e), _gtk.Warning) 
Processing triggers for python-central ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb 

Its for a german language pack that i don't need but update manager keeps popping up and i don't know how to block it.I usually just install it to get rid of it.any fixes?thanks
Hi, try this in a terminal.
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by cadogan32 on 2011-06-14
I tried those 2 commands but got this error:

Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Iam using update manager to try to install it

---

### Post by wildmanne39 on 2011-06-14
> **cadogan32 said:**
> I tried those 2 commands but got this error:

Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Iam using update manager to try to install it
Hi, try this one command at a time.
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -rf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f

---

### Post by cadogan32 on 2011-06-15
I still get the same errors as before :(


Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]          
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/) maverick/main Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg [316B]           
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/) maverick/main Translation-en_US
Get:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,775B]             
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [31.4kB]        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en        
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US       
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]             
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release [9,759B]                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release.gpg [198B]            
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/main Translation-en_US  
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [18.1kB]                  
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-proposed/universe Translation-en_US
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]                   
Get:12 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [15.4kB]            
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [69.2kB]
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources [1,882B]                  
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages [8,635B]            
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [31.4kB]              
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed Release [31.4kB]             
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [147kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]         
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [3,749B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/universe i386 Packages [5,791kB]      
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5,992B]     
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/multiverse i386 Packages [183kB]      
Get:25 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/universe i386 Packages [143kB]
Get:26 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [368kB]    
Get:27 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/multiverse i386 Packages [5,203B]
Get:28 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/universe i386 Packages [14.8kB]
Get:30 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/main i386 Packages [135kB]   
Get:31 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/multiverse i386 Packages [1,124B]
Get:32 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-proposed/restricted i386 Packages [14B]
Fetched 8,560kB in 19s (445kB/s)                                                
                            
Current status: 2 updates [+2], 30694 new [+30680].
cadogan@cadogan:~$ sudo aptitude upgrade
The following packages will be upgraded: 
  language-pack-gnome-de linux-alsa-driver-modules-2.6.35-28-generic 
2 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2,997kB of archives. After unpacking 3,035kB will be used.
Do you want to continue? [Y/n/?] y
(Reading database ... 248960 files and directories currently installed.)
Preparing to replace language-pack-gnome-de 1:10.10+20110315 (using .../language-pack-gnome-de_1%3a10.10+20110531_all.deb) ...
Unpacking replacement language-pack-gnome-de ...
Replacing files in old package language-pack-gnome-de-base ...
dpkg: error processing /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb (--unpack):
 trying to overwrite '/usr/share/locale-langpack/de/LC_MESSAGES/app-install-data.mo', which is also in package language-pack-de 1:10.10+20110531
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace linux-alsa-driver-modules-2.6.35-28-generic 2.6.35-28.201106111600 (using .../linux-alsa-driver-modules-2.6.35-28-generic_2.6.35-28.201106141600_i386.deb) ...
Unpacking replacement linux-alsa-driver-modules-2.6.35-28-generic ...
Processing triggers for software-center ...
Processing triggers for python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-alsa-driver-modules-2.6.35-28-generic (2.6.35-28.201106141600) ...
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
                                         
Current status: 1 update [-1].
cadogan@cadogan:~$ sudo aptitude install -f
The following packages will be REMOVED:  
  chromium-browser-inspector{u} firefox-branding{u} gcj-4.4-base{u} 
  gcj-4.4-jre-lib{u} libblas3gf{u} libboost-filesystem1.42.0{u} 
  libboost-python1.42.0{u} libboost-system1.42.0{u} 
  libboost-thread1.42.0{u} libcommons-beanutils-java{u} 
  libcommons-collections3-java{u} libcommons-compress-java{u} 
  libcommons-digester-java{u} libcommons-logging-java{u} libdb-je-java{u} 
  libdb4.7-java{u} libdb4.7-java-gcj{u} libgcj-bc{u} libgcj-common{u} 
  libgcj10{u} libhsqldb-java{u} libicu4j-java{u} libjaxp1.3-java{u} 
  libjline-java{u} libjtidy-java{u} liblapack3gf{u} liblucene2-java{u} 
  libmikmod2{u} libportmidi0{u} libregexp-java{u} libreoffice-base{u} 
  libreoffice-calc{u} libreoffice-filter-mobiledev{u} 
  libreoffice-java-common{u} libreoffice-report-builder-bin{u} 
  libsdl-mixer1.2{u} libsdl-ttf2.0-0{u} libsmpeg0{u} 
  libtorrent-rasterbar6{u} localechooser-data{u} python-chardet{u} 
  python-libtorrent{u} python-numpy{u} python-pygame{u} ttf-sil-gentium{u} 
  ttf-sil-gentium-basic{u} user-setup{u} 
The following packages will be upgraded:
  language-pack-gnome-de 
1 packages upgraded, 0 newly installed, 47 to remove and 0 not upgraded.
Need to get 0B/852kB of archives. After unpacking 144MB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 248959 files and directories currently installed.)
Removing chromium-browser-inspector ...
Removing firefox-branding ...
Removing libdb4.7-java-gcj ...
Removing libgcj-bc ...
Removing gcj-4.4-jre-lib ...
Removing libgcj10 ...
rmdir: failed to remove `/var/lib/gcj-4.4': No such file or directory
Removing gcj-4.4-base ...
Removing python-pygame ...
Removing python-numpy ...
Removing liblapack3gf ...
Removing libblas3gf ...
Removing python-libtorrent ...
Removing libtorrent-rasterbar6 ...
Removing libboost-filesystem1.42.0 ...
Removing libboost-python1.42.0 ...
Removing libboost-system1.42.0 ...
Removing libboost-thread1.42.0 ...
Removing libcommons-digester-java ...
Removing libcommons-beanutils-java ...
Removing libcommons-collections3-java ...
Removing libcommons-compress-java ...
Removing libcommons-logging-java ...
Removing libdb-je-java ...
Removing libdb4.7-java ...
Removing libgcj-common ...
Removing libreoffice-report-builder-bin ...
Removing libreoffice-base ...
Removing libhsqldb-java ...
Removing libicu4j-java ...
Removing libjtidy-java ...
Removing libjaxp1.3-java ...
Removing libjline-java ...
Removing liblucene2-java ...
Removing libsdl-mixer1.2 ...
Removing libmikmod2 ...
Removing libportmidi0 ...
Removing libregexp-java ...
Removing libreoffice-calc ...
Removing libreoffice-filter-mobiledev ...
Removing libreoffice-java-common ...
Removing libsdl-ttf2.0-0 ...
Removing libsmpeg0 ...
Removing localechooser-data ...
Removing python-chardet ...
Removing ttf-sil-gentium ...
Removing ttf-sil-gentium-basic ...
Removing user-setup ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for python-support ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for menu ...
Processing triggers for fontconfig ...
Processing triggers for python-support ...
(Reading database ... 247269 files and directories currently installed.)
Preparing to replace language-pack-gnome-de 1:10.10+20110315 (using .../language-pack-gnome-de_1%3a10.10+20110531_all.deb) ...
Unpacking replacement language-pack-gnome-de ...
Replacing files in old package language-pack-gnome-de-base ...
dpkg: error processing /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb (--unpack):
 trying to overwrite '/usr/share/locale-langpack/de/LC_MESSAGES/app-install-data.mo', which is also in package language-pack-de 1:10.10+20110531
No apport report written because MaxReports is reached already
                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for software-center ...
Processing triggers for python-central ...
Errors were encountered while processing:
 /var/cache/apt/archives/language-pack-gnome-de_1%3a10.10+20110531_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

is there a way to just block that update instead of installing it?If its gonna be a problem to figure out i can just deal with it being there.thanks for the help.

---

### Post by wildmanne39 on 2011-06-15
Hi, you can go into the file and manually delete it, however I have read that is not recommended,but if you want to move it to a new location in case you need it later you can use the mv command to move it to a new folder and then rename it by adding old to the end of it. You have to change to its directory so see it, then use the ls command to list all the files in that folder.

---

### Post by cadogan32 on 2011-06-15
i deleted all the packages that relate to that language pack but it still shows up in the update manager.i tried to update again and get the same error.I really don't know whats going on but it looks like i might just have to get used to that in the corner.I never had a problem like this before.

---

### Post by wildmanne39 on 2011-06-15
> **cadogan32 said:**
> i deleted all the packages that relate to that language pack but it still shows up in the update manager.i tried to update again and get the same error.I really don't know whats going on but it looks like i might just have to get used to that in the corner.I never had a problem like this beforHi, if you look around the forum there are a lot of updating issues right now but all most all of them can be fixed. Hi, will will try this and see if it works.
```
sudo apt-get update
```

```
sudo apt-get autoclean[CODE]


```sudo apt-get clean[/CODE]

```
sudo apt-get autoremove
```do them one at a time. There are 2 commands in the big box for some reason I could not get it to separate those to command it refused.

---

### Post by cadogan32 on 2011-06-15
I tried that also but it still pops up.i can deal with it being there its just a little annoying having it popup all the time.hopefully there will be a fix soon.thanks anyways for the help.

---

### Post by wildmanne39 on 2011-06-15
> **cadogan32 said:**
> I tried that also but it still pops up.i can deal with it being there its just a little annoying having it popup all the time.hopefully there will be a fix soon.thanks anyways for the help.Hi, your welcome.

---

