---
title: "Ubuntu 11.04 update manager got stuck"
date: 2011-06-24
forum: General Help
---

### Post by orasisd on 2011-06-24
Hi, I went to update manager about 4 days ago to check for updates, it downloaded all the new updates and while installing them, I remember I was doing something else at the same time and I am not sure if that is the problem that caused this, but the update manager since then gets stuck at applying changes almost in the middle right here with the cursor blinking:

```
Get:1 Changelog for ark (http://changelogs.ubuntu.com/changelogs/pool/main/k/kdeutils/kdeutils_4.6.2-0ubuntu1.1/changelog) [85.5 kB]
kdeutils (4:4.6.2-0ubuntu1.1) natty-proposed; urgency=low

  * Move kerfuffle_libarchive_readonly.desktop from the filelight package
    to ark. The file is needed to detect various archive types, e.g. deb
    packages. (LP: #797067)

 -- Felix Geyer <debfx-pkg@fobos.de>  Thu, 16 Jun 2011 11:24:37 +0200

Get:1 Changelog for language-pack-el (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-el/language-pack-el_11.04+20110607/changelog) [192 B]

Get:1 Changelog for language-pack-el-base (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-el-base/language-pack-el-base_11.04+20110607/changelog) [197 B]

Get:1 Changelog for language-pack-en (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-en/language-pack-en_11.04+20110607/changelog) [192 B]

Get:1 Changelog for language-pack-en-base (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-en-base/language-pack-en-base_11.04+20110607/changelog) [197 B]

Get:1 Changelog for language-pack-gnome-el (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-gnome-el/language-pack-gnome-el_11.04+20110607/changelog) [198 B]

Get:1 Changelog for language-pack-gnome-el-base (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-gnome-el-base/language-pack-gnome-el-base_11.04+20110607/changelog) [203 B]

Get:1 Changelog for language-pack-gnome-en (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_11.04+20110607/changelog) [198 B]

Get:1 Changelog for language-pack-gnome-en-base (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_11.04+20110607/changelog) [203 B]

Get:1 Changelog for language-pack-kde-el (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-kde-el/language-pack-kde-el_11.04+20110607/changelog) [196 B]

Get:1 Changelog for language-pack-kde-el-base (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-kde-el-base/language-pack-kde-el-base_11.04+20110607/changelog) [201 B]

Get:1 Changelog for language-pack-kde-en (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-kde-en/language-pack-kde-en_11.04+20110607/changelog) [196 B]

Get:1 Changelog for language-pack-kde-en-base (http://changelogs.ubuntu.com/changelogs/pool/main/l/language-pack-kde-en-base/language-pack-kde-en-base_11.04+20110607/changelog) [201 B]

Get:1 Changelog for xul-ext-ubufox (http://changelogs.ubuntu.com/changelogs/pool/main/u/ubufox/ubufox_0.9.1-0ubuntu0.11.04.1/changelog) [27.4 kB]
ubufox (0.9.1-0ubuntu0.11.04.1) natty-security; urgency=low

  * New upstream release v0.9.1
    - Bump maxVersion to 6.0.* (it's compatible with what is in
      mozilla-aurora already)
    - Fix a typo in the "spellchecker.dictionary" default prefs
/tmp/tmp9XzfvJ 

```I have no idea how to continue 
any help on this greatly appreciated !
thank you guys

---

### Post by orasisd on 2011-07-04
hello, thanks for the help so far, it is still in that state.
shall I re-install ubuntu every time I face something like that ?
what would you do

---

### Post by orasisd on 2011-07-07
no one
thank you

---

### Post by Zill on 2011-07-07
> **orasisd said:**
> Hi, I went to update manager about 4 days ago to check for updates, it downloaded all the new updates and while installing them, I remember I was doing something else at the same time and I am not sure if that is the problem that caused this, but the update manager since then gets stuck at applying changes almost in the middle right here with the cursor blinking:

```
Get:1 Changelog for ark (http://changelogs.ubuntu.com/changelogs/pool/main/k/kdeutils/kdeutils_4.6.2-0ubuntu1.1/changelog) [85.5 kB]
kdeutils (4:4.6.2-0ubuntu1.1) [COLOR="Red"]natty-proposed[/COLOR]; urgency=low

  * Move kerfuffle_libarchive_readonly.desktop from the filelight package
    to ark. The file is needed to detect various archive types, e.g. deb
    packages. (LP: #797067)

 -- Felix Geyer <debfx-pkg@fobos.de>  Thu, 16 Jun 2011 11:24:37 +0200...
```
It looks like you have enabled the "proposed updates" repository as this is not enabled by default.  As detailed in the [Ubuntu Updates]("https://help.ubuntu.com/community/UbuntuUpdates") documentation, this is not recommended for inexperienced users as it *can* break your system.

I suggest you post your /etc/apt/sources.list file so that we can see *exactly* which repositories are listed.
```
cat /etc/apt/sources.list
```

---

### Post by orasisd on 2011-07-07
hi zill, thanks for the answer finally ! thanks

here is my /etc/apt/sources.list

```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu natty main restricted
deb-src http://archive.ubuntu.com/ubuntu natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu natty-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
deb http://archive.ubuntu.com/ubuntu natty-updates universe
deb-src http://archive.ubuntu.com/ubuntu natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu natty multiverse
deb-src http://archive.ubuntu.com/ubuntu natty multiverse
deb http://archive.ubuntu.com/ubuntu natty-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu natty-security main restricted
deb-src http://archive.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.ubuntu.com/ubuntu natty-security universe
deb-src http://archive.ubuntu.com/ubuntu natty-security universe
deb http://archive.ubuntu.com/ubuntu natty-security multiverse
deb-src http://archive.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

```

any help appreciated
thank you

---

### Post by Zill on 2011-07-07
Thanks orasisd.  Your sources.list looks fine to me - no mention of "proposed" so I'm not quite sure where that has come from. :confused:
Let's try to break this down by starting at the beginning.  Please post the outputs from the following three commands:
```
uname -a
```
```
cat /etc/issue
```
```
sudo apt-get update
```

---

### Post by orasisd on 2011-07-07
I deeply appreciate your help here zill,

note that I am running an ispconfig3 on this machine so I edited/changed the domain info in the next result. so:


uname -a
```
Linux myhostname.mydomain.net 2.6.38-8-generic-pae #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011 i686 i686 i386 GNU/Linux
```
cat /etc/issue
```

Ubuntu 11.04 \n \l
```
sudo apt-get update

```
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease                                                        
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                                                 
Ign http://archive.ubuntu.com natty InRelease                                
Ign http://archive.ubuntu.com natty-updates InRelease                        
Ign http://archive.ubuntu.com natty-security InRelease                       
Hit http://archive.canonical.com natty Release.gpg                           
Hit http://extras.ubuntu.com natty Release                                   
Hit http://archive.ubuntu.com natty Release.gpg                                                     
Get:2 http://archive.ubuntu.com natty-updates Release.gpg [198 B]                                   
Hit http://archive.canonical.com natty Release                                                                 
Get:3 http://archive.ubuntu.com natty-security Release.gpg [198 B]                                  
Hit http://extras.ubuntu.com natty/main Sources                                                                    
Hit http://archive.canonical.com natty/partner Sources                                                             
Hit http://archive.ubuntu.com natty Release                                                  
Hit http://extras.ubuntu.com natty/main i386 Packages                                                             
Ign http://extras.ubuntu.com natty/main TranslationIndex                                                          
Hit http://archive.canonical.com natty/partner i386 Packages                                
Ign http://archive.canonical.com natty/partner TranslationIndex                            
Get:4 http://archive.ubuntu.com natty-updates Release [27.2 kB]      
Get:5 http://archive.ubuntu.com natty-security Release [27.2 kB]                                   
Hit http://archive.ubuntu.com natty/main Sources                                                                    
Hit http://archive.ubuntu.com natty/restricted Sources                                     
Hit http://archive.ubuntu.com natty/universe Sources                 
Hit http://archive.ubuntu.com natty/multiverse Sources               
Hit http://archive.ubuntu.com natty/main i386 Packages               
Hit http://archive.ubuntu.com natty/restricted i386 Packages         
Hit http://archive.ubuntu.com natty/universe i386 Packages           
Hit http://archive.ubuntu.com natty/multiverse i386 Packages                               
Ign http://archive.ubuntu.com natty/main TranslationIndex                                  
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty/universe TranslationIndex        
Get:6 http://archive.ubuntu.com natty-updates/main Sources [90.9 kB]                       
Get:7 http://archive.ubuntu.com natty-updates/restricted Sources [14 B]                             
Get:8 http://archive.ubuntu.com natty-updates/universe Sources [17.0 kB]
Get:9 http://archive.ubuntu.com natty-updates/multiverse Sources [1,893 B]                                                 
Get:10 http://archive.ubuntu.com natty-updates/main i386 Packages [266 kB]                                                 
Ign http://extras.ubuntu.com natty/main Translation-en_US                                                                   
Ign http://archive.canonical.com natty/partner Translation-en_US                                      
Get:11 http://archive.ubuntu.com natty-updates/restricted i386 Packages [14 B] 
Get:12 http://archive.ubuntu.com natty-updates/universe i386 Packages [67.4 kB]            
Ign http://extras.ubuntu.com natty/main Translation-en                                                                      
Ign http://archive.canonical.com natty/partner Translation-en                                                               
Get:13 http://archive.ubuntu.com natty-updates/multiverse i386 Packages [4,267 B]                       
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex             
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Get:14 http://archive.ubuntu.com natty-security/main Sources [57.0 kB]
Get:15 http://archive.ubuntu.com natty-security/restricted Sources [14 B]         
Get:16 http://archive.ubuntu.com natty-security/universe Sources [6,105 B]
Get:17 http://archive.ubuntu.com natty-security/multiverse Sources [658 B]   
Get:18 http://archive.ubuntu.com natty-security/main i386 Packages [146 kB]
Get:19 http://archive.ubuntu.com natty-security/restricted i386 Packages [14 B]  
Ign http://dl.google.com stable InRelease                              
Get:20 http://archive.ubuntu.com natty-security/universe i386 Packages [20.8 kB]
Get:21 http://archive.ubuntu.com natty-security/multiverse i386 Packages [2,074 B]
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://archive.ubuntu.com natty/main Translation-en_US             
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Get:22 http://dl.google.com stable Release.gpg [198 B]                                                                                                                                                                
Get:23 http://dl.google.com stable Release [1,338 B]                                                                                                                                                                  
Get:24 http://dl.google.com stable/main i386 Packages [464 B]                                                                                                                                                         
Ign http://dl.google.com stable/main TranslationIndex                                                                                                                                                                 
Ign http://dl.google.com stable/main Translation-en_US                                                                                                                                                                
Ign http://dl.google.com stable/main Translation-en
Fetched 737 kB in 23s (30.8 kB/s)
Reading package lists... Done
```
thanks again

---

### Post by Zill on 2011-07-07
> **orasisd said:**
> ...
```
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease                                                        
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                                                 
Ign http://archive.ubuntu.com natty InRelease                                
...
Ign http://dl.google.com stable/main Translation-en
Fetched 737 kB in 23s (30.8 kB/s)
Reading package lists... Done
```
Looks OK to me - no errors there apparently.  Caveat:  I do not use a pae kernel or Natty so cannot directly compare my results with yours. :|

Please post the output from the following command:
```
sudo apt-get upgrade
```

---

### Post by orasisd on 2011-07-07
hi zill again,

so:

sudo apt-get upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apt apt-transport-https apt-utils banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore bind9 bind9-host bind9utils chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg compiz
  compiz-core compiz-gnome compiz-plugins cups cups-bsd cups-client cups-common cups-ppdc dnsutils evince evince-common flashplugin-installer initramfs-tools initramfs-tools-bin libbind9-60 libcups2 libcupscgi1
  libcupsdriver1 libcupsimage2 libcupsmime1 libcupsppdc1 libdecoration0 libdns69 libevdocument3 libevview3 libgpod-common libgpod4 libisc62 libisccc60 libisccfg62 liblwres60 libvlc5 libvlccore4 unity unity-common
  vlc vlc-data vlc-nox vlc-plugin-notify vlc-plugin-pulse x11-common xorg xserver-xorg xserver-xorg-input-all xserver-xorg-video-all
58 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 30.2 MB/44.2 MB of archives.
After this operation, 520 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ natty-updates/universe chromium-browser-l10n all 12.0.742.112~r90304-0ubuntu0.11.04.1 [1,881 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ natty-updates/universe chromium-codecs-ffmpeg i386 12.0.742.112~r90304-0ubuntu0.11.04.1 [268 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ natty-updates/main libcups2 i386 1.4.6-5ubuntu1.3 [158 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ natty-updates/universe chromium-browser i386 12.0.742.112~r90304-0ubuntu0.11.04.1 [16.5 MB]
Get:5 http://archive.ubuntu.com/ubuntu/ natty-updates/main apt i386 0.8.13.2ubuntu4 [2,102 kB]                                                                                                                        
Get:6 http://archive.ubuntu.com/ubuntu/ natty-updates/main apt-utils i386 0.8.13.2ubuntu4 [223 kB]                                                                                                                    
Get:7 http://archive.ubuntu.com/ubuntu/ natty-updates/main initramfs-tools all 0.98.8ubuntu3.1 [52.8 kB]                                                                                                              
Get:8 http://archive.ubuntu.com/ubuntu/ natty-updates/main initramfs-tools-bin i386 0.98.8ubuntu3.1 [11.0 kB]                                                                                                         
Get:9 http://archive.ubuntu.com/ubuntu/ natty-updates/main apt-transport-https i386 0.8.13.2ubuntu4 [19.1 kB]                                                                                                         
Get:10 http://archive.ubuntu.com/ubuntu/ natty-updates/main bind9 i386 1:9.7.3.dfsg-1ubuntu2.2 [315 kB]                                                                                                               
Get:11 http://archive.ubuntu.com/ubuntu/ natty-updates/main bind9-host i386 1:9.7.3.dfsg-1ubuntu2.2 [52.9 kB]                                                                                                         
Get:12 http://archive.ubuntu.com/ubuntu/ natty-updates/main dnsutils i386 1:9.7.3.dfsg-1ubuntu2.2 [137 kB]                                                                                                            
Get:13 http://archive.ubuntu.com/ubuntu/ natty-updates/main libisc62 i386 1:9.7.3.dfsg-1ubuntu2.2 [143 kB]                                                                                                            
Get:14 http://archive.ubuntu.com/ubuntu/ natty-updates/main libisccc60 i386 1:9.7.3.dfsg-1ubuntu2.2 [17.4 kB]                                                                                                         
Get:15 http://archive.ubuntu.com/ubuntu/ natty-updates/main libisccfg62 i386 1:9.7.3.dfsg-1ubuntu2.2 [36.4 kB]                                                                                                        
Get:16 http://archive.ubuntu.com/ubuntu/ natty-updates/main liblwres60 i386 1:9.7.3.dfsg-1ubuntu2.2 [35.6 kB]                                                                                                         
Get:17 http://archive.ubuntu.com/ubuntu/ natty-updates/main libdns69 i386 1:9.7.3.dfsg-1ubuntu2.2 [634 kB]                                                                                                            
Get:18 http://archive.ubuntu.com/ubuntu/ natty-updates/main bind9utils i386 1:9.7.3.dfsg-1ubuntu2.2 [101 kB]                                                                                                          
Get:19 http://archive.ubuntu.com/ubuntu/ natty-updates/main libbind9-60 i386 1:9.7.3.dfsg-1ubuntu2.2 [24.8 kB]                                                                                                        
Get:20 http://archive.ubuntu.com/ubuntu/ natty-updates/main libgpod4 i386 0.8.0-2ubuntu0.1 [217 kB]                                                                                                                   
Get:21 http://archive.ubuntu.com/ubuntu/ natty-updates/main banshee i386 2.0.0-2ubuntu2 [1,842 kB]                                                                                                                    
Get:22 http://archive.ubuntu.com/ubuntu/ natty-updates/main banshee-extension-soundmenu i386 2.0.0-2ubuntu2 [23.8 kB]                                                                                                 
Get:23 http://archive.ubuntu.com/ubuntu/ natty-updates/main banshee-extension-ubuntuonemusicstore i386 2.0.0-2ubuntu2 [20.5 kB]                                                                                       
Get:24 http://archive.ubuntu.com/ubuntu/ natty-updates/main compiz-gnome i386 1:0.9.4+bzr20110606-0ubuntu1~natty2 [121 kB]                                                                                            
Get:25 http://archive.ubuntu.com/ubuntu/ natty-updates/main compiz-plugins i386 1:0.9.4+bzr20110606-0ubuntu1~natty2 [1,364 kB]                                                                                        
Get:26 http://archive.ubuntu.com/ubuntu/ natty-updates/main libdecoration0 i386 1:0.9.4+bzr20110606-0ubuntu1~natty2 [26.3 kB]                                                                                         
Get:27 http://archive.ubuntu.com/ubuntu/ natty-updates/main compiz-core i386 1:0.9.4+bzr20110606-0ubuntu1~natty2 [268 kB]                                                                                             
Get:28 http://archive.ubuntu.com/ubuntu/ natty-updates/main compiz all 1:0.9.4+bzr20110606-0ubuntu1~natty2 [5,492 B]                                                                                                  
Get:29 http://archive.ubuntu.com/ubuntu/ natty-updates/main libcupscgi1 i386 1.4.6-5ubuntu1.3 [35.6 kB]                                                                                                               
Get:30 http://archive.ubuntu.com/ubuntu/ natty-updates/main libcupsdriver1 i386 1.4.6-5ubuntu1.3 [24.7 kB]                                                                                                            
Get:31 http://archive.ubuntu.com/ubuntu/ natty-updates/main libcupsimage2 i386 1.4.6-5ubuntu1.3 [54.7 kB]                                                                                                             
Get:32 http://archive.ubuntu.com/ubuntu/ natty-updates/main libcupsmime1 i386 1.4.6-5ubuntu1.3 [18.6 kB]                                                                                                              
Get:33 http://archive.ubuntu.com/ubuntu/ natty-updates/main libcupsppdc1 i386 1.4.6-5ubuntu1.3 [60.8 kB]                                                                                                              
Get:34 http://archive.ubuntu.com/ubuntu/ natty-updates/main cups-common all 1.4.6-5ubuntu1.3 [1,275 kB]                                                                                                               
Get:35 http://archive.ubuntu.com/ubuntu/ natty-updates/main cups-bsd i386 1.4.6-5ubuntu1.3 [44.5 kB]                                                                                                                  
Get:36 http://archive.ubuntu.com/ubuntu/ natty-updates/main cups-client i386 1.4.6-5ubuntu1.3 [126 kB]                                                                                                                
Get:37 http://archive.ubuntu.com/ubuntu/ natty-updates/main cups-ppdc i386 1.4.6-5ubuntu1.3 [34.4 kB]                                                                                                                 
Get:38 http://archive.ubuntu.com/ubuntu/ natty-updates/main cups i386 1.4.6-5ubuntu1.3 [1,963 kB]                                                                                                                     
Get:39 http://archive.ubuntu.com/ubuntu/ natty-updates/main libgpod-common i386 0.8.0-2ubuntu0.1 [27.4 kB]                                                                                                            
Fetched 30.2 MB in 29s (1,043 kB/s)                                                                                                                                                                                   
Reading changelogs... Done







Get:1 Changelog for apt (http://changelogs.ubuntu.com/changelogs/pool/main/a/apt/apt_0.8.13.2ubuntu4/changelog) [291 kB]
apt (0.8.13.2ubuntu4) natty-proposed; urgency=low

  [ Julian Andres Klode ]
  * apt-pkg/acquire-item.cc:
    - Reject files known to be invalid (LP: #346386) (Closes: #627642)

  [ Michael Vogt ]
  * apt-pkg/acquire-item.cc:
    - do not reject empty Packages files when checking them for
      correctness

 -- Brian Murray <brian@ubuntu.com>  Fri, 10 Jun 2011 12:05:03 -0700

Get:1 Changelog for banshee (http://changelogs.ubuntu.com/changelogs/pool/main/b/banshee/banshee_2.0.0-2ubuntu2/changelog) [94.9 kB]
banshee (2.0.0-2ubuntu2) natty-proposed; urgency=low

  * Rebuild against new libgpod (LP: #772089)

 -- Chow Loong Jin <hyperair@ubuntu.com>  Mon, 27 Jun 2011 19:07:05 +0800

Get:1 Changelog for libisc62 (http://changelogs.ubuntu.com/changelogs/pool/main/b/bind9/bind9_9.7.3.dfsg-1ubuntu2.2/changelog) [48.9 kB]
bind9 (1:9.7.3.dfsg-1ubuntu2.2) natty-security; urgency=low

  * SECURITY UPDATE: denial of service via specially crafted packet
    - lib/dns/include/dns/rdataset.h, lib/dns/{masterdump,message,ncache,
      nsec3,rbtdb,rdataset,resolver,validator}.c: Use an rdataset attribute
      flag to indicate negative-cache records rather than using rrtype 0.
    - Patch backported from 9.7.3-P3.
    - CVE-2011-2464

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Tue, 05 Jul 2011 08:33:30 -0400

Get:1 Changelog for chromium-codecs-ffmpeg (http://changelogs.ubuntu.com/changelogs/pool/universe/c/chromium-browser/chromium-browser_12.0.742.112~r90304-0ubuntu0.11.04.1/changelog) [57.2 kB]
chromium-browser (12.0.742.112~r90304-0ubuntu0.11.04.1) natty-security; urgency=low

  [ Fabien Tassin <fta@ubuntu.com> ]
  * New Minor upstream release from the Stable Channel (LP: #803107)
    This release fixes the following security issues:
    + WebKit issues:
      - [84355] High, CVE-2011-2346: Use-after-free in SVG font handling.
        Credit to miaubiz.
      - [85003] High, CVE-2011-2347: Memory corruption in CSS parsing. Credit
        to miaubiz.
      - [85102] High, CVE-2011-2350: Lifetime and re-entrancy issues in the
        HTML parser. Credit to miaubiz.
      - [85211] High, CVE-2011-2351: Use-after-free with SVG use element.
        Credit to miaubiz.
      - [85418] High, CVE-2011-2349: Use-after-free in text selection. Credit
        to miaubiz.
    + Chromium issues:
      - [77493] Medium, CVE-2011-2345: Out-of-bounds read in NPAPI string
        handling. Credit to Philippe Arteau.
      - [85177] High, CVE-2011-2348: Bad bounds check in v8. Credit to Aki
        Helin of OUSPG.

 -- Micah Gersten <micahg@ubuntu.com>  Thu, 30 Jun 2011 12:52:08 +0100

Get:1 Changelog for libdecoration0 (http://changelogs.ubuntu.com/changelogs/pool/main/c/compiz/compiz_0.9.4+bzr20110606-0ubuntu1~natty2/changelog) [62.3 kB]
compiz (1:0.9.4+bzr20110606-0ubuntu1~natty2) natty-proposed; urgency=low

  * debian/patches/00_bzr_fix_727143.patch:
    - Fix unity-window-decorator crashes with SIGSEGV when closing Java
      windows (LP: #727143)

 -- Didier Roche <didrocks@ubuntu.com>  Fri, 24 Jun 2011 10:52:47 +0200

Get:1 Changelog for libcups2 (http://changelogs.ubuntu.com/changelogs/pool/main/c/cups/cups_1.4.6-5ubuntu1.3/changelog) [208 kB]
cups (1.4.6-5ubuntu1.3) natty-proposed; urgency=low

  * debian/patches/cups-avahi.dpatch: Updated Avahi patch to fix places in
    the CUPS source code where libdns_sd is supported but not Avahi.
    especially accept being called with a hostname with ".local" domain
    so that AirPrint works without "ServerAlias *" in cupsd.conf (LP: #801306).

 -- Till Kamppeter <till.kamppeter@gmail.com>  Fri, 24 Jun 2011 13:30:59 +0200

Get:1 Changelog for libevdocument3 (http://changelogs.ubuntu.com/changelogs/pool/main/e/evince/evince_2.32.0-0ubuntu12.2/changelog) [35.8 kB]
evince (2.32.0-0ubuntu12.2) natty-proposed; urgency=low

  * debian/patches/0001-libview-Make-sure-we-have-a-valid-page-range*:
    - Backport patch from upstream commit, fixing segfault in
      clear_job_selection(). (LP: #651931)

 -- Chow Loong Jin <hyperair@ubuntu.com>  Sun, 08 May 2011 19:18:04 +0800

Get:1 Changelog for flashplugin-installer (http://changelogs.ubuntu.com/changelogs/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.3.181.34ubuntu0.11.04.1/changelog) [45.4 kB]
flashplugin-nonfree (10.3.181.34ubuntu0.11.04.1) natty-security; urgency=low

  * New upstream release 10.3.181.34 (LP: #803761)
    - debian/config, debian/postinst: Updated sha256sums and path.

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Thu, 30 Jun 2011 15:11:20 +0100

Get:1 Changelog for initramfs-tools-bin (http://changelogs.ubuntu.com/changelogs/pool/main/i/initramfs-tools/initramfs-tools_0.98.8ubuntu3.1/changelog) [210 kB]
initramfs-tools (0.98.8ubuntu3.1) natty-proposed; urgency=low

  * Rename xhci to xhci-hcd to fix booting from USB 3.0 devices
    (cherry-picked fix from Debian bug #625224). (LP: #565047)

 -- Evan Broder <evan@ebroder.net>  Wed, 08 Jun 2011 09:46:20 -0700

Get:1 Changelog for libgpod4 (http://changelogs.ubuntu.com/changelogs/pool/main/libg/libgpod/libgpod_0.8.0-2ubuntu0.1/changelog) [19.0 kB]
libgpod (0.8.0-2ubuntu0.1) natty-proposed; urgency=low

  * [d3ab740] Add autoreconf during build (LP: #772089)

 -- Chow Loong Jin <hyperair@ubuntu.com>  Thu, 28 Apr 2011 08:04:53 +0800

Get:1 Changelog for unity-common (http://changelogs.ubuntu.com/changelogs/pool/main/u/unity/unity_3.8.16-0ubuntu1~natty1/changelog) [95.8 kB]
unity (3.8.16-0ubuntu1~natty1) natty-proposed; urgency=low

  * New upstream version:
    - Unable to load icon text-x-preview at size 48 in a loop (lp: #794556)
    - Display garbled upon restoring original resolution (lp: #795454)
    - Display garbled upon connecting external displays (lp: #795458)
    - Panel disappears after resolution change (lp: #795459)
    - Dragging the launcher with right mouse button is 
      confusing as menu pops up (lp: #735031)
    - In a double monitor setup the Unity top panel in the second screen is 
      cut at the right (lp: #750481)
    - Menu key should open quicklist for the selected item in the launcher 
      (lp: #750778)
    - unity is spamming ~/.xsession-errors when windows are closed 
      (lp: #767642)
    - Dash button ignores transparency when clicked. (lp: #767733)
  * Revert commit for bug #769335, to fix a launcher autohidding issue

 -- Sebastien Bacher <seb128@ubuntu.com>  Fri, 17 Jun 2011 12:22:35 +0200

Get:1 Changelog for vlc-data (http://changelogs.ubuntu.com/changelogs/pool/universe/v/vlc/vlc_1.1.9-1ubuntu1.2/changelog) [112 kB]
vlc (1.1.9-1ubuntu1.2) natty-proposed; urgency=low

  * Backport PulseAudio output plugin rewrite to fix memory leak. (LP: #743323)
  * ASX: fix NULL derefence (LP: #785979)
  * Qt: undo the FSC/KDE workaround (LP: #774581)
  * Add Firefox 4 compatibility (LP: #722690)

 -- Benjamin Drung <bdrung@ubuntu.com>  Tue, 14 Jun 2011 03:04:10 +0200

Get:1 Changelog for x11-common (http://changelogs.ubuntu.com/changelogs/pool/main/x/xorg/xorg_7.6+4ubuntu3.1/changelog) [200 kB]
xorg (1:7.6+4ubuntu3.1) natty-proposed; urgency=low

  * apport/source_xorg.py:
    - Simplify answers for bug reporters filing post-release reports.
      (LP: #778758)
    - Remove attach_drm_info().  This is useful info but we use it very
      infrequently, and it is already available in other log files.  But the
      call makes bug reports a bit cluttered since it adds a lot of lines to
      the report itself.

 -- Bryce Harrington <bryce@ubuntu.com>  Thu, 07 Apr 2011 14:02:40 -0700

(END)

```actually the screen in terminal does not stop at the ---> (END) point, but at some point similar to my first post here with the cursor blinking like: /tmp/tmp9XzfvJ

if you wait for like 15 minutes it does nothing, there's been times that I left it for hours like that and nothing happened. if you ctrl+c it says that it is busy to close etc.

I only run linux to have a local web server for my work, so, except all the rest of the 11.04 totally problematic behaviour in all areas, the server itself is perfectly setup and runs fluently. I did install a couple of stupid things like google earth, but all from within ubuntu. not getting the updates is bad.

any ideas ?

---

### Post by orasisd on 2011-07-07
oh also note that sometimes I get the: Not all updates can be installed > run a partial upgrade ...etc. which does install some stuff, but in the next time it will find updates it will get stuck again

---

### Post by Zill on 2011-07-07
orasisd:  Please post the output of the following command:
```
sudo apt-get dist-upgrade
```
Note that this will not actually upgrade the distribution but will try to upgrade the existing distribution using "smart" conflict resolution.

---

### Post by orasisd on 2011-07-07
hm... I just did a partial update and like last time, now it behaves as if there are no new updates until next time.

sudo apt-get dist-upgrade

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


```same goes for: sudo apt-get upgrade

but as I said, next time it will find updates, it will get stuck again
by the way, I always thought if there is any way to clean the update cache maybe ?

thanks alot

EDIT// 11.04 was a fresh install on a brand new pc that I didn't change hardware after installation.

---

### Post by Zill on 2011-07-07
orasisd:  The [AptGetHowto]("https://help.ubuntu.com/community/AptGet/Howto") document details all the appropriate commands to use and resolve apt-get problems.

I suggest the following commands may be useful:
```
sudo apt-get check
```
```
sudo apt-get -f install
```
```
sudo apt-get clean
```

---

### Post by orasisd on 2011-07-07
thank you zill for all your help, wish this was solved but I cannot know for now.
I used those commands for now and will have in mind, lets see until next update it finds.
this is the first time i fell into problems with updates. I don't have a problem re-installing everything. but a normal everyday user would just quit with ubuntu with such os behaviours, I 100% believe. and this is a damn bad thing for my fav ubuntu.

---

### Post by Zill on 2011-07-07
> **orasisd said:**
> thank you zill for all your help, wish this was solved but I cannot know for now.
I used those commands for now and will have in mind, lets see until next update it finds.
this is the first time i fell into problems with updates. I don't have a problem re-installing everything. but a normal everyday user would just quit with ubuntu with such os behaviours, I 100% believe. and this is a damn bad thing for my fav ubuntu.
Just keep the [AptGetHowto]("https://help.ubuntu.com/community/AptGet/Howto") document to hand and you should be able to resolve any future problems.

FWIW, you really should not need to re-install Ubuntu - it really is rock solid as long as you don't do anything daft!  I have been using Ubuntu since 2005 and have *never* needed to re-install.  I just stick to established LTS releases for stability and try not to install software that wasn't packaged for that particular release.  Then everything just works. :-)

---

### Post by YellowBronco on 2011-07-10
i have re-installed 5 or 6 times, i get the same flashing curser and when i finaly get into ubuntu it wont let me do updates either, i agree with u about the people who will just five up on ubuntu with this problem, now im getting a ,, Denial of services  message ,,, sestem is very slow also, 
is there a fix for this problem?
dan

---

### Post by Zill on 2011-07-10
YellowBronco:  Sorry you are having problems with Ubuntu but I do not fully understand your question.  This thread relates to error messages seen while updating and, unless you are having very similar problems, I suggest you start a new thread clearly listing exactly what problems you are experiencing.  Please use an explanatory title for each problem ("Help!" is useless as *everyone* posting wants help!)

I suggest you start by identifying exactly which Ubuntu release you are using.  Is this a new installation or an upgrade from a previous release?
Are you running Ubuntu on its own partition or within Windows as a wubi install?  Has this Ubuntu release ever run correctly on your PC?

Then describe what you see on the screen at each stage, together with any error messages that appear.

All this information will be of assistance in resolving your problem(s).

---

### Post by orasisd on 2011-07-12
back again.
As the new updates came up, and i was expecting it to get stuck again once more, it did.
By the way when it gets stuck you cannot cancel it, you have to kill it or logout/in. Then I opened a terminal and did the following commands.

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get -f install
sudo apt-get check
```and then I get this when I do update:

```
sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```Then I went to System > Administration > Update Manager, and click "Check" to check for all new updates. Now it got stuck at: "Updating Cache" at 0%
I can only kill it or logout to close this window.

Any idea why this is hapenning ?
many thanks

Edit//
I restarted and now it can check updates but once again it gets stuck at "Applying Changes"
When I do it in terminal I still get this now:

```
sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

I also removed google earth from the software sources, restarted even but it wasn't the one that was causing the problem.

I think it's totally broken :-) wish I had done something wrong to it myself so I know what not to do again.
I think I am going for a new install, but not 11.04 this time.

---

### Post by wildmanne39 on 2011-07-12
Hi, that message could be caused by having another instance of a software installer open, like the terminal or synaptic or software center, if you closed all of them but one sometimes you have to restart to get it to let you update.

---

### Post by Zill on 2011-07-12
> **wildmanne39 said:**
> Hi, that message could be caused by having another instance of a software installer open, like the terminal or synaptic or software center, if you closed all of them but one sometimes you have to restart to get it to let you update.
+1

All the package management systems, including apt-get, Synaptic and the Software Centre, are frontends for the same underlying dpkg system.  Only *one* of these frontends can run at once, otherwise errors occur due to file locks.

Can the OP please confirm that only *one* of these frontends is running when this error occurs.  Please also post the output of the following command:
```
sudo dpkg --configure -a
```

---

### Post by orasisd on 2011-07-12
thanks [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") thanks [Zill]("http://ubuntuforums.org/member.php?u=53885") for the answers indeed,
well, I was very aware that you cannot run 2 at the same time yes, and I didn't. But you can never know so, trying to test this issue, what happens is the following:

step1 > fresh boot > 1st time login to user account.
step2 > open terminal > sudo apt-get update > works fine.
step3 > then close terminal and go to update manager > gets stuck to the usual point > kill process (even logout/in as well).
step4 > then open terminal again (without update manager running) and repeat step2 and I get the error that indeed gets solved with restart.

So ok that is not the problem for me, doesn't matter much.


zill, the command sudo dpkg --configure -a had no output at all.

thanks everyone

EDIT//
by the way of course now the command sudo apt-get -f install shows:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and [COLOR=Red]**6 not upgraded**[/COLOR].

```

---

### Post by Zill on 2011-07-12
> **orasisd said:**
> ...what happens is the following:

step1 > fresh boot > 1st time login to user account.
step2 > open terminal > sudo apt-get update > works fine.
step3 > then close terminal and go to update manager > gets stuck to the usual point > kill process (even logout/in as well).
step4 > then open terminal again (without update manager running) and repeat step2 and I get the error that indeed gets solved with restart
I am concerned that your step3 above uses the update manager which then gets stuck.  This starts a root process, not a user process, and so it may be that it is not being properly "killed" if you try to kill as a user.  Similarly, logout/in only ends user processes, leaving root processes still running.

What happens if you try changing step3 to "**sudo apt-get dist-upgrade**" in the terminal?  i.e. are packages upgraded correctly or do any errors occur?

> zill, the command sudo dpkg --configure -a had no output at all.
This is correct if apt-get runs correctly, with no locks present.  It is worth running this command if you get the "E: Could not get lock..." error again.

---

### Post by orasisd on 2011-07-12
thanks zill again for helping,

I haven't tried the upgrade commands just in case we might need it stuck for now :-)
So after a restart I do the following and these are the results:

sudo apt-get update
```

Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty InRelease 
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Ign http://archive.canonical.com natty InRelease
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Hit http://archive.ubuntu.com natty Release.gpg                               
Hit http://archive.canonical.com natty Release.gpg
Hit http://extras.ubuntu.com natty Release     
Hit http://archive.ubuntu.com natty-updates Release.gpg               
Hit http://archive.canonical.com natty Release 
Hit http://extras.ubuntu.com natty/main Sources                       
Hit http://archive.ubuntu.com natty-security Release.gpg
Hit http://archive.canonical.com natty/partner Sources
Hit http://extras.ubuntu.com natty/main i386 Packages
Ign http://extras.ubuntu.com natty/main TranslationIndex
Hit http://archive.ubuntu.com natty Release    
Hit http://archive.canonical.com natty/partner i386 Packages                                
Ign http://archive.canonical.com natty/partner TranslationIndex      
Hit http://archive.ubuntu.com natty-updates Release
Hit http://archive.ubuntu.com natty-security Release                                        
Hit http://archive.ubuntu.com natty/main Sources                                            
Hit http://archive.ubuntu.com natty/restricted Sources               
Hit http://archive.ubuntu.com natty/universe Sources                 
Hit http://archive.ubuntu.com natty/multiverse Sources               
Hit http://archive.ubuntu.com natty/main i386 Packages               
Hit http://archive.ubuntu.com natty/restricted i386 Packages         
Hit http://archive.ubuntu.com natty/universe i386 Packages
Hit http://archive.ubuntu.com natty/multiverse i386 Packages
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex      
Ign http://archive.ubuntu.com natty/restricted TranslationIndex      
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Hit http://archive.ubuntu.com natty-updates/main Sources
Hit http://archive.ubuntu.com natty-updates/restricted Sources       
Hit http://archive.ubuntu.com natty-updates/universe Sources         
Hit http://archive.ubuntu.com natty-updates/multiverse Sources       
Hit http://archive.ubuntu.com natty-updates/main i386 Packages
Hit http://archive.ubuntu.com natty-updates/restricted i386 Packages 
Hit http://archive.ubuntu.com natty-updates/universe i386 Packages   
Hit http://archive.ubuntu.com natty-updates/multiverse i386 Packages
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://archive.ubuntu.com natty-security/main Sources
Hit http://archive.ubuntu.com natty-security/restricted Sources      
Hit http://archive.ubuntu.com natty-security/universe Sources        
Hit http://archive.ubuntu.com natty-security/multiverse Sources      
Hit http://archive.ubuntu.com natty-security/main i386 Packages      
Ign http://extras.ubuntu.com natty/main Translation-en_US            
Hit http://archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://archive.ubuntu.com natty-security/universe i386 Packages
Hit http://archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://archive.ubuntu.com natty-security/main TranslationIndex   
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en
Ign http://archive.ubuntu.com natty/main Translation-en_US
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Fetched 72 B in 3s (24 B/s)
Reading package lists... Done

```
sudo apt-get dist-upgrade
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  nautilus-sendto ntp ntpdate software-center xserver-xorg-video-ati xserver-xorg-video-radeon
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,524 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Reading changelogs... Done





Get:1 Changelog for nautilus-sendto (http://changelogs.ubuntu.com/changelogs/pool/main/n/nautilus-sendto/nautilus-sendto_2.32.0-0ubuntu1.1/changelog) [14.8 kB]
nautilus-sendto (2.32.0-0ubuntu1.1) natty-proposed; urgency=low

  * Rebuild to fix crash in libnstevolution (build against libebook-1.2.so.9.
    (LP: #765847)

 -- Mathieu Trudel-Lapierre <mathieu-tl@ubuntu.com>  Fri, 01 Jul 2011 11:14:47 -0400

Get:1 Changelog for ntpdate (http://changelogs.ubuntu.com/changelogs/pool/main/n/ntp/ntp_4.2.6.p2+dfsg-1ubuntu5.1/changelog) [88.3 kB]
ntp (1:4.2.6.p2+dfsg-1ubuntu5.1) natty-proposed; urgency=low

  * debian/patches/ntpdate-accept-same-timestamp-replies.patch:
    Resolving regression where ntpdate ignores replies from some
    ntp servers where recieve and transmit timestamps are equal.
    Patch cherry picked from upstream commit. (LP: #787551)

 -- Dave Walker (Daviey) <DaveWalker@ubuntu.com>  Mon, 13 Jun 2011 15:43:57 +0100

Get:1 Changelog for software-center (http://changelogs.ubuntu.com/changelogs/pool/main/s/software-center/software-center_4.0.4/changelog) [182 kB]
software-center (4.0.4) natty-proposed; urgency=low

  [ Aaron Peachey ]
  * utils/submit_review.py:
    - ensure error message shows if usefulness submit 
      fails (LP: #790450)
  * softwarecenter/view/widgets/reviews.py:
    - fix disappearing usefulness UI on clicking 'OK' after error
  * softwarecenter/db/reviews.py,
    softwarecenter/view/appdetailsview_gtk.py,
    softwarecenter/view/widgets/reviews.py:
    - fix duplication of reviews after user has submitted
      usefulness or flagged a review (LP: #794060)

  [ Gary Lasker ]
  * softwarecenter/app.py,
    softwarecenter/view/softwarepane.py:
    - fix issue where the background image for installed channels
      details view is not consistently rendered (LP: #724724) 

 -- Michael Vogt <michael.vogt@ubuntu.com>  Fri, 10 Jun 2011 18:22:41 +0200

Get:1 Changelog for xserver-xorg-video-radeon (http://changelogs.ubuntu.com/changelogs/pool/main/x/xserver-xorg-video-ati/xserver-xorg-video-ati_6.14.0-0ubuntu4.1/changelog) [54.9 kB]
xserver-xorg-video-ati (1:6.14.0-0ubuntu4.1) natty-proposed; urgency=low

  * 102_disable_pageflipping_for_transformed_displays.patch:
    Add cherrypick patch to not enable pageflipping if display has been
    rotated.  Fixes issue where garbage appears on rotated screens
    while rotated.
    (LP: #772111)

 -- Bryce Harrington <bryce@ubuntu.com>  Thu, 30 Jun 2011 17:25:30 -0700

~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END) 

```stuck here again, only ctrl+c to leave it. but looks like we are almost there ? cause I use no ATI, I have nvidia installed. shall I just remove:

xserver-xorg-video-ati
xserver-xorg-video-radeon

.. from the synaptic package manager ? they both appear with exclamation mark (!)

> **Zill said:**
> This starts a root process, not a user process, and  so it may be that it is not being properly "killed" if you try to kill  as a user.  Similarly, logout/in only ends user processes, leaving root  processes still running.

this makes sense :-) I should have though of that myself, but lately I indeed feel like "it's not working well", maybe cause of summer heat, or I am getting to old maybe ?

thanks !

---

### Post by Zill on 2011-07-12
> **orasisd said:**
> ...stuck here again, only ctrl+c to leave it. but looks like we are almost there ? cause I use no ATI, I have nvidia installed. shall I just remove:

xserver-xorg-video-ati
xserver-xorg-video-radeon

.. from the synaptic package manager ? they both appear with exclamation mark (!)
According to Synaptic, Help, Icon Legend an exclamation mark has two possible meanings, depending on your colour scheme.  One means "Installed (upgradable)" and the other means "Broken".  Unfortunately, I doubt that these packages are really the cause of the problem as I have both packages installed on my Nvidia system as well.  However, I see no reason why you could not remove them if you wish.

I do not use Natty myself as I stick to LTS releases such as Lucid.  Maybe someone using a Natty system can verify the outputs you have already supplied, such as the sources.list and from the update/upgrade commands.

All I can suggest is that there may be a broken package somewhere, possibly within apt itself.  I would try selecting Synaptic Custom Filters to identify any broken packages.  If any show up, use Synaptic to reinstall each one singly.  Note that you may need to reboot between each package reinstallation to ensure the apt-get system is not locked up.  As mentioned, you could also try reinstalling apt.

It may be worth retrying the commands listed in my post [#13]("http://ubuntuforums.org/showpost.php?p=11022722&postcount=13") above.

---

### Post by orasisd on 2011-07-12
Unfortunately, if I uninstall any of these 2 drivers it says it will have to uninstall xserver-xorg-video-all as well. their color is grey (except xserver-xorg-video-all) and is same icon as nautilus-sendto, ntp, ntpdate and software-center.

Using Custom Filters // Broken > it shows nothing
I also reinstalled apt, restarted, tried those commands again, and that didn't change the situation. in a way I did everything you suggested in this reply of yours here.

To be honest, I always had LTS installed, also because my time is very limited to mess with computer problems (in the past I was messing a lot with that and never used a computer that way), but getting a new i7 computer made me feel like I wanted to install the latest of everything as I saw much difference from previous pc :-) I also always thought it is much faster and smart move, to reinstall ubuntu or try a different version than posting on the forum, but this time I acted differently.

I will once again express my personal opinion, not about linux or ubuntu services etc, which are the best and I am also depended on (and not only me), but about ubuntu as a desktop environment. The more the time passes, instead of getting better, it appears to have more (a lot more) problems, for instance, right now the screen of the linux next to me went off although I have set everything to NEVER (screensaver, power management, etc). These are not serious things for such a serious os. Always new releases in very short time is not the best way to progress I believe, I would expect longer periods of not having a new ubuntu version even for the non LTS. But I don't know, that's just opinion.

well, as I said, too much time for nothing, I will just install 10.04 LTS and see.

But indeed, thanks for your great help and interest mr zill, I honestly appreciate it, as it seamed that before you appeared the forum died, and it wasn't like that years ago.

sorry for going off topic a little,
peace

---

### Post by Zill on 2011-07-12
> **orasisd said:**
> ...Using Custom Filters // Broken > it shows nothing
I also reinstalled apt, restarted, tried those commands again, and that didn't change the situation. in a way I did everything you suggested in this reply of yours here.
Did you try reinstalling *each* of the problem packages using Synaptic ***in turn*** as I suggested?  I suggest you reboot between each one to make sure there are no "sticky toffees" left by the upgrade process.

The only other suggestion I have is to replace your /etc/apt/sources.list file with a new, totally clean version, just in case yours has an error I haven't noticed.  If you boot temporarily with your Natty live CD you can then copy this good file to, for example, a USB thumbdrive.  If this works you can then update the default sources.list with your nearest location.

---

### Post by wildmanne39 on 2011-07-12
Hi, you can try these two commands it might take care of your problem.
```
sudo rm /var/lib/apt/lists/* -vf

```
```
sudo apt-get update
```

---

### Post by orasisd on 2011-07-12
back to you guys in a few minutes
thanks again

---

### Post by orasisd on 2011-07-12
zill, reinstalled the following packages with reboots after each one:

```
apt
apt-listchanges
apt-transport-https
apt-utils
apt-xapian-index
aptdaemon
aptdaemon-data
apturl
apturl-common
libept1
libqapt-runtime
libqapt1
python-apt
python-apt-common
python-aptdaemon
python-aptdaemon-gtk
python-aptdaemon.gtk3widgets
python-aptdaemon.gtkwidgets
python-software-properties
sessioninstaller
software-properties-gtk
software-properties-kde
synaptic
unattended-upgrades
update-manager
update-notifier-common
xul-ext-ubufox
```problem still there

wildmanne39, I did the commands you advised me, but no success. I get this:

sudo rm /var/lib/apt/lists/* -vf
```

removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_source_Sources'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-security_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_universe_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_main_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_Release'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_Release.gpg'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty-updates_universe_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_Release.gpg'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
```sudo apt-get update

```

Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.canonical.com natty InRelease                           
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]                    
Ign http://archive.ubuntu.com natty InRelease  
Ign http://archive.ubuntu.com natty-updates InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Get:2 http://archive.canonical.com natty Release.gpg [198 B]
Get:3 http://extras.ubuntu.com natty Release [9,753 B]                          
Get:4 http://archive.ubuntu.com natty Release.gpg [198 B]                      
Get:5 http://archive.canonical.com natty Release [5,916 B]                                
Get:6 http://archive.ubuntu.com natty-updates Release.gpg [198 B]                        
Get:7 http://archive.ubuntu.com natty-security Release.gpg [198 B]                                  
Get:8 http://extras.ubuntu.com natty/main Sources [14 B]                           
Get:9 http://archive.ubuntu.com natty Release [39.8 kB]                                    
Get:10 http://archive.canonical.com natty/partner Sources [4,159 B]           
Get:11 http://extras.ubuntu.com natty/main i386 Packages [14 B]                                       
Ign http://extras.ubuntu.com natty/main TranslationIndex                              
Get:12 http://archive.canonical.com natty/partner i386 Packages [7,861 B]        
Ign http://archive.canonical.com natty/partner TranslationIndex                            
Get:13 http://archive.ubuntu.com natty-updates Release [27.2 kB]                              
Get:14 http://archive.ubuntu.com natty-security Release [27.2 kB]                                       
Get:15 http://archive.ubuntu.com natty/main Sources [862 kB]                                           
Ign http://extras.ubuntu.com natty/main Translation-en_US                                             
Ign http://extras.ubuntu.com natty/main Translation-en                        
Ign http://archive.canonical.com natty/partner Translation-en_US
Ign http://archive.canonical.com natty/partner Translation-en
Get:16 http://archive.ubuntu.com natty/restricted Sources [4,104 B]
Get:17 http://archive.ubuntu.com natty/universe Sources [4,380 kB]
Get:18 http://archive.ubuntu.com natty/multiverse Sources [155 kB]                                                                             
Get:19 http://archive.ubuntu.com natty/main i386 Packages [1,550 kB]                                                                           
Get:20 http://archive.ubuntu.com natty/restricted i386 Packages [8,986 B]                                                                      
Get:21 http://archive.ubuntu.com natty/universe i386 Packages [6,021 kB]                                                                       
Get:22 http://archive.ubuntu.com natty/multiverse i386 Packages [183 kB]                                                                       
Ign http://archive.ubuntu.com natty/main TranslationIndex                                                                                      
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex                                                                                
Ign http://archive.ubuntu.com natty/restricted TranslationIndex                                                                                
Ign http://archive.ubuntu.com natty/universe TranslationIndex                                                                                  
Get:23 http://archive.ubuntu.com natty-updates/main Sources [92.1 kB]                                                                          
Get:24 http://archive.ubuntu.com natty-updates/restricted Sources [14 B]                                                                       
Get:25 http://archive.ubuntu.com natty-updates/universe Sources [17.9 kB]                                                                      
Get:26 http://archive.ubuntu.com natty-updates/multiverse Sources [1,893 B]                                                                    
Get:27 http://archive.ubuntu.com natty-updates/main i386 Packages [268 kB]                                                                     
Get:28 http://archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]                                                                 
Get:29 http://archive.ubuntu.com natty-updates/universe i386 Packages [68.5 kB]                                                                
Get:30 http://archive.ubuntu.com natty-updates/multiverse i386 Packages [4,267 B]                                                              
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex                                                                              
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex                                                                        
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex                                                                        
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex                                                                          
Get:31 http://archive.ubuntu.com natty-security/main Sources [57.0 kB]                                                                         
Get:32 http://archive.ubuntu.com natty-security/restricted Sources [14 B]                                                                      
Get:33 http://archive.ubuntu.com natty-security/universe Sources [7,103 B]                                                                     
Get:34 http://archive.ubuntu.com natty-security/multiverse Sources [658 B]                                                                     
Get:35 http://archive.ubuntu.com natty-security/main i386 Packages [146 kB]                                                                    
Get:36 http://archive.ubuntu.com natty-security/restricted i386 Packages [14 B]                                                                
Get:37 http://archive.ubuntu.com natty-security/universe i386 Packages [22.0 kB]                                                               
Get:38 http://archive.ubuntu.com natty-security/multiverse i386 Packages [2,074 B]                                                             
Ign http://archive.ubuntu.com natty-security/main TranslationIndex                                                                             
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex                                                                       
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex                                                                       
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex                                                                         
Ign http://archive.ubuntu.com natty/main Translation-en_US                                                                                     
Ign http://archive.ubuntu.com natty/main Translation-en                                                                                        
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US                                                                               
Ign http://archive.ubuntu.com natty/multiverse Translation-en                                                                                  
Ign http://archive.ubuntu.com natty/restricted Translation-en_US                                                                               
Ign http://archive.ubuntu.com natty/restricted Translation-en                                                                                  
Ign http://archive.ubuntu.com natty/universe Translation-en_US                                                                                 
Ign http://archive.ubuntu.com natty/universe Translation-en                                                                                    
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US                                                                             
Ign http://archive.ubuntu.com natty-updates/main Translation-en                                                                                
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US                                                                       
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en                                                                          
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US                                                                       
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en                                                                          
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US                                                                         
Ign http://archive.ubuntu.com natty-updates/universe Translation-en                                                                            
Ign http://archive.ubuntu.com natty-security/main Translation-en_US                                                                            
Ign http://archive.ubuntu.com natty-security/main Translation-en                                                                               
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US                                                                      
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en                                                                         
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US                                                                      
Ign http://archive.ubuntu.com natty-security/restricted Translation-en                                                                         
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US                                                                        
Ign http://archive.ubuntu.com natty-security/universe Translation-en                                                                           
Fetched 14.0 MB in 16s (841 kB/s)                                                                                                              
Reading package lists... Done
```but when I do the upgrade it gets stuck again.


> **Zill said:**
> The only other suggestion I have is to replace your /etc/apt/sources.list file with a new
This is the only thing I haven't done... I will have to this too !

thank you so much.

EDIT//
Question: Once it gets stuck at "Applying Changes" and not at downloading, do the sources.list play a role in this ?

---

### Post by Zill on 2011-07-13
> **orasisd said:**
> ...EDIT//
Question: Once it gets stuck at "Applying Changes" and not at downloading, do the sources.list play a role in this ?
Simple answer - I don't know. :-(  Maybe someone else can clarify this one.

I still think it is worth trying a new "clean" sources.list.  Just rename your old one so that you have it as a backup for reference if needed.  It may be necessary to run some of the commands discussed earlier to ensure apt runs correctly with a new sources.list.  Just post whatever errors are flagged up - maybe the same as before or maybe different. ;-)

ps.  I do suggest that you use "sudo apt-get update" followed by "sudo apt-get [COLOR="Red"]dist-upgrade[/COLOR]" rather than "sudo apt-get upgrade" when the sources.list has been replaced.  This should ensure that *all* relevant packages are updated together.

---

### Post by MichaelLenahan on 2011-07-20
Hi there

I have been experiencing the same problem with natty.

In the Details window, where the Changelog messages are appearing, I type q to quit and the update manager continues as normal.

(On my system the window works like vim - clicking k moves up one line, j down one line, q quits and so on).

Not a solution to the original problem I know, but I thought I'd mention it if it helps.

---

### Post by orasisd on 2011-07-23
zill, took me a while to respond once I am moving house to Athens and I got many things to do. Thanks for all the help, unfortunately, I think that If I am to replace almost every piece of the os with the original at the moment that I haven't done anything wrong myself, or the power never went down, or, or, it is far better and smart to re-install. Lets take it as a fact, and you already must know once old in computers too, that sometimes computers just DON'T WANT to do things for you right. I have learned this since my first Texas Instruments computer (age of spectrum). Well in this case this version of Ubuntu didn't want to do 'anything' right for me. To me it is a fail of the version, although I can be nice and say "you never know what might have gone wrong". But I really take care of my systems and what they run, even when developers don't.

MichaelLenahan, thanks for the reply, really didn't know such a thing, tried it and indeed the update continued. But I think you don't need to guess what happened to the next update :-) ---->go stuck again ? yes..

Actually, with the last update I have done, there was one thing missing to break too (cause everything else is not running fine on 11.04 either), and that was grub. Since the last update, I cannot set which is gonna be the default OS to boot using StartUp-Manager.

In a few words, better work with something else, than facing the developer's ignorance for people's limits. Very sorry, but this was the worst Ubuntu version I ever-ever installed. I will go back to 10.04 or switch to debian, and if I was not using linux as a web server etc, I would never think of installing ubuntu ever again.

thanks for you help guys, indeed I appreciate from heart.
peace.

EDIT//
maybe an advice to the devs: Feel just a little shame, every time you release something that is at a "broken" state.

---

