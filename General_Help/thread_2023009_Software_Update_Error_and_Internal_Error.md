---
title: "Software Update Error and Internal Error"
date: 2012-07-11
forum: General Help
---

### Post by xchecker on 2012-07-11
I am running Precise on a desktop.  When I try to run Update Manager I get an error:

> Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.2.3_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.2.3_all.deb) 404  Not Found [IP: 91.189.91.25 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/x/xdiagnose/xdiagnose_2.5.1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xdiagnose/xdiagnose_2.5.1_all.deb) 404  Not Found [IP: 91.189.91.25 80]



I was then given an Internal Error message which included as detail:
> ExecutablePath
	/usr/bin/Xorg


Suggestions?

---

### Post by jmfal on 2012-07-11
Hi 
Run 
```
  sudo apt-get update  
```

and post the results

---

### Post by matt_symes on 2012-07-11
Hi

There is no xdiagnose_2.5.1_all.deb in the repositories (neither the us or uk repos).

Take a look here.

[http://us.archive.ubuntu.com/ubuntu/pool/main/x/xdiagnose/](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xdiagnose/)

You have the same problem with the software center as well.

Can you please post the output of

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*
```

You may have some problems with your source files.

It may be a case of editing them or deleting the list files in /var/lib/dpkg/lists.

Kind regards

---

### Post by xchecker on 2012-07-11
Results...> 

crichmond@brichmond-desktop:~$ cat /etc/apt/sources.list /etc/apt/sources.list.d/*
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[Edubuntu 8.04.1 _Hardy Heron_ - Release i386 Binary-1 (20080701.1)]/ hardy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse

# deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) hardy main
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main # disabled on upgrade to maverick
# deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main # disabled on upgrade to maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main #Third party developers repository
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main # disabled on upgrade to maverick
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main # disabled on upgrade to maverick
# deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) maverick main # disabled on upgrade to maverick
# deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/do-testers/ppa/ubuntu](http://ppa.launchpad.net/do-testers/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/do-test/ppa/ubuntu](http://ppa.launchpad.net/do-test/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/do-test/ppa/ubuntu](http://ppa.launchpad.net/do-test/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/do-test/ppa/ubuntu](http://ppa.launchpad.net/do-test/ppa/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main # disabled on upgrade to maverick
# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main # disabled on upgrade to maverick
# deb [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) maverick main # disabled on upgrade to maverick
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
# deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main # disabled on upgrade to lucid
deb [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main
deb [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main
deb-src [http://ppa.launchpad.net/tikhonov/misc/ubuntu](http://ppa.launchpad.net/tikhonov/misc/ubuntu) precise main
crichmond@brichmond-desktop:~$

---

### Post by xchecker on 2012-07-11
Also...

> crichmond@brichmond-desktop:~$ sudo apt-get update
[sudo] password for crichmond: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease                     
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]                 
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) precise InRelease                                
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease                      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease                                 
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]                   
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg [198 B]                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release.gpg                               
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B]          
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release [49.6 kB]                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release                                   
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release                               
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]           
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                              
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources                       
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources [934 kB]                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main TranslationIndex                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                     
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex              
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [14 B]   
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [24.8 kB]      
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [713 B]  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [7,832 B]  
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [75.5 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [14 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [19.7 kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [73 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [70 B]
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B]
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [38.4 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en_US                    
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Translation-en                       
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [13.3 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]        
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]        
Get:29 [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources [5,470 B]          
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]      
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B] 
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]  
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex             
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [127 kB]      
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [33.0 kB] 
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [321 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [88.6 kB]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,047 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [74 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [71 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [71 B]
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en               
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en [150 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en     
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en [52.8 kB]
Fetched 14.4 MB in 17s (833 kB/s)                                              
Reading package lists... Done

---

### Post by matt_symes on 2012-07-11
Hi

You upgraded this from Hardy ?

Open a terminal and copy and paste

```
sudo rm /var/lib/apt/lists/*  /var/lib/apt/lists/partial/*
```Enter your password. It will not be echoed to the screen.

```
sudo apt-get update
``````
^date^grade
```Post back any errors.

Kind regards

---

### Post by xchecker on 2012-07-11
I started on Hardy years ago and have updated through the various new versions over the years.  It was working fine in 11.04 but since I updated to 12.04 I have been having regular crashes which I had thought was related to Flash problems but I have now begun to think something else is causing the crashes and may be related to whatever is causing the Update Manager problem.

Well, Terminal finished with your commands, replacing and setting up my software again (I assume that was the intent) but it was so long I can't scroll back to the beginning to capture the output of the first command.  I recall it said something like "Doesn't exist" or "Not a folder", something like that.  Shall I try running it again, or is it too late now?

Thanks!

---

### Post by xchecker on 2012-07-11
I ran the first command again and got the following.  I believe this is the same response as before.

> crichmond@brichmond-desktop:~$ sudo rm /var/lib/apt/lists/*  /var/lib/apt/lists/partial/*
[sudo] password for crichmond: 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory


---

### Post by matt_symes on 2012-07-12
Hi

This error message is not a problem.

> rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

Don't worry about the second error message.

Does update manager work now ?

Kind regards

---

### Post by xchecker on 2012-07-12
Things seem to be working much better now.  In addition to Update Manager, when I launch my browser Firefox now actually shows my home pages.  Prior to your suggestions it would always launch with a blank tab instead of with my home pages and each tab I launched would keep showing "Connecting..." all the time.

But this is all fixed now so I thank you very much.  I'll mark this as solved!

---

### Post by donaldt on 2012-07-19
I have a similar problem.  Update manager does not work.  When I do sudo apt-get update, it updates files and ends with this message:

 Failed to fetch [http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/hardy/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/lucid/main/binary-i386/Packages](http://wine.budgetdedicated.com/apt/dists/lucid/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
donald@donald-Aspire-3810T:~$ 

I deleted wine some time ago and don't want it back.  What else can I do to unlock my update capability.  It says I have 75 updates, but when I try to update them the program freezes.

Thanks if you can help!  donaldt

---

### Post by matt_symes on 2012-07-19
Hi 

@donaldt

You are using hardy as well ? That ppa for hardy does not exist.

Please post the output, from the terminal, of this command

```
grep -rv "^#" /etc/apt/sources.list /etc/apt/sources.list.d/*
```

Kind regards

---

