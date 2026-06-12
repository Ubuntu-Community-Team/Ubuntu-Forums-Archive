---
title: "Cant update since Jan 24th"
date: 2012-02-05
forum: General Help
---

### Post by dannodan2008 on 2012-02-05
Hi guys, My ubuntu has not been able to update since the 24th Jan. I constantly have a red error sign next to my wireless sign. When i run the cursor over it the message reads " The update information is outdated.This may be caused by network problems or a repository that is no longer available.Please update manually by pressing this icon and then select  "check for updates" and check if some of the listed repositories fail " .....
Ok so i do this and the update manager appears and starts to look for an update. The text reads downloading release then update manager is blank with no update and the error sign and message appears again. im worried that my computer is at risk as i cant get the updates. I have been trying to take a screenshot to show you guys the error sign and message but i cant figure out how. I only know the win process.
I need to warn you that i am a complete ubuntu/linux noob. Thanks in advance to anybody who takes the time to read this and can maybe help me .
Regards
Danno

---

### Post by TeoBigusGeekus on 2012-02-05
Open a terminal and post us the output of the following commands:
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by dannodan2008 on 2012-02-05
Hi there and thanks for taking the time to look. the sudo apt-get update gave me the following...
```
danno@danno-laptop:~$ sudo apt-get update
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg [198 B]       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Get:2 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg         
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Get:4 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                               
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex 
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Fetched 666 B in 1s (483 B/s)
Reading package lists... Done
W: GPG error: [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
danno@danno-laptop:~$ ^C
danno@danno-laptop:~$ 
```

And the sudo apt-get upgrade gave me ...

```
danno@danno-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
danno@danno-laptop:~$ 
```

I hope  this is the right info. I have to be honest, i cant make head or tail out of this text.
Regards
Danno

---

### Post by TeoBigusGeekus on 2012-02-05
Try these commands
```
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get update
```

---

### Post by dannodan2008 on 2012-02-05
Hi, I think it has worked. The update manager now reads the package information was just updated. The red error symbol has gone too. Does this mean that i should remember these commands and update like this from now on ? also would you like me to post the text from the terminal ? Thank you ever so much for sorting this out for me .
Regards#
Danno

---

### Post by TeoBigusGeekus on 2012-02-05
No, just copy the commands somewhere, in case it happens again.
If your update is successful, don't forget to mark the thread as solved.

---

