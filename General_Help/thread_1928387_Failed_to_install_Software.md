---
title: "Failed to install Software"
date: 2012-02-20
forum: General Help
---

### Post by Fayaz427 on 2012-02-20
Hello Everyone.....
Iam unable to install any software from ubuntu Software center...
It is giving error message as "Failed to install package...check your internet connection...
and then another error "requires installaton of untrusted packages....The action would require the installation of packages from not authenticated sources"
iam using ubuntu 11.10...
What might be the problem...
this is the second time iam facing the same problem....
previously it was solved by using "sudo apt-get update" command...
but this time it is not working...
Please help me...
Thanks for help in advance....

---

### Post by Fayaz427 on 2012-02-20
Iam still waiting for your help...

---

### Post by cortman on 2012-02-20
Run

```
sudo apt-get update
```

And post the results.

---

### Post by Fayaz427 on 2012-02-21
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric InRelease                   
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates InRelease           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports InRelease         
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]          
Get:2 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]                 
Get:3 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release.gpg [198 B]       
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]            
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
  
Get:6 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]         
Get:7 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release                               
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release                               
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release [40.8 kB]           
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [29.7 kB]       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages/DiffIndex       
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release                     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]   
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [11.4 kB]  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources/DiffIndex            
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Sources [125 kB]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,645 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [81.0 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_IN             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Sources [1,337 B]
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Sources [44.2 kB] 
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [29.7 kB]
Get:19 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,662 B]
Get:20 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main i386 Packages [290 kB]
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main i386 Packages [290 kB]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,355 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [43.9 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,968 B]
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe i386 Packages [97.7 kB]
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,355 B]
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Sources/DiffIndex      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Sources/DiffIndex  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Sources/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe i386 Packages/DiffIndex
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages/DiffIndex
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Translation-en               
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Translation-en [135 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Translation-en [58.5 kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Translation-en     
Fetched 1,048 kB in 48s (21.7 kB/s)                                            
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead

---

### Post by cortman on 2012-02-21
Hi, looks like key signing problems. Rather than repeat what's already been given, I will direct you to [this thread]("http://ubuntuforums.org/archive/index.php/t-1865223.html") from the forum archives. Run the commands given in the second post, and post back if it still needs work.
Good luck!

---

### Post by Fayaz427 on 2012-02-22
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Fayaz427 on 2012-02-22
still same errors

---

### Post by roelforg on 2012-02-22
Try this (from the thread cortman referred to):
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3E5C1192 437D05B5
sudo apt-get update

```

---

### Post by Fayaz427 on 2012-02-22
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by roelforg on 2012-02-22
Which version are you using?

---

### Post by cortman on 2012-02-22
> **Fayaz427 said:**
> W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This didn't work because you still have an apt or dpkg process running. Open a terminal and run

```
sudo killall -9 *apt*
sudo killall -9 *dpkg*
```

to end all such processes, then try again.

---

### Post by raja.genupula on 2012-02-22
if anything regrading your GPG won't help then do this 
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
```

All the best fayaz.

---

### Post by Fayaz427 on 2012-02-23
Ubuntu 11.10 Oneiric Ocelot

---

### Post by Fayaz427 on 2012-02-23
> Originally Posted by raja.genupula
if anything regrading your GPG won't help then do this 
Code:
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
All the best fayaz.
________________
this helped me.....
now everything is fine...
thanking everyone....

---

### Post by cortman on 2012-02-23
Great! Mark this thread as [SOLVED], please, using the thread tools in the upper right.
Enjoy Ubuntu!

---

