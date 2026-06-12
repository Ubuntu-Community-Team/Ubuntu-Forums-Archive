---
title: "The following packages have unresolvable dependencies."
date: 2012-07-07
forum: General Help
---

### Post by CLCressman on 2012-07-07
I am running Precise. I usually use Synaptic to do my updates. This morning I hit Reload in Synaptic, then Mark All Upgrades. When I hit Apply it said there were 3 packages held back, so I went looking. They are linux-generic-pae, linux-headers-generic-pae, linux-image-generic-pae. All are installed version 3.2.0.26.28 and latest available version 3.2.0.27.29. When I try to mark linux-headers-generic-pae for Update I get a message. 

The following packages have unresolvable dependencies.
linux-image-generic-pae:
 Depends: linux-image-3.2.0-27-generic-pae  but it is not installable

What am I doing wrong?

---

### Post by Bucky Ball on 2012-07-07
Try these two commands in a terminal:

```
sudo apt-get update
sudo apt-get upgrade
```Post any errors here. ;)

*Always* update before upgrading.

---

### Post by danforward on 2012-07-07
I am having a similar issue. I ran

```
sudo apt-get update
``` followed by:

```
sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```

If I use Synaptic and I select [FONT="Courier New"]linux-generic[/FONT] for upgrade, it wants to remove [FONT="Courier New"]linux-image-generic[/FONT] and vice-versa. If I select [FONT="Courier New"]linux-headers-generic[/FONT] for upgrade, it says

```
Depends: linux-headers-3.2.0-27-generic  but it is not installable
```

---

### Post by CLCressman on 2012-07-07
I don't see any errors from the first command.

sudo apt-get update```
chester@Blue:~$ sudo apt-get update
[sudo] password for chester: 
Hit http://packages.sil.org precise InRelease                                  
Hit http://packages.sil.org precise/main Sources                               
Ign http://security.ubuntu.com precise-security InRelease                      
Ign http://extras.ubuntu.com precise InRelease                                 
Hit http://packages.sil.org precise/main i386 Packages                         
Ign http://packages.sil.org precise/main TranslationIndex                      
Ign http://ppa.launchpad.net precise InRelease                                 
Ign http://us.archive.ubuntu.com precise InRelease                             
Ign http://us.archive.ubuntu.com precise-updates InRelease                     
Ign http://us.archive.ubuntu.com precise-backports InRelease                   
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]          
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Ign http://us.archive.ubuntu.com precise-proposed InRelease                    
Get:2 http://us.archive.ubuntu.com precise Release.gpg [198 B]                 
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]            
Hit http://extras.ubuntu.com precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Get:5 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]       
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise/main Sources                              
Get:6 http://us.archive.ubuntu.com precise-proposed Release.gpg [198 B]        
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]                   
Get:8 http://security.ubuntu.com precise-security/main Sources [22.5 kB]       
Ign http://packages.sil.org precise/main Translation-en_US                     
Get:9 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Ign http://packages.sil.org precise/main Translation-en                        
Get:10 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]        
Get:11 http://security.ubuntu.com precise-security/restricted Sources [14 B]   
Get:12 http://security.ubuntu.com precise-security/universe Sources [7,832 B]  
Get:13 http://us.archive.ubuntu.com precise-proposed Release [49.6 kB]         
Get:14 http://security.ubuntu.com precise-security/multiverse Sources [713 B]  
Get:15 http://security.ubuntu.com precise-security/main i386 Packages [70.2 kB]
Get:16 http://us.archive.ubuntu.com precise/main Sources [934 kB]              
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Get:17 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:18 http://security.ubuntu.com precise-security/universe i386 Packages [19.0 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Ign http://ppa.launchpad.net precise/main Translation-en                       
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:20 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:21 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:22 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:23 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:24 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:25 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:26 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:27 http://us.archive.ubuntu.com precise-updates/main Sources [124 kB]      
Get:28 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:29 http://us.archive.ubuntu.com precise-updates/universe Sources [30.6 kB] 
Get:30 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:31 http://us.archive.ubuntu.com precise-updates/main i386 Packages [314 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:33 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [85.7 kB]
Get:34 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Get:35 http://us.archive.ubuntu.com precise-backports/main Sources [1,845 B]   
Get:36 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:37 http://us.archive.ubuntu.com precise-backports/universe Sources [11.1 kB]
Get:38 http://us.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:39 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:40 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:41 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [9,703 B]
Get:42 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex       
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex   
Get:43 http://us.archive.ubuntu.com precise-proposed/restricted i386 Packages [14 B]
Get:44 http://us.archive.ubuntu.com precise-proposed/main i386 Packages [166 kB]
Get:45 http://us.archive.ubuntu.com precise-proposed/multiverse i386 Packages [14 B]
Get:46 http://us.archive.ubuntu.com precise-proposed/universe i386 Packages [22.5 kB]
Hit http://us.archive.ubuntu.com precise-proposed/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise-proposed/multiverse TranslationIndex  
Hit http://us.archive.ubuntu.com precise-proposed/restricted TranslationIndex  
Hit http://us.archive.ubuntu.com precise-proposed/universe TranslationIndex    
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en         
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en     
Hit http://us.archive.ubuntu.com precise-proposed/main Translation-en          
Hit http://us.archive.ubuntu.com precise-proposed/multiverse Translation-en    
Hit http://us.archive.ubuntu.com precise-proposed/restricted Translation-en    
Hit http://us.archive.ubuntu.com precise-proposed/universe Translation-en      
Fetched 13.5 MB in 2min 10s (103 kB/s)                                         
Reading package lists... Done

```Here is the next command.

sudo apt-get upgrade
```
chester@Blue:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```What next?

Thanks for the help.

---

### Post by Bucky Ball on 2012-07-07
You could also try:

```
sudo apt-get dist-upgrade
```

After an update, naturally. ;)

---

### Post by CLCressman on 2012-07-07
```
chester@Blue:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic-pae linux-headers-generic-pae linux-image-generic-pae
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```
Now what?

Thanks again.

---

### Post by CLCressman on 2012-07-10
Something changed.  When I did a Reload in Synaptic, everything worked normally. Maybe there was a bug. :)

---

### Post by Bucky Ball on 2012-07-10
It is 12.04 ... should settle some at 12.04.1 which will be sometime later this month. 

Good luck and enjoy the OS. ;)

---

