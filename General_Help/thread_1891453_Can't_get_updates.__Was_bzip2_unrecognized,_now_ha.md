---
title: "Can't get updates.  Was bzip2 unrecognized, now hash error"
date: 2011-12-05
forum: General Help
---

### Post by brons2 on 2011-12-05
Here is what I get from a 'sudo apt-get update'
I've been searching the web and trying some different things but so far I've not gotten it working.


```

jim@10:~$ sudo apt-get update
Ign http://dl.google.com stable InRelease
Get:1 http://dl.google.com stable Release.gpg [198 B]               
Get:2 http://archive.canonical.com oneiric InRelease [11.4 kB]                 
Ign http://us.archive.ubuntu.com oneiric InRelease                             
Ign http://extras.ubuntu.com oneiric InRelease                       
Get:3 http://dl.google.com stable Release [1347 B]                   
Ign http://archive.canonical.com oneiric InRelease                        
Ign http://us.archive.ubuntu.com oneiric-updates InRelease                     
Hit http://extras.ubuntu.com oneiric Release.gpg                               
Ign http://us.archive.ubuntu.com oneiric-security InRelease          
Hit http://extras.ubuntu.com oneiric Release                         
Get:4 http://archive.canonical.com oneiric/partner i386 Packages [11.4 kB]     
Hit http://us.archive.ubuntu.com oneiric Release.gpg                           
99% [4 Packages bzip2 0 B] [Waiting for headers] [Waiting for headers] [Waitingbzip2: (stdin) is not a bzip2 file.
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg                   
Get:5 http://dl.google.com stable/main i386 Packages [1207 B]                  
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Hit http://us.archive.ubuntu.com oneiric-security Release.gpg                  
Ign http://dl.google.com stable/main TranslationIndex                          
Get:6 http://archive.canonical.com oneiric/partner TranslationIndex [11.4 kB]  
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Hit http://us.archive.ubuntu.com oneiric Release                     
Hit http://us.archive.ubuntu.com oneiric-updates Release                       
Ign http://dl.google.com stable/main Translation-en                            
Hit http://us.archive.ubuntu.com oneiric-security Release                      
69% [4 Packages xz 0 B] [Release gpgv 32.4 kB] [Waiting for headers] [Waiting f/usr/bin/xz: (stdin): File format not recognized
Err http://archive.canonical.com oneiric/partner i386 Packages                 
  
Hit http://us.archive.ubuntu.com oneiric/main Sources                          
Hit http://us.archive.ubuntu.com oneiric/restricted Sources                    
Hit http://us.archive.ubuntu.com oneiric/universe Sources            
Ign http://extras.ubuntu.com oneiric/main Translation-en
69% [4 Packages lzma 0 B] [Waiting for headers]/usr/bin/lzma: SetDecoderProperties() error
Err http://archive.canonical.com oneiric/partner i386 Packages
  
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/main Sources
Hit http://us.archive.ubuntu.com oneiric-security/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-security/universe Sources
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en             
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en               
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en           
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en       
Hit http://us.archive.ubuntu.com oneiric-security/main Translation-en          
Hit http://us.archive.ubuntu.com oneiric-security/multiverse Translation-en    
Hit http://us.archive.ubuntu.com oneiric-security/restricted Translation-en    
Hit http://us.archive.ubuntu.com oneiric-security/universe Translation-en      
Fetched 36.9 kB in 7s (5059 B/s)                                               
W: GPG error: http://archive.canonical.com oneiric InRelease: File /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_InRelease doesn't start with a clearsigned message
W: Failed to fetch gzip:/var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/archive.canonical.com_ubuntu_dists_oneiric_partner_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by brons2 on 2011-12-05
OK so I went into Synaptic and unchecked everything but Canonical supported software and updates from Oneiric only.  Then I started update manager and it wanted to do a partial upgrade, I said NO and then started the normal update process.  It's running now.  We'll see what happens...

---

### Post by brons2 on 2011-12-05
Things seemed to be working better, so I went back in and started re-checking repositories in Synaptic.  Universe worked fine and after I did that it had more updates and stopped bugging me for partial upgrade.  Re-enabling the repository under Other Software for Google Chrome also worked fine.

However, when I enabled Canonical Partners, it broke Update Manager again.  It says that it was added by software-center and that it is Software packaged by Canonical for their partners.  Seems like it would be OK but it's not.  Do I not need this source any longer?  I'm gonna leave it unchecked for now.

---

### Post by brons2 on 2011-12-05
Was also able to re-enable restricted and multiverse.  Guess I don't really need anything else.  I suppose this is what I get for upgrading rather than doing a clean install :)

---

