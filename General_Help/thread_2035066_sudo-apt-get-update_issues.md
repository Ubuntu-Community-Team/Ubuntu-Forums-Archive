---
title: "sudo-apt-get-update issues"
date: 2012-07-29
forum: General Help
---

### Post by spunkycabage11 on 2012-07-29
I keep getting the error E: Some index files failed to download. They have been ignored, or old ones used instead, whenever i run sudo apt-get. I'm running ubuntu 12.04 Here is the terminal session:

burhan@epsilon:~$ sudo apt-get update
[sudo] password for burhan: 
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_GB
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_GB
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease                     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                    
Get:1 [http://www.plexapp](http://www.plexapp) beta InRelease [1,042 B]                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
Ign [http://www.plexapp](http://www.plexapp) beta InRelease                                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                     
Get:2 [http://www.plexapp](http://www.plexapp) beta/main i386 Packages [1,090 B]                     
Hit [http://www.plexapp.com](http://www.plexapp.com) lucid InRelease                                     
99% [2 Packages bzip2 0 B] [Release gpgv 49.6 kB] [Waiting for headers] [Connecbzip2: (stdin) is not a bzip2 file.
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                          
Get:3 [http://www.plexapp](http://www.plexapp) beta/main TranslationIndex [1,062 B]                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
67% [2 Packages xz 0 B] [InRelease gpgv 2,146 B] [Waiting for headers] [Waiting/usr/bin/xz: (stdin): File format not recognised
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Err [http://www.plexapp](http://www.plexapp) beta/main i386 Packages                                 
  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en
68% [2 Packages lzma 0 B] [Waiting for headers] [Waiting for headers] [Waiting /usr/bin/lzma: (stdin): File format not recognised
Err [http://www.plexapp](http://www.plexapp) beta/main i386 Packages                                 
  
Hit [http://www.plexapp.com](http://www.plexapp.com) lucid/main i386 Packages                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_GB                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en
Ign [http://www.plexapp.com](http://www.plexapp.com) lucid/main TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Ign [http://www.plexapp.com](http://www.plexapp.com) lucid/main Translation-en_GB
Ign [http://www.plexapp.com](http://www.plexapp.com) lucid/main Translation-en
Fetched 3,194 B in 2s (1,286 B/s)
W: GPG error: [http://www.plexapp](http://www.plexapp) beta InRelease: File /var/lib/apt/lists/partial/www.plexapp_repo_dists_beta_InRelease doesn't start with a clearsigned message
W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch gzip:/var/lib/apt/lists/partial/www.plexapp_repo_dists_beta_main_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch [http://www.plexapp/repo/dists/beta/main/i18n/Index](http://www.plexapp/repo/dists/beta/main/i18n/Index)  No Hash entry in Release file /var/lib/apt/lists/partial/www.plexapp_repo_dists_beta_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Cheesehead on 2012-07-29
You have two problems.

> Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise InRelease
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise Release.gpg
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise Release
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main TranslationIndex
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted TranslationIndex
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main i386 Packages
Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted i386 Packages
Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en_GB
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/main Translation-en
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en_GB
Ign cdrom://Ubuntu 12.04 LTS _Precise Pangolin_ - Release i386 (20120423) precise/restricted Translation-en
It's trying to update from your CD drive. You probably want to comment those out by adding a # in front.

> Get:1 [http://www.plexapp](http://www.plexapp) beta InRelease [1,042 B]
Ign [http://www.plexapp](http://www.plexapp) beta InRelease
Get:2 [http://www.plexapp](http://www.plexapp) beta/main i386 Packages [1,090 B]
Hit [http://www.plexapp.com](http://www.plexapp.com) lucid InRelease
99% [2 Packages bzip2 0 B] [Release gpgv 49.6 kB] [Waiting for headers] [Connecbzip2: (stdin) is not a bzip2 file.
Get:3 [http://www.plexapp](http://www.plexapp) beta/main TranslationIndex [1,062 B]
Err [http://www.plexapp](http://www.plexapp) beta/main i386 Packages
Err [http://www.plexapp](http://www.plexapp) beta/main i386 Packages
Hit [http://www.plexapp.com](http://www.plexapp.com) lucid/main i386 Packages
Ign [http://www.plexapp.com](http://www.plexapp.com) lucid/main TranslationIndex
Ign [http://www.plexapp.com](http://www.plexapp.com) lucid/main Translation-en_GB
Ign [http://www.plexapp.com](http://www.plexapp.com) lucid/main Translation-en
Be careful with third-party repos. Be sure you remember why you added them, and delete them when their utility is past. For example, you have a bunch of Lucid repos here instead of Precise. Mixing releases like that can break your system.

You probably want to comment out the old lines.

---

### Post by spunkycabage11 on 2012-07-30
Thanks for your help, im kind of a novice at this stuff so could you tell me how to comment those lines out and how to replace the lucid repos?

EDIT: Never mind, i figured it out, just had to edit my source.list file. Thanks man, you helped a lot.

---

### Post by Lyfang on 2012-07-30
Novice users may run at their own risk (as usual):
```
gksudo gedit /etc/apt/sources.list
```

---

