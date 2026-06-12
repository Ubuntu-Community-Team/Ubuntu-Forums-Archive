---
title: "Can't run Updates"
date: 2012-07-28
forum: General Help
---

### Post by rickm1945 on 2012-07-28
Trying to download and install updates for the past two days and keep getting error messages. Here is the last one I got after trying to install updates. How do I put this is a code box? The # in the post option doesn't work.

                                  Error authenticating some packages  
 

 It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
 
```

 atril  
 atril-common  
 caja  
 caja-common  
 engrampa  
 engrampa-common  
 eom  
 eom-common  
 ffmpegthumbnailer-caja  
 libatril  
 libcaja-extension  
 libmarco  
 libmate  
 libmate-common  
 libmatebluetooth  
 libmatecanvas  
 libmatecomponent  
 libmatecomponentui  
 libmateconf  
 libmatecorba  
 libmatedesktop  
 libmatekbd  
 libmatekeyring  
 libmatemenu  
 libmatenotify  
 libmatepanelapplet  
 libmatepolkit  
 libmateui  
 libmatevfs  
 libmateweather  
 libmateweather-common  
 libmatewnck  
 libmatewnck-common  
 marco  
 marco-common  
 mate-applets  
 mate-applets-common  
 mate-backgrounds  
 mate-bluetooth  
 mate-calc  
 mate-conf  
 mate-conf-common  
 mate-control-center  
 mate-corba  
 mate-core  
 mate-desktop  
 mate-desktop-common  
 mate-desktop-environment  
 mate-dialogs  
 mate-icon-theme  
 mate-keyring  
 mate-media  
 mate-media-common  
 mate-media-gstreamer  
 mate-menus  
 mate-mime-data  
 mate-netspeed  
 mate-panel  
 mate-panel-common  
 mate-polkit  
 mate-power-manager  
 mate-power-manager-common  
 mate-screensaver  
 mate-session-manager  
 mate-settings-daemon  
 mate-settings-daemon-common  
 mate-settings-daemon-gstreamer  
 mate-system-monitor  
 mate-system-tools  
 mate-terminal  
 mate-terminal-common  
 mate-text-editor  
 mate-themes  
 mate-user-share  
 mate-utils  
 mate-vfs  
 mate-vfs-common  
 mate-window-manager  
 mozo  
 python-corba  
 python-mate  
 python-mate-desktop  
 python-mate-menu
```
  Anybody know what is  going on?

---

### Post by matt_symes on 2012-07-28
Hi

Open a terminal and type

```
sudo apt-get update
```Enter your password. It will not be echoed to the screen.

Post the output back here between code tag like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by rickm1945 on 2012-07-29
> **matt_symes said:**
> Hi

Open a terminal and type

```
sudo apt-get update
```Enter your password. It will not be echoed to the screen.

Post the output back here between code tag like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```Kind regards

```

richard@XPS8100:~$ sudo apt-get update
[sudo] password for richard: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]       
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]               
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [32.4 kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,849 B]  
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [121 kB] 
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [26.8 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:22 [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease [4,977 B]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Sources/DiffIndex            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main i386 Packages/DiffIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main TranslationIndex             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Sources                      
Hit [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main i386 Packages                
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [138 kB]      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [2,073 B]
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [41.2 kB] 
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [339 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [3,949 B]
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [109 kB]
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,540 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [2,422 B]   
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [12.4 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [1,383 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [1,941 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [11.2 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [999 B]
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
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en_US            
Ign [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise/main Translation-en               
Fetched 13.4 MB in 12s (1,032 kB/s)                                            
Reading package lists... Done
W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8
richard@XPS8100:~$ 

```

---

### Post by plucky on 2012-07-29
> W: GPG error: [http://packages.mate-desktop.org](http://packages.mate-desktop.org) precise InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 68980A0EA10B4DE8
richard@XPS8100:~$

Open a terminal an run ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 68980A0EA10B4DE8
gpg --export --armor 68980A0EA10B4DE8 | sudo apt-key add -
``` This will add the missing key for the repository.

Good luck

---

### Post by rickm1945 on 2012-07-30
> **plucky said:**
> Open a terminal an run ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 68980A0EA10B4DE8
gpg --export --armor 68980A0EA10B4DE8 | sudo apt-key add -
``` This will add the missing key for the repository.

Good luck
Thanks

---

### Post by maneto on 2012-10-30
> **plucky said:**
> Open a terminal an run ```
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 68980A0EA10B4DE8
gpg --export --armor 68980A0EA10B4DE8 | sudo apt-key add -
``` This will add the missing key for the repository.

Good luck
I have this problem when trying to install mate in Quantal Quetzal and I'll find this answer which suits me.

Thanks.

---

### Post by Dafydd on 2012-11-08
> **maneto said:**
> I have this problem when trying to install mate in Quantal Quetzal and I'll find this answer which suits me.

Thanks.

thanks too. worked for me on 12.10.

---

