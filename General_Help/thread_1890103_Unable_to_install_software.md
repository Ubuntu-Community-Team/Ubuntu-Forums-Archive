---
title: "Unable to install software"
date: 2011-12-02
forum: General Help
---

### Post by rmcellig on 2011-12-02
For some reason I am unable to install software from the software installer. I keep getting this message even after restarting my computer. I can't see any open apps that might be causing this problem. What should I do?

---

### Post by staf0048 on 2011-12-02
Have a look here:  [http://freshtutorial.com/solve-unable-lock-administration-directory-varlibdpkg/](http://freshtutorial.com/solve-unable-lock-administration-directory-varlibdpkg/)

Hope this solves your issue!

---

### Post by matt_symes on 2011-12-03
Hi

You can try to see what has a lock on the dpkg lock file with

```
sudo lsof /var/lib/dpkg/lock
```

Post back results if the other tutorial did not work for you.

Kind regards

---

### Post by rmcellig on 2011-12-06
Doesn't seem to do anything.


randy@randy-Dimension-3000:~$ sudo lsof /var/lib/dpkg/lock
[sudo] password for randy: 
randy@randy-Dimension-3000:~$ sudo lsof /var/lib/dpkg/lock
randy@randy-Dimension-3000:~$ 


I still can't install using the Muon Software Center

---

### Post by rmcellig on 2011-12-06
I'm starting to think this is  a problem with the latest Kubuntu because it is  happening on two seperate machines that I tried it on.

---

### Post by matt_symes on 2011-12-06
Hi

Nothing seems to have a lock on the dpkg lock file. Open a terminal and type

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen.

If that works with no errors try

```
sudo apt-get install htop
```

Post the results back here if there are any errors.

Kind regards

---

### Post by rmcellig on 2011-12-06
This  is  the output after typing in the code:


<code>
randy@randy-Dimension-3000:~$ sudo apt-get update
[sudo] password for randy: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports Release.gpg        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources         
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates Release [32.4 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe TranslationIndex   
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Sources [94.3 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_CA          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en 
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Sources [1,348 B]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Sources [25.8 kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Sources [1,992 B]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main i386 Packages [219 kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,935 B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe i386 Packages [64.1 kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [4,396 B]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en_CA                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Translation-en               
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Translation-en [99.4 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Translation-en [39.8 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 586 kB in 9s (64.9 kB/s)                                               
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
randy@randy-Dimension-3000:~$ sudo apt-get install htop
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
randy@randy-Dimension-3000:~$ 


<code/>

---

### Post by oldtimer7777 on 2011-12-06
Run from terminal:

sudo dpkg --configure -a

> **rmcellig said:**
> This  is  the output after typing in the code:


<code>
randy@randy-Dimension-3000:~$ sudo apt-get update
[sudo] password for randy: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports Release.gpg        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources         
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates Release [32.4 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe TranslationIndex   
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Sources [94.3 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_CA          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en 
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Sources [1,348 B]
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Sources [25.8 kB]
Get:7 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Sources [1,992 B]
Get:8 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main i386 Packages [219 kB]
Get:9 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,935 B]
Get:10 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe i386 Packages [64.1 kB]
Get:11 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [4,396 B]
Get:12 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:13 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:14 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:15 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en_CA                
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric/universe Translation-en               
Get:16 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/main Translation-en [99.4 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:17 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-updates/universe Translation-en [39.8 kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 586 kB in 9s (64.9 kB/s)                                               
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
randy@randy-Dimension-3000:~$ sudo apt-get install htop
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
randy@randy-Dimension-3000:~$ 


<code/>

---

### Post by rmcellig on 2011-12-06
Seems to work fine now. Dropbox was the issue.

---

