---
title: "Update Manager wont let me update, and i can't install Openjdk"
date: 2011-10-08
forum: General Help
---

### Post by Acutical on 2011-10-08
I am running Ubuntu 11.10 Beta 2.

I have 11.04 on another PC, and have the same issue.

I've tried switching to the main server, still, no luck.

sudo apt-get update error:
```
acutical@Ronnie-PC:~$ sudo apt-get update
[sudo] password for acutical: 
Ign http://archive.canonical.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease
Hit http://archive.canonical.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://archive.canonical.com oneiric Release
Hit http://extras.ubuntu.com oneiric Release                          
Hit http://archive.canonical.com oneiric/partner i386 Packages        
Hit http://extras.ubuntu.com oneiric/main Sources
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Ign http://archive.ubuntu.com oneiric-backports InRelease            
Ign http://archive.ubuntu.com oneiric-security InRelease
Hit http://archive.ubuntu.com oneiric Release.gpg
Hit http://archive.ubuntu.com oneiric-updates Release.gpg
Hit http://archive.ubuntu.com oneiric-backports Release.gpg          
Hit http://archive.ubuntu.com oneiric-security Release.gpg           
Hit http://archive.ubuntu.com oneiric Release                        
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://archive.ubuntu.com oneiric-backports Release                        
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources               
Hit http://archive.ubuntu.com oneiric/multiverse Sources             
Hit http://archive.ubuntu.com oneiric/main i386 Packages             
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages       
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages       
Ign http://archive.ubuntu.com oneiric/main TranslationIndex          
Ign http://archive.ubuntu.com oneiric/multiverse TranslationIndex    
Ign http://archive.ubuntu.com oneiric/restricted TranslationIndex    
Ign http://archive.ubuntu.com oneiric/universe TranslationIndex      
Hit http://archive.ubuntu.com oneiric-updates/main Sources           
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources     
Hit http://archive.ubuntu.com oneiric-updates/universe Sources       
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources     
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages     
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages 
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Ign http://archive.ubuntu.com oneiric-updates/main TranslationIndex  
Ign http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Ign http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Ign http://archive.canonical.com oneiric/partner Translation-en      
Hit http://archive.ubuntu.com oneiric-backports/main Sources         
Hit http://archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://archive.ubuntu.com oneiric-backports/universe Sources
Ign http://extras.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Ign http://archive.ubuntu.com oneiric-backports/main TranslationIndex
Ign http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Ign http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Ign http://archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/main Sources
Hit http://archive.ubuntu.com oneiric-security/restricted Sources
Hit http://archive.ubuntu.com oneiric-security/universe Sources
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://archive.ubuntu.com oneiric-security/main TranslationIndex
Ign http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Get:1 http://archive.ubuntu.com oneiric/universe i386 Packages [5,771 kB]
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Get:2 http://archive.ubuntu.com oneiric/universe Translation-en [3,166 kB]
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en              
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Ign http://archive.ubuntu.com oneiric/main Translation-en_US                   
Ign http://archive.ubuntu.com oneiric/multiverse Translation-en_US             
Ign http://archive.ubuntu.com oneiric/restricted Translation-en_US             
Ign http://archive.ubuntu.com oneiric/universe Translation-en_US               
Ign http://archive.ubuntu.com oneiric-updates/main Translation-en_US           
Ign http://archive.ubuntu.com oneiric-updates/multiverse Translation-en_US     
Ign http://archive.ubuntu.com oneiric-updates/restricted Translation-en_US     
Ign http://archive.ubuntu.com oneiric-updates/universe Translation-en_US       
Ign http://archive.ubuntu.com oneiric-backports/main Translation-en_US         
Ign http://archive.ubuntu.com oneiric-backports/main Translation-en            
Ign http://archive.ubuntu.com oneiric-backports/multiverse Translation-en_US   
Ign http://archive.ubuntu.com oneiric-backports/multiverse Translation-en      
Ign http://archive.ubuntu.com oneiric-backports/restricted Translation-en_US   
Ign http://archive.ubuntu.com oneiric-backports/restricted Translation-en      
Ign http://archive.ubuntu.com oneiric-backports/universe Translation-en_US     
Ign http://archive.ubuntu.com oneiric-backports/universe Translation-en        
Ign http://archive.ubuntu.com oneiric-security/main Translation-en_US          
Ign http://archive.ubuntu.com oneiric-security/main Translation-en             
Ign http://archive.ubuntu.com oneiric-security/multiverse Translation-en_US    
Ign http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Ign http://archive.ubuntu.com oneiric-security/restricted Translation-en_US    
Ign http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Ign http://archive.ubuntu.com oneiric-security/universe Translation-en_US      
Ign http://archive.ubuntu.com oneiric-security/universe Translation-en         
Fetched 3,166 kB in 31s (101 kB/s)                                             
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Any advice? :(

---

### Post by Acutical on 2011-10-08
Help me, please? :(

---

### Post by drs305 on 2011-10-09
Try this:
Open Software Sources. Go to the Ubuntu tab and untick the 'universe' repository, then close it and run the second command. 
Open Software Sources:
```
gksu software-properties-gtk
sudo apt-get update
```
You may be able to install what you want, but either way repeat the commands afterward and reselect 'universe' and update again.

You could also try changing servers in Software Sources just to make sure the problem isn't with the server's list.

---

### Post by drs305 on 2011-10-09
You could also just try to clean up the folder with:
```
sudo apt-get clean
sudo dpkg --clear-avail
```

If neither of these work, you could try opening nautilus as root and moving the problem list somewhere else (such as your Desktop):
```
gksu nautilus /var/lib/apt/lists/partial/
```
File to move:
*archive.ubuntu.com_ubuntu_dists_oneiric_universe_binary-i386_Packages*

---

### Post by Acutical on 2011-10-09
Thanks! :D That fixed it!

---

