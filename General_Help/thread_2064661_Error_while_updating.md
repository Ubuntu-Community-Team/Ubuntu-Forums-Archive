---
title: "Error while updating"
date: 2012-09-29
forum: General Help
---

### Post by N64Cam on 2012-09-29
cam@Cam:~$ sudo apt-get -f install
[sudo] password for cam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  lib32bz2-1.0 libsdl-ttf2.0-0 libaccess-bridge-java lib32ncurses5 libx264-116
  libfile-homedir-perl lib32tinfo5 libxdg-basedir1 libiso9660-7 caribou
  lib32ffi6 lib32nss-mdns libaccess-bridge-java-jni libreadline5 libvpx0
  libjpeg62:i386 lib32ncursesw5 libgrail1 libid3tag0 lib32z1
  libmusicbrainz4c2a openoffice.org-common libllvm2.9:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up uml-utilities (20070815-1.3ubuntu1) ...
 * Starting User-mode networking switch uml_switch                       [fail] 
invoke-rc.d: initscript uml-utilities, action "start" failed.
dpkg: error processing uml-utilities (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 uml-utilities
E: Sub-process /usr/bin/dpkg returned an error code (1)
cam@Cam:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up uml-utilities (20070815-1.3ubuntu1) ...
 * Starting User-mode networking switch uml_switch                       [fail] 
invoke-rc.d: initscript uml-utilities, action "start" failed.
dpkg: error processing uml-utilities (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 uml-utilities
E: Sub-process /usr/bin/dpkg returned an error code (1)
cam@Cam:~$ 

Does anyone have a  fix for this?

---

### Post by N64Cam on 2012-09-30
Setting up uml-utilities (20070815-1.3ubuntu1) ...
 * Starting User-mode networking switch uml_switch                                                                        [fail] 
invoke-rc.d: initscript uml-utilities, action "start" failed.

---

### Post by robtygart on 2012-09-30
Try this first ```
sudo apt-get update
sudo apt-get upgrade
```

Why are you doing?? ```
sudo apt-get -f install
```

Also please use the code tags found in Advanced. or by typing [ code ] [ /code ] No spaces..

---

### Post by N64Cam on 2012-09-30
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Bashing-om on 2012-09-30
N64Cam; Hi !

How bout removing the package ?
As it is not installed by default (not on my 12.04, synaptic advises the package is new in the repository) Do you want to try and re-install it ?
This terminal code removes the package and it's config files:
```
sudo apt-get --purge remove uml-utilities
```install:
```
sudo apt-get install uml-utilities
```then I would suggest run:
```
sudo apt-get update
sudo apt-get upgrade
```[INDENT]hth <==BDQ

[/INDENT]

---

### Post by N64Cam on 2012-09-30
Ok so i done everything you told meto but i also get an error like this.
While clicking on ubuntu software center:
Sorry cannot open the software database
Please reinstall the 'software center' package.

 Any solutions?

---

### Post by Bashing-om on 2012-09-30
Allow me to get a handle on what is going on. Please post the output from the terminal command :
```
sudo apt-get update
```
I want to see if there are any errors at this point.
Bear in mind USC is a GUI front end to the lower level package management (apt, for one).

[INDENT]regards <==BDQ

[/INDENT]

---

### Post by N64Cam on 2012-09-30
[code]cam@Cam:~$ sudo apt-get update
[sudo] password for cam: 
Ign http://dl.google.com stable InRelease
Hit http://dl.google.com stable Release.gpg                                    
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Ign http://us.archive.ubuntu.com oneiric-backports InRelease                   
Hit http://dl.google.com stable Release                                        
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg         
Ign http://extras.ubuntu.com oneiric InRelease                                 
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg                 
Hit http://us.archive.ubuntu.com oneiric Release                               
Ign http://security.ubuntu.com oneiric-security InRelease                      
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Hit http://us.archive.ubuntu.com oneiric-backports Release                     
Get:1 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://security.ubuntu.com oneiric-security Release.gpg          
Hit http://us.archive.ubuntu.com oneiric/main Sources                
Hit http://us.archive.ubuntu.com oneiric/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric/universe Sources                      
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources                    
Hit http://us.archive.ubuntu.com oneiric/main amd64 Packages                   
Hit http://us.archive.ubuntu.com oneiric/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/universe amd64 Packages               
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://us.archive.ubuntu.com oneiric/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages                    
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages                
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex                 
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex           
Hit http://extras.ubuntu.com oneiric Release                                   
Hit http://security.ubuntu.com oneiric-security Release                        
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex             
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources         
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources   
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources     
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com oneiric-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com oneiric-updates/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/universe amd64 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages            
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages      
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages        
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://security.ubuntu.com oneiric-security/main Sources                   
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources                
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources          
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources            
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources          
Hit http://extras.ubuntu.com oneiric/main amd64 Packages                       
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric-backports/main amd64 Packages         
Hit http://us.archive.ubuntu.com oneiric-backports/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com oneiric-backports/universe amd64 Packages     
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse amd64 Packages   
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages          
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted Sources   
Hit http://security.ubuntu.com oneiric-security/universe Sources     
Hit http://security.ubuntu.com oneiric-security/multiverse Sources   
Hit http://security.ubuntu.com oneiric-security/main amd64 Packages            
Hit http://security.ubuntu.com oneiric-security/restricted amd64 Packages      
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en   
Hit http://security.ubuntu.com oneiric-security/universe amd64 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse amd64 Packages
Hit http://security.ubuntu.com oneiric-security/main i386 Packages   
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages         
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages       
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en         
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en   
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en     
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Ign http://dl.google.com stable/main Translation-en                  
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Fetched 72 B in 2s (32 B/s)
Reading package lists... Done
cam@Cam:~$ 
[code]

---

### Post by Bashing-om on 2012-09-30
well, The base looks good. Do as the error on clicking software center directs.
```
sudo apt-get --reinstall software-center
sudo apt-get update
sudo apt-get upgrade
```Post back with any errors.[INDENT]tks <==BDQ

[/INDENT]

---

