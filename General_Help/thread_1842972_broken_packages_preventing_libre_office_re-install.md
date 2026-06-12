---
title: "broken packages preventing libre office re-install"
date: 2011-09-12
forum: General Help
---

### Post by GreenEU on 2011-09-12
I've had problem with libre office so I tries a complete uninstallation and reinstalliing - except synaptic manager tells me I have broken packages and the software centre insists I repair but then tells me repair is impossible. This is the detail it gives:

```
installArchives() failed: Selecting previously deselected package libreoffice-style-human. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 178306 files and directories currently installed.) 
Unpacking libreoffice-style-human (from .../libreoffice-style-human_1%3a3.3.3-1ubuntu2_all.deb) ... 
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb) ... 
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb (--unpack): 
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556 
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe) 
Selecting previously deselected package libreoffice-core. 
Unpacking libreoffice-core (from .../libreoffice-core_1%3a3.3.3-1ubuntu2_i386.deb) ... 
Selecting previously deselected package libreoffice-base-core. 
Unpacking libreoffice-base-core (from .../libreoffice-base-core_1%3a3.3.3-1ubuntu2_i386.deb) ... 
Selecting previously deselected package libreoffice-calc. 
Unpacking libreoffice-calc (from .../libreoffice-calc_1%3a3.3.3-1ubuntu2_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Can't open /usr/share/applications/openoffice.org3-base.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-calc.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-draw.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-impress.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-javafilter.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-math.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-printeradmin.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-startcenter.desktop: No such file or directory at -e line 1, <> line 2455. 
Can't open /usr/share/applications/openoffice.org3-writer.desktop: No such file or directory at -e line 1, <> line 2455. 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for shared-mime-info ... 
Unknown media type in type 'all/all' 
Unknown media type in type 'all/allfiles' 
Unknown media type in type 'uri/mms' 
Unknown media type in type 'uri/mmst' 
Unknown media type in type 'uri/mmsu' 
Unknown media type in type 'uri/pnm' 
Unknown media type in type 'uri/rtspt' 
Unknown media type in type 'uri/rtspu' 
Unknown media type in type 'interface/x-winamp-skin' 
Processing triggers for python-support ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb 
dpkg: dependency problems prevent configuration of libreoffice-core: 
 libreoffice-core depends on libreoffice-common (>> 1:3.3.3); however: 
  Package libreoffice-common is not installed. 
dpkg: error processing libreoffice-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-style-human: 
 libreoffice-style-human depends on libreoffice-core; however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-style-human (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-base-core: 
 libreoffice-base-core depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however: 
  Package libreoffice-core is not configured yet. 
dpkg: error processing libreoffice-base-core (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libreoffice-calc: 
 libreoffice-calc depends on libreoffice-core (= 1:3.3.3-1ubuntu2); however: 
  Package libreoffice-core is not configured yet. 
 libreoffice-calc depends on libreoffice-base-core (= 1:3.3.3-1ubuntu2); however: 
  Package libreoffice-base-core is not configured yet. 
dpkg: error processing libreoffice-calc (--configure): 
 dependency problems - leaving unconfigured 
```


can anyone offer help, please?

---

### Post by ubudog on 2011-09-12
Can you post the output of:
```
sudo apt-get update
```
?

---

### Post by GreenEU on 2011-09-12
```
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease                                  
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty InRelease                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates InRelease                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release.gpg                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release.gpg                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty Release                           
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release.gpg [198 B]  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty Release  
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates Release [31.4 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Sources                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main i386 Packages                         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main TranslationIndex                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Sources                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en_GB                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe TranslationIndex               
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Sources [105 kB]         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Sources [14 B]     
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Sources [25.2 kB]    
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Sources [1,890 B]  
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main i386 Packages [315 kB]   
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_GB               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_GB                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_GB           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en         
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe i386 Packages [92.2 kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) natty/main Translation-en                       
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,258 B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/main Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/multiverse Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/restricted Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) natty-updates/universe Translation-en
Fetched 575 kB in 1s (415 kB/s)
Reading package lists... Done
```

---

### Post by ubudog on 2011-09-12
Run this:
```
sudo apt-get -f install
```

And post the output please.
(that command will attempt to repair your packages)

---

### Post by GreenEU on 2011-09-12
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-common
Suggested packages:
  libreoffice-style-hicontrast libreoffice-style-tango
  libreoffice-style-crystal libreoffice-style-oxygen
The following NEW packages will be installed
  libreoffice-common
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
4 not fully installed or removed.
Need to get 0 B/16.8 MB of archives.
After this operation, 43.8 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 178545 files and directories currently installed.)
Unpacking libreoffice-common (from .../libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb (--unpack):
 trying to overwrite '/usr/share/mime/packages/openoffice.org.xml', which is also in package openoffice.org-debian-menus 3.3-9556
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Can't open /usr/share/applications/openoffice.org3-base.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-calc.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-draw.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-impress.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-javafilter.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-math.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-printeradmin.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-startcenter.desktop: No such file or directory at -e line 1, <> line 2455.
Can't open /usr/share/applications/openoffice.org3-writer.desktop: No such file or directory at -e line 1, <> line 2455.
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-common_1%3a3.3.3-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

