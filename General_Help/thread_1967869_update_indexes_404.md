---
title: "update indexes 404"
date: 2012-04-28
forum: General Help
---

### Post by fisch246 on 2012-04-28
```
paul@thor:/var/lib/apt$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Ign http://us.archive.ubuntu.com precise-backports InRelease
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]
Get:3 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:4 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]
Get:5 http://us.archive.ubuntu.com precise Release [49.6 kB]   
Get:6 http://us.archive.ubuntu.com precise-security Release [49.6 kB]    
Get:7 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:8 http://us.archive.ubuntu.com precise-backports Release [28.9 kB]         
Get:9 http://us.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]      
Get:10 http://us.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]
Get:11 http://us.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]
Ign http://archive.canonical.com precise InRelease                             
Get:12 http://archive.canonical.com precise Release.gpg [198 B]                
Get:13 http://archive.canonical.com precise Release [7,078 B] 
Get:14 http://us.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB] 
Get:15 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:16 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:17 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB] 
Get:18 http://archive.canonical.com precise/partner Sources [3,007 B]         
Get:19 http://archive.canonical.com precise/partner amd64 Packages [3,887 B]  
Get:20 http://archive.canonical.com precise/partner i386 Packages [4,957 B]    
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:21 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:22 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]  
Get:23 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:24 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:25 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:26 http://us.archive.ubuntu.com precise-security/main amd64 Packages [14 B]
Get:27 http://us.archive.ubuntu.com precise-security/restricted amd64 Packages [14 B]
Get:28 http://us.archive.ubuntu.com precise-security/universe amd64 Packages [932 B]
Get:29 http://us.archive.ubuntu.com precise-security/multiverse amd64 Packages [14 B]
Get:30 http://us.archive.ubuntu.com precise-security/main i386 Packages [14 B]
Get:31 http://us.archive.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:32 http://us.archive.ubuntu.com precise-security/universe i386 Packages [920 B]
Get:33 http://us.archive.ubuntu.com precise-security/multiverse i386 Packages [14 B]
Get:34 http://us.archive.ubuntu.com precise-security/main TranslationIndex [70 B]
Get:35 http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex [70 B]
Get:36 http://us.archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:37 http://us.archive.ubuntu.com precise-security/universe TranslationIndex [71 B]
Get:38 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [768 B]
Get:39 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [14 B]
Get:40 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [14 B]
Get:41 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [14 B]
Get:42 http://us.archive.ubuntu.com precise-updates/main i386 Packages [768 B]
Get:43 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [14 B]
Get:44 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [14 B]
Get:45 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [14 B]
Get:46 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [71 B]
Get:47 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [70 B]
Get:48 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [70 B]
Get:49 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [70 B]
Get:50 http://us.archive.ubuntu.com precise-backports/main amd64 Packages [14 B]
Get:51 http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]
Get:52 http://us.archive.ubuntu.com precise-backports/universe amd64 Packages [14 B]
Get:53 http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages [14 B]
Get:54 http://us.archive.ubuntu.com precise-backports/main i386 Packages [14 B]
Get:55 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:56 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [14 B]
Get:57 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [14 B]
Get:58 http://us.archive.ubuntu.com precise-backports/main TranslationIndex [70 B]
Get:59 http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex [70 B]
Get:60 http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:61 http://us.archive.ubuntu.com precise-backports/universe TranslationIndex [70 B]
Get:62 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:63 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:64 http://us.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:65 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB] 
Err http://us.archive.ubuntu.com precise/main Sources                          
  404  Not Found
Err http://us.archive.ubuntu.com precise/restricted Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise/universe Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise/multiverse Sources
  404  Not Found
Get:66 http://us.archive.ubuntu.com precise-security/main Translation-en [14 B]
Get:67 http://us.archive.ubuntu.com precise-security/multiverse Translation-en [14 B]
Get:68 http://us.archive.ubuntu.com precise-security/restricted Translation-en [14 B]
Get:69 http://us.archive.ubuntu.com precise-security/universe Translation-en [305 B]
Get:70 http://us.archive.ubuntu.com precise-updates/main Translation-en [538 B]
Get:71 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [14 B]
Get:72 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [14 B]
Get:73 http://us.archive.ubuntu.com precise-updates/universe Translation-en [14 B]
Get:74 http://us.archive.ubuntu.com precise-backports/main Translation-en [14 B]
Get:75 http://us.archive.ubuntu.com precise-backports/multiverse Translation-en [14 B]
Get:76 http://us.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]
Get:77 http://us.archive.ubuntu.com precise-backports/universe Translation-en [14 B]
Err http://us.archive.ubuntu.com precise-security/main Sources                 
  404  Not Found
Err http://us.archive.ubuntu.com precise-security/restricted Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-security/universe Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-security/multiverse Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-updates/main Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-updates/restricted Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-updates/universe Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-updates/multiverse Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-backports/main Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-backports/restricted Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-backports/universe Sources
  404  Not Found
Err http://us.archive.ubuntu.com precise-backports/multiverse Sources
  404  Not Found
Ign http://archive.canonical.com precise/partner Translation-en_US
Ign http://archive.canonical.com precise/partner Translation-en
Fetched 16.8 MB in 7s (2,227 kB/s)                                             
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/restricted/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/universe/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/main/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/restricted/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/universe/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-security/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/main/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/restricted/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/universe/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-updates/multiverse/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/main/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/restricted/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/universe/source/Sources  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/precise-backports/multiverse/source/Sources  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Anyone have any idea on how to get the right indexes? I installed by Live USB. I looked all over, couldn't find anything that worked. I even did the "apt-get clean" method. I also did the "apt-get dist-upgrade" method. I just need to figure out how to get the correct indexes.

---

### Post by fisch246 on 2012-04-29
Not sure if it was an issue with the network I was on or what. However once I changed to kernel.org it worked perfectly. I changed around to several different servers already. However kernel.org seemed to work just fine. Yea so no worries I DID try changing servers about 3 different times before I posted this. I'll mark it as solved now.

---

