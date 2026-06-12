---
title: "Update issues"
date: 2012-04-24
forum: General Help
---

### Post by lbennett125 on 2012-04-24
I'm not exactly a new user to ubuntu, but I would say I am a bit of a novice, and I have been having trouble updating using the updater, so I tried doing it through the terminal, and received this message:



:/var/lib/apt$ sudo apt-get update
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                      
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease                  
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg [198 B]                
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]      
Get:4 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg [198 B]              
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                        
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security Release.gpg [198 B]  
Get:7 [http://archive.canonical.com](http://archive.canonical.com) oneiric Release [5,922 B]                              
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release [40.8 kB]                        
Get:9 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources [2,617 B]                    
Get:10 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [877 kB]                                  
Get:11 [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages [4,333 B]            
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex                              
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release [40.8 kB]                          
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security Release [40.8 kB]                         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                                     
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [1,226 kB]           
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources [5,351 B]                    
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]                     
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_GB                             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en                
Get:17 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en [861 kB]                           
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB                                    
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources [877 kB]                              
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]                        
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B]                 
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]                  
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]                      
Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]                  
Get:24 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex [3,289 B]                    
Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex [2,265 B]              
Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex [2,263 B]              
Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]                
Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources [2,864 B]               
Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources [50.1 kB]                 
Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources [50.1 kB]                 
Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources [136 kB]                      
99% [30 Sources bzip2 0 B] [31 Sources 919 B/136 kB 0%]                             466 kB/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,652 B]               
Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [6,268 B]         
Get:34 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages [109 kB]            
Get:35 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages [318 kB]                
Get:36 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,358 B]         
Get:37 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]               
Get:38 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]         
Get:39 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [72 B]         
Get:40 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]           
Get:41 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted Sources [1,959 B]              
Get:42 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe Sources [13.8 kB]                
Get:43 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main Sources [36.6 kB]                    
Get:44 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse Sources [1,646 B]              
Get:45 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted i386 Packages [3,939 B]        
Get:46 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe i386 Packages [32.4 kB]          
Get:47 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main i386 Packages [97.9 kB]              
Get:48 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse i386 Packages [3,372 B]        
Get:49 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main TranslationIndex [73 B]              
Get:50 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]        
Get:51 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted TranslationIndex [71 B]        
Get:52 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]          
Get:53 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB [69.0 kB]                   
Get:54 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en [701 kB]                       
Get:55 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB [68.5 kB]             
Get:56 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]                
Get:57 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB [1,937 B]             
Get:58 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]                
Get:59 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB [4,365 B]               
Get:60 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB]                 
Get:61 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en [149 kB]               
Get:62 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [3,524 B]        
Get:63 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en [1,304 B]        
Get:64 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en [65.5 kB]          
Get:65 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/main Translation-en [54.3 kB]             
Get:66 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/multiverse Translation-en [1,494 B]       
Get:67 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/restricted Translation-en [978 B]         
Get:68 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-security/universe Translation-en [23.0 kB]         
Fetched 19.8 MB in 1min 6s (297 kB/s)                                                          
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/gb.archive.ubuntu.com_ubuntu_dists_oneiric-updates_universe_source_Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


I have tried unselecting certain sources in the Other Software section in the Software sources, but it hasn't helped.

Any suggestions or help would be very much appreciated.

---

### Post by plucky on 2012-04-24
Be careful with updates as the GB Servers are being hammered at the moment.

My updates were downloading at 36Kb/s today when normally it is 716kb/s.

Perhaps getting ready for the new release.

Good Luck

---

### Post by lbennett125 on 2012-04-26
Hey again, thanks for the advice, but I have seen no difference in the last couple of days, evening changing the server location made no difference.

If I use the update manager, I still get something say check you internet connection and this error message:

W:Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Hash Sum mismatch
, W:Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

