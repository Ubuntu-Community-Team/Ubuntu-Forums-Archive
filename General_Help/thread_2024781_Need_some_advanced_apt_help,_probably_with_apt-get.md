---
title: "Need some advanced apt help, probably with apt-get -c"
date: 2012-07-14
forum: General Help
---

### Post by kansasnoob on 2012-07-14
To understand what I'm doing you need to first look here:

[http://ubuntuforums.org/showpost.php?p=12093593&postcount=20](http://ubuntuforums.org/showpost.php?p=12093593&postcount=20)

That actually works just fine ATM (although I wonder if I shouldn't wildcard a couple of the packages in my purge command) but I'm trying to get away from directly editing the Precise sources.list for fear of someone failing to revert the Oneiric source change back to Precise :(

So I figured out that I can create the desired new source like this:

```
sudo sed -e s'/precise/oneiric/g' /etc/apt/sources.list | sudo tee /etc/apt/sources.list.oneiric
```

eg;

```
lance@lance-desktop:~$ sudo sed -e s'/precise/oneiric/g' /etc/apt/sources.list | sudo tee /etc/apt/sources.list.oneiric
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta i386 (20120404)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

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

I sort of wish I could get that to run silently but it does appear to work:

```
lance@lance-desktop:~$ ls /etc/apt
apt.conf.d     sources.list    sources.list.oneiric  trustdb.gpg  trusted.gpg~
preferences.d  sources.list.d  sources.list.save     trusted.gpg  trusted.gpg.d

```

And I think the new source looks OK:

```
# deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Beta i386 (20120404)]/ oneiric main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric universe
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric multiverse
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ oneiric-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://security.ubuntu.com/ubuntu oneiric-security main restricted
deb http://security.ubuntu.com/ubuntu oneiric-security universe
deb-src http://security.ubuntu.com/ubuntu oneiric-security universe
deb http://security.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://security.ubuntu.com/ubuntu oneiric-security multiverse

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

But I'd hoped to next update only that source and install 'abiword':

```
sudo apt-get -c /etc/apt/sources.list.oneiric update 

sudo apt-get -c /etc/apt/sources.list.oneiric install abiword

```

However when I try to update I get this:

```
lance@lance-desktop:~$ sudo apt-get -c /etc/apt/sources.list.oneiric update
E: Syntax error /etc/apt/sources.list.oneiric:57: Extra junk at end of file

```

I've poured over the man pages and I'm stumped :confused:

So, question #1:

Is this just a stupid idea to begin with?

And question #2:

Why am I getting that error?

Potential question #3:

Also might as well ask, in case I figure out those two questions, is it possible to run that first command "silently"?

Many thanks in advance :D

---

### Post by Vaphell on 2012-07-14
#2 [http://lists.debian.org/deity/2005/05/msg00236.html](http://lists.debian.org/deity/2005/05/msg00236.html)

#3 sure, just redirect sed output to file :-)
```
sed '...' input > output
```

---

### Post by kansasnoob on 2012-07-14
Excellent, many thanks :D

Now it's time to see how badly I can blow things up :guitar:

---

### Post by kansasnoob on 2012-07-14
I'm getting closer all the time but still having some trouble getting apt to install only from that new source.

But I'm bone tired and may well be making a stupid mistake so I'll revisit this later :)

Many, many thanks for the help.

---

### Post by kansasnoob on 2012-07-14
Somehow I'm still not getting the syntax right to update and install only from the new source:

```
lance@lance-desktop:~$ sudo apt-get -o Item::Dir::Etc::SourceList=/etc/apt/sources.list.oneiric update
Ign http://security.ubuntu.com precise-security InRelease                 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]     
Ign http://us.archive.ubuntu.com precise InRelease                        
Ign http://us.archive.ubuntu.com precise-updates InRelease                
Ign http://us.archive.ubuntu.com precise-backports InRelease              
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]       
Ign http://extras.ubuntu.com precise InRelease                            
Get:3 http://us.archive.ubuntu.com precise Release.gpg [198 B]            
Hit http://extras.ubuntu.com precise Release.gpg                          
Get:4 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]    
Hit http://extras.ubuntu.com precise Release                              
Get:5 http://us.archive.ubuntu.com precise-backports Release.gpg [198 B]  
Get:6 http://security.ubuntu.com precise-security/main Sources [26.1 kB]  
Hit http://extras.ubuntu.com precise/main Sources                         
Get:7 http://us.archive.ubuntu.com precise Release [49.6 kB]              
Hit http://extras.ubuntu.com precise/main i386 Packages                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                
Ign http://deb.opera.com stable InRelease                                 
Get:8 http://security.ubuntu.com precise-security/restricted Sources [14 B]
Get:9 http://security.ubuntu.com precise-security/universe Sources [7,832 B]
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [713 B]
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [78.4 kB]
Hit http://deb.opera.com stable Release.gpg                               
Get:12 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]     
Get:13 http://security.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:14 http://security.ubuntu.com precise-security/universe i386 Packages [20.7 kB]
Hit http://deb.opera.com stable Release                                   
Get:15 http://us.archive.ubuntu.com precise-backports Release [49.6 kB]   
Get:16 http://security.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex     
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex 
Get:17 http://us.archive.ubuntu.com precise/main Sources [934 kB]         
Hit http://deb.opera.com stable/non-free i386 Packages                    
Hit http://security.ubuntu.com precise-security/main Translation-en       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en 
Hit http://security.ubuntu.com precise-security/restricted Translation-en 
Ign http://deb.opera.com stable/non-free TranslationIndex                 
Hit http://security.ubuntu.com precise-security/universe Translation-en   
Ign http://extras.ubuntu.com precise/main Translation-en_US               
Ign http://extras.ubuntu.com precise/main Translation-en                  
Ign http://deb.opera.com stable/non-free Translation-en_US                
Get:18 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]  
Get:19 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]   
Ign http://deb.opera.com stable/non-free Translation-en                   
Ign http://archive.canonical.com precise InRelease                        
Ign http://ppa.launchpad.net precise InRelease                            
Ign http://ppa.launchpad.net precise InRelease            
Ign http://ppa.launchpad.net precise InRelease                            
Hit http://archive.canonical.com precise Release.gpg                      
Ign http://ppa.launchpad.net precise InRelease            
Hit http://ppa.launchpad.net precise Release.gpg          
Hit http://archive.canonical.com precise Release                          
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://archive.canonical.com precise/partner Sources                  
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://ppa.launchpad.net precise Release.gpg            
Hit http://archive.canonical.com precise/partner i386 Packages            
Ign http://archive.canonical.com precise/partner TranslationIndex         
Hit http://ppa.launchpad.net precise Release                
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise Release                              
Hit http://ppa.launchpad.net precise/main Sources                         
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Sources                         
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Sources                         
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main Sources                         
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Ign http://archive.canonical.com precise/partner Translation-en_US        
Ign http://archive.canonical.com precise/partner Translation-en           
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en                  
Get:20 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]   
Get:21 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB] 
Get:22 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]
Get:23 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get:24 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Hit http://us.archive.ubuntu.com precise/main TranslationIndex            
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex      
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex      
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex        
Get:25 http://us.archive.ubuntu.com precise-updates/main Sources [128 kB] 
Get:26 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:27 http://us.archive.ubuntu.com precise-updates/universe Sources [33.0 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:29 http://us.archive.ubuntu.com precise-updates/main i386 Packages [321 kB]
Get:30 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:31 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [89.3 kB]
Get:32 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex    
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:33 http://us.archive.ubuntu.com precise-backports/main Sources [1,845 B]
Get:34 http://us.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:35 http://us.archive.ubuntu.com precise-backports/universe Sources [12.4 kB]
Get:36 http://us.archive.ubuntu.com precise-backports/multiverse Sources [1,383 B]
Get:37 http://us.archive.ubuntu.com precise-backports/main i386 Packages [1,271 B]
Get:38 http://us.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:39 http://us.archive.ubuntu.com precise-backports/universe i386 Packages [11.2 kB]
Get:40 http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages [999 B]
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex  
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en              
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en        
Hit http://us.archive.ubuntu.com precise/restricted Translation-en        
Hit http://us.archive.ubuntu.com precise/universe Translation-en          
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en      
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en  
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en    
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 13.3 MB in 30s (433 kB/s)                                         
Reading package lists... Done

```

---

### Post by kansasnoob on 2012-07-14
I seem to be gaining a little bit :)

It appears that I need to also use the "-t=" suffix to indicate the specific target.

Still struggling a bit though but I never give up :)

---

### Post by kansasnoob on 2012-07-14
I guess I'm totally stumped :confused:

Apt ate my lunch :(

---

### Post by kansasnoob on 2012-07-15
I may have a PPA to work with now:

[https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise](https://launchpad.net/~mrpouit/+archive/ppa?field.series_filter=precise)

I'm too fried to try it ATM ........... but soon :D

---

### Post by kansasnoob on 2012-07-17
Just bumping this :)

Nothing urgent but it's something I'd like to learn anyway.

And there's always a chance of fresh eyes having a different idea.

---

### Post by kansasnoob on 2012-07-20
Can't hurt to bump this just in case some fresh eyes have new ideas :)

There is no urgency, but I'd like to add it to my toolbox.

---

