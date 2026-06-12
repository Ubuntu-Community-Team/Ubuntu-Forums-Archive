---
title: "ubuntu software center and synaptic pkg manager problem"
date: 2012-03-27
forum: General Help
---

### Post by javaaddict on 2012-03-27
Hi friends!! Am new to ubuntu.. Am using Ubuntu 11.04 version.. If I try to open synaptic package manager it results as encountered  a problem.. and if am trying install any software in terminal(sudo apt-get install), it results as

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

Even software center not loading, it just opening and left as it is..

I executed this command at last, sudo apt-get remove..

Please help me..

---

### Post by kc1di on 2012-03-27
Try this first : (in terminal)
```
sudo apt-get update
```

that may give us another error message post it here if it does.

if it does not clear the problem go to the file manager and navigate to file system /etc/apt/sources.list copy and print it here lets see what's not right.  Or you can try if there is a soruces.list.saved making it your new source list by removing the .saved and changing the name on the current source list to say sources.list.bak

Hope that's not too confusing.
After doing the above again go to terminal and type: sudo apt-get update

Try again synaptic

---

### Post by javaaddict on 2012-03-27
Sir, This is the file


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main

---

### Post by javaaddict on 2012-03-27
This is the output in terminal sir..


Ign file: natty InRelease
Ign file: natty Release.gpg       
Get:1 file: natty Release [11.0 kB]                                 
Ign file: natty/main i386 Packages/DiffIndex                                   
Ign file: natty/restricted i386 Packages/DiffIndex                  
Ign file: natty/multiverse i386 Packages/DiffIndex                  
Ign file: natty/universe i386 Packages/DiffIndex                    
Ign file: natty/main TranslationIndex                               
Ign file: natty/multiverse TranslationIndex                         
Ign file: natty/restricted TranslationIndex                         
Ign file: natty/universe TranslationIndex                           
Ign file: natty/main Translation-en_US                              
Ign file: natty/main Translation-en                                 
Ign file: natty/multiverse Translation-en_US                        
Ign file: natty/multiverse Translation-en                           
Ign file: natty/restricted Translation-en_US                        
Ign file: natty/restricted Translation-en                           
Ign file: natty/universe Translation-en_US                          
Ign file: natty/universe Translation-en                             
Hit [http://hacktolive.org](http://hacktolive.org) natty InRelease                                      
Hit [http://hacktolive.org](http://hacktolive.org) natty/main i386 Packages                             
Hit [http://hacktolive.org](http://hacktolive.org) natty/restricted i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) natty/multiverse i386 Packages
Hit [http://hacktolive.org](http://hacktolive.org) natty/partner i386 Packages                 
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease [12.6 kB]              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                               
Get:3 [http://hacktolive.org](http://hacktolive.org) natty/universe i386 Packages [12.6 kB]         
Get:4 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources/DiffIndex [12.6 kB]          
Get:5 [http://hacktolive.org](http://hacktolive.org) natty/main TranslationIndex [12.6 kB]              
Get:6 [http://hacktolive.org](http://hacktolive.org) natty/main TranslationIndex [12.6 kB]              
Get:7 [http://hacktolive.org](http://hacktolive.org) natty/main TranslationIndex [12.6 kB]              
Get:8 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages/DiffIndex [12.6 kB]    
Get:9 [http://hacktolive.org](http://hacktolive.org) natty/main TranslationIndex [12.6 kB]              
Hit [http://hacktolive.org](http://hacktolive.org) natty/multiverse TranslationIndex                    
Get:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages/DiffIndex [12.6 kB]   
Hit [http://hacktolive.org](http://hacktolive.org) natty/partner TranslationIndex                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Hit [http://hacktolive.org](http://hacktolive.org) natty/restricted TranslationIndex                    
Hit [http://hacktolive.org](http://hacktolive.org) natty/universe TranslationIndex                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Hit [http://hacktolive.org](http://hacktolive.org) natty/main Translation-en_US                         
Hit [http://hacktolive.org](http://hacktolive.org) natty/main Translation-en                            
Hit [http://hacktolive.org](http://hacktolive.org) natty/multiverse Translation-en_US                   
Hit [http://hacktolive.org](http://hacktolive.org) natty/multiverse Translation-en                      
Hit [http://hacktolive.org](http://hacktolive.org) natty/partner Translation-en_US                      
Get:11 [http://hacktolive.org](http://hacktolive.org) natty/partner Translation-en [12.6 kB]            
Get:12 [http://hacktolive.org](http://hacktolive.org) natty/partner Translation-en [12.6 kB]            
50% [12 Translation-en bzip2 0 B] [Connecting to [www.reliancenetconnect.co.in](www.reliancenetconnect.co.in) (bzip2: (stdin) is not a bzip2 file.
Hit [http://hacktolive.org](http://hacktolive.org) natty/restricted Translation-en_US                   
Get:13 [http://hacktolive.org](http://hacktolive.org) natty/restricted Translation-en [12.6 kB]         
57% [13 Translation-en bzip2 0 B] [Connecting to hacktolive.org]  2,061 B/s 18sbzip2: (stdin) is not a bzip2 file.
Hit [http://hacktolive.org](http://hacktolive.org) natty/universe Translation-en_US                     
Hit [http://hacktolive.org](http://hacktolive.org) natty/universe Translation-en                        
57% [12 Translation-en xz 0 B] [Connecting to hacktolive.org]     2,061 B/s 18s/usr/bin/xz: (stdin): File format not recognized
57% [13 Translation-en xz 0 B] [Connecting to hacktolive.org]     2,061 B/s 18s/usr/bin/xz: (stdin): File format not recognized
57% [12 Translation-en lzma 0 B] [Connecting to hacktolive.org]   2,075 B/s 18s/usr/bin/lzma: Decoder error
57% [13 Translation-en lzma 0 B]                                  2,075 B/s 18s/usr/bin/lzma: Decoder error
Fetched 46.7 kB in 29s (1,574 B/s)                                             
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2Please click one of the Quick Reply icons in the posts above to activate Quick Reply.
W: Failed to fetch gzip:/var/lib/apt/lists/partial/hacktolive.org_repo_archive_dists_natty_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Paqman on 2012-03-27
Ok, the problem seems to be some of the third-party sources you're using:
```
50% [12 Translation-en bzip2 0 B] [Connecting to **www.reliancenetconnect.co.in** (bzip2: (stdin) is not a bzip2 file.
Hit http://hacktolive.org natty/restricted Translation-en_US 
Get:13 http://hacktolive.org natty/restricted Translation-en [12.6 kB] 
57% [13 Translation-en bzip2 0 B] [**Connecting to hacktolive.org**] 2,061 B/s 18sbzip2: (stdin) is not a bzip2 file.
Hit http://hacktolive.org natty/universe Translation-en_US 
Hit http://hacktolive.org natty/universe Translation-en 
57% [12 Translation-en xz 0 B] [Connecting to hacktolive.org] 2,061 B/s 18s/usr/bin/xz: (stdin): File format not recognized
57% [13 Translation-en xz 0 B] [Connecting to hacktolive.org] 2,061 B/s 18s/usr/bin/xz: (stdin): File format not recognized
57% [12 Translation-en lzma 0 B] [Connecting to hacktolive.org] 2,075 B/s 18s/usr/bin/lzma: Decoder error
57% [13 Translation-en lzma 0 B] 2,075 B/s 18s/usr/bin/lzma: Decoder error
Fetched 46.7 kB in 29s (1,574 B/s) 
W: GPG error: http://ppa.launchpad.net natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2Please click one of the Quick Reply icons in the posts above to activate Quick Reply.
W: Failed to fetch gzip:/var/lib/apt/lists/partial/hacktolive.org_repo_archive_dists_natty_universe_b inary-i386_Packages Hash Sum mismatch
```

I don't know what relianceconnect is, but IIRC hacktolive is the repo for a little remastersys-based respin called Super OS. Go to Software Sources and disable any of the entries in there relating to these repositories.

---

### Post by javaaddict on 2012-03-27
After performing that my sources.list becomes like this .. a long gap and

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main universe
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports restricted main universe


---------------------------------x-----------------------------------x----------------------------
And While closing software sources, it prompt as "Package out-of-date" and started downloading, then this is error shown after downloading packages..

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports InRelease: The following signatures were invalid: NODATA 1 NODATA 2

---

### Post by kc1di on 2012-03-27
> **javaaddict said:**
> After performing that my sources.list becomes like this .. a long gap and

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main universe
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty restricted main universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports restricted main universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) natty-backports restricted main universe


---------------------------------x-----------------------------------x----------------------------
And While closing software sources, it prompt as "Package out-of-date" and started downloading, then this is error shown after downloading packages..

W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) natty-backports InRelease: The following signatures were invalid: NODATA 1 NODATA 2

Hi again,
Please post what your /etc/apt/sources.list looks like.
go to the file and copy it and past it here.

---

### Post by raja.genupula on 2012-03-27
hi open your terminal and do this
```
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update

```
and let us know what you got .
all the best .

---

### Post by javaaddict on 2012-03-28
Thank you frnds........... Thanks a lot for all your help..

---

