---
title: "help"
date: 2012-05-26
forum: General Help
---

### Post by xdweaver on 2012-05-26
I entered the command 
sudo apt-get install kde-full, it was all working fine then a window opened with some options, but froze at that point.I restarted the computer and am trying to reinstall it and get this error message, daniel@daniel-HP-Pavilion-dv5-Notebook-PC:~$     sudo apt-get install kde-full
[sudo] password for daniel: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
daniel@daniel-HP-Pavilion-dv5-Notebook-PC:~$ sudo dpkg--configure -a
sudo: dpkg--configure: command not found
daniel@daniel-HP-Pavilion-dv5-Notebook-PC:~$ sudo dpkg-a
sudo: dpkg-a: command not found
daniel@daniel-HP-Pavilion-dv5-Notebook-PC:~$ sudo dpkg
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
daniel@daniel-HP-Pavilion-dv5-Notebook-PC:~$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports InRelease         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release.gpg [198 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main amd64 Packages                       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports Release [49.6 kB]         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]         
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [12.6 kB]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [4,522 B] 
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [696 B]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main amd64 Packages [42.8 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted amd64 Packages [14 B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe amd64 Packages [10.3 kB]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse amd64 Packages [1,142 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [43.9 kB]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [10.3 kB]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,393 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en      
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                    
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
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [46.6 kB]     
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [13.4 kB] 
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [696 B] 
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main amd64 Packages [118 kB]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted amd64 Packages [2,417 B]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe amd64 Packages [36.0 kB]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse amd64 Packages [1,142 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [120 kB]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [36.5 kB]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [1,393 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Sources [700 B]     
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Sources [14 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Sources [3,490 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Sources [14 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main amd64 Packages [559 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted amd64 Packages [14 B]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe amd64 Packages [2,656 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse amd64 Packages [14 B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main i386 Packages [559 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted i386 Packages [14 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe i386 Packages [2,653 B]
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse i386 Packages [14 B]
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
Fetched 19.2 MB in 23s (818 kB/s)                                              
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
daniel@daniel-HP-Pavilion-dv5-Notebook-PC:~$ 



How do i fix this?

---

### Post by m_duck on 2012-05-26
You need to run ```
sudo dpkg --configure -a
```Note the space between ***dpkg*** and ***--configure***. This results in ***--configure*** being passed to the ***dpkg*** program as an option, rather than trying to run the non-existent ***dpkg--configure***.

---

