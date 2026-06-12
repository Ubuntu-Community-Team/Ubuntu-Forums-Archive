---
title: "Update manager not working,error message"
date: 2011-04-12
forum: General Help
---

### Post by stephenstop on 2011-04-12
My update manager is not working,it showed an error that said it might be because a file is no longer available.I have ubuntu 10.4.Thank you so much!
stephen

---

### Post by earthpigg on 2011-04-12
lots more details, please. including the exact error message, and what led up to it.

and, in anticipation of what we are most likely to see... can you please copy/paste the output from these commands?

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

---

### Post by stephenstop on 2011-04-13
Hey sorry dude.

```
owner@owner-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04.2 LTS _Lucid Lynx_ - Release i386 (20110211.1)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid universe
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu lucid partner
# deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse
owner@owner-laptop:~$ ls /etc/apt/sources.list.d/
google-chrome.list                   lucid-partner.list
google-chrome.list.save              lucid-partner.list.save
google-talkplugin.list               owner-lmms-lucid.list
google-talkplugin.list.save          owner-lmms-lucid.list.save
kxstudio-team-music-lucid.list       owner-ppa-lucid.list
kxstudio-team-music-lucid.list.save  owner-ppa-lucid.list.save
owner@owner-laptop:~$ 

```
im running the update manager and its taking forever,

---

### Post by stephenstop on 2011-04-13
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2  Sub-process /bin/bzip2 returned an error code (2)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz  504  Gateway Time-out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.lzma  Sub-process /usr/bin/lzma returned an error code (1)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz  504  Gateway Time-out

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz  Sub-process gzip returned an error code (1)

W: Some index files failed to download, they have been ignored, or old ones used instead.

```


This is the error code

---

### Post by earthpigg on 2011-04-13
well, that is actually pretty unusual i think. usually we just see a lot of 404 errors.

i found a few others with a similar problem.

possible solution 1:

close update manager or software center if it is open.

system -> administration -> synaptic.

settings -> repositories

download from -> other -> select best server


if that has no effect, possible solution 2:

[this]("http://www.webupd8.org/2010/05/automatically-import-all-missing.html") solution looks promising.

---

### Post by stephenstop on 2011-04-13
Thanks i went into the synaptic manager and went to repositories and then other software and all but two boxes were checked.I dont really understand what any of them mean.For option 2 i dont understand it either.I have very limited computer and linux skills.Could you spell it out more.Thanks so much
stephen

---

### Post by KegHead on 2011-04-13
Hi!

Could this be the problem?

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

KegHead

---

### Post by earthpigg on 2011-04-13
> **KegHead said:**
> Hi!

Could this be the problem?

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

KegHead

nah, millions of us use universe and don't see this problem. :)

> Could you spell it out more.Thanks so much

I think the short version of that guide is to download [this package]("https://launchpad.net/~nilarimogard/+archive/webupd8/+files/launchpad-getkeys_0.3.1-1%7Ewebupd8%7Elucid3_all.deb") to your desktop, and then double click on it. 

After installing it, run this command from a terminal:

```
sudo launchpad-getkeys
```

if it does its thing without errors...

```
sudo apt-get update
```

if that does its thing without errors, then your problem is solved.

I can't promise you this will work, though, as I've never personally encountered your problem - this is based on google research.

---

### Post by KegHead on 2011-04-13
Hi earthpigg,

It was an (un)educated guess!

KegHead

---

### Post by stephenstop on 2011-04-13
```
Fetched 39.4kB in 4s (8,614B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.canonical.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com lucid-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/lucid-security/Release  

W: Failed to fetch http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some ind
```
any other ideas?

---

### Post by KegHead on 2011-04-13
Hi!

Could you try this in terminal:

sudo apt-get update

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

Advise

KegHead

---

### Post by stephenstop on 2011-04-13
```
owner@owner-laptop:~$ sudo apt-get update
[sudo] password for owner: 
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/kxstudio-team/music/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:3 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://ppa.launchpad.net/owner/lmms/ubuntu/ lucid/main Translation-en_US   
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/owner/ppa/ubuntu/ lucid/main Translation-en_US    
Hit http://ppa.launchpad.net lucid Release                                     
Get:4 http://dl.google.com stable Release [1,347B]                             
Get:5 http://dl.google.com stable Release [1,347B]                             
Get:6 http://archive.canonical.com lucid Release [8,215B]                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:7 http://security.ubuntu.com lucid-security Release [44.7kB]               
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Get:8 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]            
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net lucid Release                                     
Ign http://ppa.launchpad.net lucid Release                                     
Get:9 http://us.archive.ubuntu.com lucid Release [57.2kB]                      
Get:10 http://dl.google.com stable/main Packages [1,082B]                      
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:11 http://dl.google.com stable/main Packages [737B]                        
Hit http://archive.canonical.com lucid/partner Packages                        
Ign http://ppa.launchpad.net lucid/main Packages                               
Get:12 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]             
Ign http://ppa.launchpad.net lucid/main Packages                               
Get:13 http://security.ubuntu.com lucid-security/main Packages [176kB]        
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages                    
Hit http://us.archive.ubuntu.com lucid/main Sources                           
Hit http://us.archive.ubuntu.com lucid/restricted Sources                     
Ign http://ppa.launchpad.net lucid/main Packages                              
Hit http://us.archive.ubuntu.com lucid/universe Packages                      
Hit http://us.archive.ubuntu.com lucid/universe Sources                       
Hit http://us.archive.ubuntu.com lucid/multiverse Packages                    
Hit http://us.archive.ubuntu.com lucid/multiverse Sources                     
Err http://ppa.launchpad.net lucid/main Packages                              
  404  Not Found
Get:14 http://us.archive.ubuntu.com lucid-updates/main Packages [471kB]       
Err http://ppa.launchpad.net lucid/main Packages                               
  404  Not Found
Get:15 http://security.ubuntu.com lucid-security/restricted Packages [14B]     
Get:16 http://security.ubuntu.com lucid-security/main Sources [52.3kB]         
Get:17 http://security.ubuntu.com lucid-security/restricted Sources [14B]      
Get:18 http://security.ubuntu.com lucid-security/universe Packages [67.3kB]  
Get:19 http://security.ubuntu.com lucid-security/universe Sources [20.2kB]     
Get:20 http://security.ubuntu.com lucid-security/multiverse Packages [4,559B]  
Get:21 http://security.ubuntu.com lucid-security/multiverse Sources [1,753B]   
Get:22 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B] 
Get:23 http://us.archive.ubuntu.com lucid-updates/main Sources [185kB]
Get:24 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:25 http://us.archive.ubuntu.com lucid-updates/universe Packages [196kB]    
Get:26 http://us.archive.ubuntu.com lucid-updates/universe Sources [72.2kB]    
Get:27 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [10.5kB] 
Get:28 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [5,066B]  
Fetched 1,426kB in 8s (173kB/s)                                                
W: Failed to fetch http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
owner@owner-laptop:~$ sudo apt-get upgrade -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  kdelibs-bin kdelibs5 kdelibs5-data kdesudo libplasma3 skype
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.0MB of archives.
After this operation, 3,199kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ lucid/partner skype 2.2.0.25-1lucid1 [23.6MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdelibs-bin 4:4.4.5-0ubuntu1.1 [232kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libplasma3 4:4.4.5-0ubuntu1.1 [758kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdelibs5-data 4:4.4.5-0ubuntu1.1 [3,979kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdelibs5 4:4.4.5-0ubuntu1.1 [7,392kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main kdesudo 3.4.2.3-0ubuntu1.1 [36.2kB]
Fetched 36.0MB in 3min 29s (171kB/s)                                           
(Reading database ... 200378 files and directories currently installed.)
Preparing to replace kdelibs-bin 4:4.4.5-0ubuntu1 (using .../kdelibs-bin_4%3a4.4.5-0ubuntu1.1_i386.deb) ...
Unpacking replacement kdelibs-bin ...
Preparing to replace libplasma3 4:4.4.5-0ubuntu1 (using .../libplasma3_4%3a4.4.5-0ubuntu1.1_i386.deb) ...
Unpacking replacement libplasma3 ...
Preparing to replace kdelibs5-data 4:4.4.5-0ubuntu1 (using .../kdelibs5-data_4%3a4.4.5-0ubuntu1.1_all.deb) ...
Unpacking replacement kdelibs5-data ...
Preparing to replace kdelibs5 4:4.4.5-0ubuntu1 (using .../kdelibs5_4%3a4.4.5-0ubuntu1.1_i386.deb) ...
Unpacking replacement kdelibs5 ...
Preparing to replace kdesudo 3.4.2.3-0ubuntu1 (using .../kdesudo_3.4.2.3-0ubuntu1.1_i386.deb) ...
Unpacking replacement kdesudo ...
Preparing to replace skype 2.1.0.81-1ubuntu5 (using .../skype_2.2.0.25-1lucid1_i386.deb) ...
Unpacking replacement skype ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up kdelibs5-data (4:4.4.5-0ubuntu1.1) ...

Setting up skype (2.2.0.25-1lucid1) ...

Setting up kdelibs-bin (4:4.4.5-0ubuntu1.1) ...
Setting up kdelibs5 (4:4.4.5-0ubuntu1.1) ...

Setting up libplasma3 (4:4.4.5-0ubuntu1.1) ...

Setting up kdesudo (3.4.2.3-0ubuntu1.1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
owner@owner-laptop:~$ sudo apt-get dist-upgrade -f
[sudo] password for owner: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

was this what is supposed to happen?

---

### Post by KegHead on 2011-04-13
Hi!

Yes, it looks like some packages were updated.

It might be a good idea to upgrade your kernel.

sudo aptitude install linux-image -f

Answer yes..after update you'll be asked to restart..do so.

Any thoughts?

KegHead

---

### Post by earthpigg on 2011-04-13
well that was simple. who'd have thought to read the manual?

my keg is off to you, keghead.

give the update manager a shot now, stephenstop.

---

### Post by KegHead on 2011-04-13
Hi!

I try...I try...I try!!


KegHead

---

### Post by stephenstop on 2011-04-13
```
 blop{u} cmt{u} libdrm-dev{u} 
  linux-backports-modules-alsa-2.6.32-29-generic{u} 
  linux-headers-2.6.32-28{u} linux-headers-2.6.32-28-generic{u} 
  mesa-common-dev{u} tex-common{u} texlive-binaries{u} 
0 packages upgraded, 1 newly installed, 9 to remove and 0 not upgraded.
Need to get 4,482B of archives. After unpacking 118MB will be freed.

```
is this a good idea?

---

### Post by KegHead on 2011-04-14
Yes.

You'll most likely have to restart.

KegHead

---

### Post by stephenstop on 2011-04-14
Hey i did it and restarted but it said this

he repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

ailed to fetch [http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by KegHead on 2011-04-14
Hi!

Have you checked your update manager?

KegHead

---

### Post by stephenstop on 2011-04-14
yes i had all the same boxes checked

---

### Post by KegHead on 2011-04-14
Hi!

How about other software and updates in update manager?

KegHead

---

### Post by KegHead on 2011-04-14
Hmm,

You mentioned you are using 10.04.

If nothing else works I would backup your files..and maybe reinstall 10.04 or maybe goto 10.10

It might take an hour, but save hours down the road and you would have fresh install.

KegHead

---

### Post by stephenstop on 2011-04-14
hmmm is there no other way?I had to go from 10.10 to 10.4 because it was crashing when i used lmms and other programs.Here is the error again,what is a launchpad in the error sense i mean.

  	 	 	 	pre.cjk { font-family: "DejaVu Sans",monospace; }p { margin-bottom: 0.08in; }[FONT=monospace]Failed to fetch [http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/owner/lmms/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.[/FONT]

---

### Post by stephenstop on 2011-04-14
yes please.My update manager when run gives the error i put on my last post.I have 10.4 ubuntu.Im a novice.Please help

---

### Post by earthpigg on 2011-04-14
two of the sources you've added over the months seem to have died.

this will make it so that they aren't searched for any more, but are still available if they come back to life in the future.

```
sudo mv /etc/apt/sources.list.d/owner-lmms-lucid.list /etc/apt/sources.list.d/owner-lmms-lucid.list-backup
sudo mv /etc/apt/sources.list.d/owner-ppa-lusid.list /etc/apt/sources.list.d/owner-ppa-lusid.list-backup
sudo apt-get update
```

---

### Post by stephenstop on 2011-04-15
Ok can you tell which sources?or actually isthere a way for me to do it?This is what happemed.Thank you so much for helping me



```
owner@owner-laptop:~$ sudo mv /etc/apt/sources.list.d/owner-lmms-lucid.list /etc/apt/sources.list.d/owner-lmms-lucid.list-backup
[sudo] password for owner: 
owner@owner-laptop:~$ sudo mv /etc/apt/sources.list.d/owner-ppa-lusid.list /etc/apt/sources.list.d/owner-ppa-lusid.list-backup
mv: cannot stat `/etc/apt/sources.list.d/owner-ppa-lusid.list': No such file or directory
owner@owner-laptop:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:3 http://archive.canonical.com lucid Release.gpg [198B]                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Get:4 http://dl.google.com stable Release [1,347B]                             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Get:5 http://dl.google.com stable Release [1,347B]                             
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/kxstudio-team/music/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg                                 
Get:6 http://archive.canonical.com lucid Release [8,215B]                      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Ign http://ppa.launchpad.net/owner/ppa/ubuntu/ lucid/main Translation-en_US    
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Get:7 http://dl.google.com stable/main Packages [1,096B]                       
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages                    
Get:8 http://dl.google.com stable/main Packages [737B]                         
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://security.ubuntu.com lucid-security/main Sources                     
Hit http://security.ubuntu.com lucid-security/restricted Sources               
Hit http://security.ubuntu.com lucid-security/universe Packages                
Hit http://security.ubuntu.com lucid-security/universe Sources                 
Hit http://security.ubuntu.com lucid-security/multiverse Packages              
Get:9 http://archive.canonical.com lucid/partner Packages [12.5kB]             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/restricted Packages                     
Hit http://us.archive.ubuntu.com lucid/main Sources                            
Hit http://us.archive.ubuntu.com lucid/restricted Sources                      
Hit http://security.ubuntu.com lucid-security/multiverse Sources               
Ign http://ppa.launchpad.net lucid/main Packages                               
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Fetched 25.8kB in 1s (16.1kB/s)
W: Failed to fetch http://ppa.launchpad.net/owner/ppa/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
owner@owner-laptop:~$
```

---

### Post by earthpigg on 2011-04-16
***EDIT:***


OOOOH, i see now. I made a mistake. the code should have been 

```
sudo mv /etc/apt/sources.list.d/owner-ppa-lu***_c_***id.list /etc/apt/sources.list.d/owner-ppa-luc_***i***_d.list-backup
```
and ***not***
```
sudo mv /etc/apt/sources.list.d/owner-ppa-lu***_s_***id.list /etc/apt/sources.list.d/owner-ppa-lu***_s_***id.list-backup
```

(see the C instead of the S, twice in each line?)

What an embarrassing typo, but it didn't do any damage. It also didn't fix anything, hence the one error message went away and one error message remains.

Here run these two commands:

```
sudo mv /etc/apt/sources.list.d/owner-ppa-lucid.list /etc/apt/sources.list.d/owner-ppa-lucid.list-backup
sudo apt-get update

```

---

### Post by stephenstop on 2011-04-19
```
owner@owner-laptop:~$ sudo mv /etc/apt/sources.list.d/owner-ppa-lucid.list /etc/apt/sources.list.d/owner-ppa-lucid.list-backup
mv: cannot stat `/etc/apt/sources.list.d/owner-ppa-lucid.list': No such file or directory
owner@owner-laptop:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [197B]
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:3 http://dl.google.com stable Release [1,347B]                             
Get:4 http://dl.google.com stable Release [1,347B]                             
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/kxstudio-team/music/ubuntu/ lucid/main Translation-en_US
Hit http://archive.canonical.com lucid Release.gpg                             
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Hit http://us.archive.ubuntu.com lucid Release.gpg                             
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US          
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US      
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US    
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg                     
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US  
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                                 
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://archive.canonical.com lucid Release                                 
Get:5 http://dl.google.com stable/main Packages [1,086B]                       
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release                          
Hit http://us.archive.ubuntu.com lucid-updates Release                         
Get:6 http://dl.google.com stable/main Packages [737B]                         
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://security.ubuntu.com lucid-security/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Fetched 4,911B in 0s (5,867B/s)
Reading package lists... Done
owner@owner-laptop:~$ 

```

hey thanks is this right?

---

