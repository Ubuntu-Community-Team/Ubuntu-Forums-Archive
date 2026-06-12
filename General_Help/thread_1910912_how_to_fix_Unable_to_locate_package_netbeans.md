---
title: "how to fix: Unable to locate package netbeans"
date: 2012-01-18
forum: General Help
---

### Post by emab on 2012-01-18
I'm trying to install netbeans in my ubuntu desktop, but I get the following error:
```
# apt-get install netbeans
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netbeans
```A week ago I had the following problem that automatically was solved: [http://ubuntuforums.org/showthread.php?t=1907332](http://ubuntuforums.org/showthread.php?t=1907332)

Can anybody help me please?
thanks

---

### Post by raja.genupula on 2012-01-18
[http://netbeans.org/downloads/index.html](http://netbeans.org/downloads/index.html)


If your required package not available then you will get such error , download netbeans from that link . look in your software center once . I hope you can find there . its easy way to install .

All the best

---

### Post by emab on 2012-01-18
The problem is that for every program I get the same error! What should I do to use apt-get?

---

### Post by raja.genupula on 2012-01-18
HI please give me the output of 
sudo apt-get update if you got any errors . If you got no errors then do the installation command again from the terminal or open software center and try again . 

All the best .

---

### Post by emab on 2012-01-19
> **raja.genupula said:**
> HI please give me the output of 
sudo apt-get update if you got any errors . If you got no errors then do the installation command again from the terminal or open software center and try again . 

All the best .

of course it's here:

```
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://extras.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease
Ign http://ir.archive.ubuntu.com oneiric InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Get:1 http://archive.ubuntu.com oneiric Release.gpg [198 B]
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]
Get:3 http://archive.canonical.com oneiric Release.gpg [198 B]
Ign http://ir.archive.ubuntu.com oneiric-updates InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Ign http://ir.archive.ubuntu.com oneiric-backports InRelease
Hit http://security.ubuntu.com oneiric-security Release
Hit http://archive.ubuntu.com oneiric Release
Hit http://extras.ubuntu.com oneiric Release
Hit http://archive.canonical.com oneiric Release
Get:4 http://ir.archive.ubuntu.com oneiric Release.gpg [198 B]
Ign http://archive.ubuntu.com oneiric Release
Ign http://archive.canonical.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Ign http://archive.ubuntu.com oneiric/main Sources/DiffIndex
Hit http://extras.ubuntu.com oneiric/main Sources
Get:5 http://ir.archive.ubuntu.com oneiric-updates Release.gpg [198 B]
Hit http://security.ubuntu.com oneiric-security/main Sources
Ign http://archive.ubuntu.com oneiric/restricted Sources/DiffIndex
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Get:6 http://ir.archive.ubuntu.com oneiric-backports Release.gpg [198 B]
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://archive.ubuntu.com oneiric/main Sources
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe Sources
Ign http://archive.canonical.com oneiric/partner Sources/DiffIndex
Get:7 http://archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Err http://archive.ubuntu.com oneiric/restricted Sources
  
Hit http://ir.archive.ubuntu.com oneiric Release
Ign http://ir.archive.ubuntu.com oneiric Release
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Ign http://archive.canonical.com oneiric/partner i386 Packages/DiffIndex
Get:8 http://ir.archive.ubuntu.com oneiric-updates Release [40.8 kB]
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Err http://archive.ubuntu.com oneiric/restricted Sources
  
Get:9 http://archive.canonical.com oneiric/partner Sources [2,255 B]
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Err http://archive.ubuntu.com oneiric/restricted Sources
  
Get:10 http://archive.canonical.com oneiric/partner i386 Packages [3,943 B]
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Err http://archive.ubuntu.com oneiric/restricted Sources
  
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Hit http://ir.archive.ubuntu.com oneiric-backports Release
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Ign http://ir.archive.ubuntu.com oneiric-backports Release
Err http://archive.ubuntu.com oneiric/restricted Sources
  404  Not Found [IP: 91.189.92.170 80]
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Get:11 http://ir.archive.ubuntu.com oneiric/restricted Sources [5,351 B]
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://ir.archive.ubuntu.com oneiric/main Sources/DiffIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://ir.archive.ubuntu.com oneiric/multiverse Sources/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric/universe Sources/DiffIndex
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Ign http://ir.archive.ubuntu.com oneiric/main i386 Packages/DiffIndex
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Ign http://ir.archive.ubuntu.com oneiric/multiverse i386 Packages/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric/restricted i386 Packages/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric/universe i386 Packages/DiffIndex
Get:12 http://ir.archive.ubuntu.com oneiric/main TranslationIndex [3,289 B]
Get:13 http://ir.archive.ubuntu.com oneiric/multiverse TranslationIndex [2,265 B]
Get:14 http://ir.archive.ubuntu.com oneiric/restricted TranslationIndex [2,263 B]
Get:15 http://ir.archive.ubuntu.com oneiric/universe TranslationIndex [2,640 B]
Err http://archive.canonical.com oneiric/partner Sources
  404  Not Found
Err http://archive.canonical.com oneiric/partner i386 Packages
  404  Not Found
Get:16 http://ir.archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Get:17 http://ir.archive.ubuntu.com oneiric-updates/main Sources [113 kB]
Ign http://archive.canonical.com oneiric/partner Translation-en
Get:18 http://ir.archive.ubuntu.com oneiric-updates/multiverse Sources [3,654 B]
Get:19 http://ir.archive.ubuntu.com oneiric-updates/universe Sources [37.9 kB]
Get:20 http://ir.archive.ubuntu.com oneiric-updates/main i386 Packages [259 kB]
Get:21 http://ir.archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:22 http://ir.archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,332 B]
Get:23 http://ir.archive.ubuntu.com oneiric-updates/universe i386 Packages [86.0 kB]
Get:24 http://ir.archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]
Get:25 http://ir.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:26 http://ir.archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:27 http://ir.archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Get:28 http://ir.archive.ubuntu.com oneiric-backports/main Sources [1,577 B]
Ign http://ir.archive.ubuntu.com oneiric-backports/restricted Sources/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric-backports/universe Sources/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric-backports/multiverse Sources/DiffIndex
Get:29 http://ir.archive.ubuntu.com oneiric-backports/main i386 Packages [1,912 B]
Ign http://ir.archive.ubuntu.com oneiric-backports/restricted i386 Packages/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric-backports/universe i386 Packages/DiffIndex
Ign http://ir.archive.ubuntu.com oneiric-backports/multiverse i386 Packages/DiffIndex
Hit http://ir.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://ir.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://ir.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://ir.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://ir.archive.ubuntu.com oneiric/main Sources
Hit http://ir.archive.ubuntu.com oneiric/multiverse Sources
Hit http://ir.archive.ubuntu.com oneiric/universe Sources
Hit http://ir.archive.ubuntu.com oneiric/main i386 Packages
Hit http://ir.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://ir.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://ir.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://ir.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://ir.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://ir.archive.ubuntu.com oneiric-updates/restricted Translation-en
Get:30 http://ir.archive.ubuntu.com oneiric-updates/universe Translation-en [52.3 kB]
Hit http://ir.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://ir.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://ir.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://ir.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://ir.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://ir.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://ir.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://ir.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://ir.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://ir.archive.ubuntu.com oneiric-backports/universe Translation-en
Err http://ir.archive.ubuntu.com oneiric/restricted Sources
  404  Not Found [IP: 91.189.92.184 80]
Err http://ir.archive.ubuntu.com oneiric-backports/main Sources
  404  Not Found [IP: 91.189.92.184 80]
Err http://ir.archive.ubuntu.com oneiric-backports/main i386 Packages
  404  Not Found [IP: 91.189.92.184 80]
Get:31 http://dl.google.com stable InRelease [1,540 B]
Ign http://dl.google.com stable InRelease
Get:32 http://dl.google.com stable/main i386 Packages [1,540 B]
Get:33 http://dl.google.com stable/main TranslationIndex [1,540 B]
Err http://dl.google.com stable/main i386 Packages
  
Err http://dl.google.com stable/main i386 Packages
  
Fetched 609 kB in 12min 4s (840 B/s)
W: GPG error: http://archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.canonical.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ir.archive.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ir.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://dl.google.com stable InRelease: File /var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_InRelease doesn't start with a clearsigned message
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources  404  Not Found [IP: 91.189.92.170 80]

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/source/Sources  404  Not Found

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_main_i18n_Index

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_multiverse_i18n_Index

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_restricted_i18n_Index

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric/universe/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/ir.archive.ubuntu.com_ubuntu_dists_oneiric_universe_i18n_Index

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/oneiric/partner/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch http://ir.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages  404  Not Found [IP: 91.189.92.184 80]

W: Failed to fetch gzip:/var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages  Encountered a section with no Package: header

W: Failed to fetch http://dl.google.com/linux/talkplugin/deb/dists/stable/main/i18n/Index  No Hash entry in Release file /var/lib/apt/lists/partial/dl.google.com_linux_talkplugin_deb_dists_stable_main_i18n_Index

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by raja.genupula on 2012-01-19
ok its look like lot of errors you got . 

do all these things
1st open your update manager and from settings option change your server to another mirror . this is for not found things .

2nd look at this link to correct the GPG problems . 
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

even you did the first process still you got that not found means then uncheck those PPA's from other software TAB at update manager settings . 

All the best .Let me know what you got .

---

### Post by emab on 2012-01-20
I did these two things but I still get the same error:

sources.list
```
# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted #Added by software-properties

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu oneiric main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-backports main restricted universe multiverse #Added by software-properties

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu oneiric-security universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main
```

aptitude update:
```
$ sudo apt-get update
Ign http://archive.ubuntu.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-updates InRelease
Ign http://archive.ubuntu.com oneiric-backports InRelease
Ign http://extras.ubuntu.com oneiric InRelease 
Ign http://archive.canonical.com oneiric InRelease
Ign http://archive.ubuntu.com oneiric-security InRelease
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://archive.canonical.com oneiric Release.gpg
Hit http://archive.ubuntu.com oneiric Release.gpg
Hit http://extras.ubuntu.com oneiric Release   
Hit http://archive.canonical.com oneiric Release
Hit http://archive.ubuntu.com oneiric-updates Release.gpg             
Hit http://extras.ubuntu.com oneiric/main Sources                    
Hit http://archive.canonical.com oneiric/partner Sources             
Hit http://archive.ubuntu.com oneiric-backports Release.gpg
Hit http://extras.ubuntu.com oneiric/main i386 Packages              
Hit http://archive.canonical.com oneiric/partner i386 Packages       
Hit http://archive.ubuntu.com oneiric-security Release.gpg           
Ign http://extras.ubuntu.com oneiric/main TranslationIndex           
Ign http://archive.canonical.com oneiric/partner TranslationIndex    
Hit http://archive.ubuntu.com oneiric Release  
Hit http://archive.ubuntu.com oneiric-updates Release                          
Hit http://archive.ubuntu.com oneiric-backports Release                        
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://archive.ubuntu.com oneiric/main Sources                             
Hit http://archive.ubuntu.com oneiric/restricted Sources             
Hit http://archive.ubuntu.com oneiric/multiverse Sources             
Hit http://archive.ubuntu.com oneiric/universe Sources               
Hit http://archive.ubuntu.com oneiric/main i386 Packages             
Ign http://archive.canonical.com oneiric/partner Translation-en_US   
Ign http://extras.ubuntu.com oneiric/main Translation-en_US          
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages
Ign http://archive.canonical.com oneiric/partner Translation-en      
Ign http://extras.ubuntu.com oneiric/main Translation-en             
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric/universe i386 Packages
Hit http://archive.ubuntu.com oneiric/main TranslationIndex
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://archive.ubuntu.com oneiric-updates/main Sources
Hit http://archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://archive.ubuntu.com oneiric-updates/universe Sources
Hit http://archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/main Sources
Hit http://archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://archive.ubuntu.com oneiric-backports/universe Sources
Hit http://archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/restricted Sources
Hit http://archive.ubuntu.com oneiric-security/main Sources
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources
Hit http://archive.ubuntu.com oneiric-security/universe Sources
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex
Hit http://archive.ubuntu.com oneiric/main Translation-en
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric/restricted Translation-en
Hit http://archive.ubuntu.com oneiric/universe Translation-en
Hit http://archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-backports/universe Translation-en
Hit http://archive.ubuntu.com oneiric-security/main Translation-en
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en
Reading package lists... Done
```


and still the previous error:
```
$ sudo apt-get install netbeans
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package netbeans
```

---

### Post by raja.genupula on 2012-01-20
are you having this problem only for netbeans or other installations are behaving as same ?

---

### Post by WorMzy on 2012-01-20
Apparently netbeans isn't in the Oneiric repositories for some reason: [http://packages.ubuntu.com/search?searchon=names&keywords=netbeans](http://packages.ubuntu.com/search?searchon=names&keywords=netbeans)

I'm not sure if that's a temporary state of affairs or not, but you might want to [file a bug report]("https://help.ubuntu.com/community/ReportingBugs") about it.

---

### Post by emab on 2012-01-27
I don't have problem with all of the packages! for example I installed eclipse instead of netbeans.
changing the mirror solved the problem. but still my graphics has got some problem: [http://ubuntuforums.org/showthread.php?p=11625532&posted=1#post11625532](http://ubuntuforums.org/showthread.php?p=11625532&posted=1#post11625532)

---

### Post by raja.genupula on 2012-01-27
thats cool . please mark this thread as solved from thread tools . 

thank you .

---

