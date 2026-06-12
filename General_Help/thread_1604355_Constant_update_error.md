---
title: "Constant update error"
date: 2010-10-23
forum: General Help
---

### Post by kurotsuno on 2010-10-23
I've had this issue now since 10.04 and I can't find anything to help me resolve it. 


Error:
> W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg](http://archive.canonical.com/ubuntu/dists/maverick/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I do get updates but the updater continues to give me this message and frankly it's becoming quite annoying. 

I'm currently on a full install of 10.10 32bit (Not an upgrade from 10.04)

---

### Post by dcstar on 2010-10-23
> **kurotsuno said:**
> I've had this issue now since 10.04 and I can't find anything to help me resolve it. 

Error:

I do get updates but the updater continues to give me this message and frankly it's becoming quite annoying. 

I'm currently on a full install of 10.10 32bit (Not an upgrade from 10.04)
Do not "quote" data.

If you do this and do not get valid data then your DNS is faulty:
```
dig archive.ubuntu.com
```

---

### Post by kurotsuno on 2010-10-23
how do I know it's valid data ?

---

### Post by dcstar on 2010-10-23
> **kurotsuno said:**
> how do I know it's valid data ?

Post the output here if you don't know.

---

### Post by kurotsuno on 2010-10-23
```
; <<>> DiG 9.7.1-P2 <<>> archive.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57690
;; flags: qr rd ra; QUERY: 1, ANSWER: 9, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;archive.ubuntu.com.		IN	A

;; ANSWER SECTION:
archive.ubuntu.com.	587	IN	A	91.189.88.40
archive.ubuntu.com.	587	IN	A	91.189.88.46
archive.ubuntu.com.	587	IN	A	91.189.88.45
archive.ubuntu.com.	587	IN	A	91.189.88.30
archive.ubuntu.com.	587	IN	A	91.189.88.31
archive.ubuntu.com.	587	IN	A	91.189.92.169
archive.ubuntu.com.	587	IN	A	91.189.92.170
archive.ubuntu.com.	587	IN	A	91.189.92.171
archive.ubuntu.com.	587	IN	A	91.189.92.172

;; Query time: 74 msec
;; SERVER: 192.168.1.31#53(192.168.1.31)
;; WHEN: Sun Oct 24 04:25:10 2010
;; MSG SIZE  rcvd: 180

```

there's the output

---

### Post by kurotsuno on 2010-10-24
any help would be appreciated I would like to get this sorted so I can get rid of that ugly red triangle that sits in my notification area.

---

### Post by kurotsuno on 2010-10-24
Anyone ?

---

### Post by philinux on 2010-10-24
Post your sources list.

```
cat /etc/apt/sources.list
```

Dont forget to wrap it with code tags. (#) icon.

---

### Post by kurotsuno on 2010-10-24
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse

```

that's my sources

---

### Post by kurotsuno on 2010-10-24
well if someone can check out what I posted and give me some help with the actual problem at hand would be appreciated.

---

### Post by kurotsuno on 2010-10-24
I've tried to look online myself for help with my issue but still can't really find anything solid.

I don't mean to keep bumping this thread but I really need this fixed.

---

### Post by philinux on 2010-10-25
Your sources.list looks fine. Have you got ppa's installed?

What are the full error messages from this.

```
sudo apt-get update

then

sudo apt-get upgrade
```

---

### Post by WaNaBePi on 2013-04-01
Don't know that I have it quite as bad as the op, but I have a very similar problem. Sorry if I'm encroaching op, but I am bumping for you in a sense if it makes you feel any better.

My output:

```
default@default-laptop:~$ sudo apt-get update
[sudo] password for default: 
Get:1 http://archive.canonical.com precise Release.gpg [198 B]
Hit http://archive.canonical.com precise Release.gpg                           
Hit http://archive.canonical.com precise Release                               
Hit http://archive.canonical.com precise Release                               
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://archive.canonical.com precise/partner amd64 Packages                
Hit http://archive.canonical.com precise/partner i386 Packages                 
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://us.archive.ubuntu.com lucid-backports Release.gpg                   
Hit http://us.archive.ubuntu.com precise Release.gpg                           
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]         
Hit http://us.archive.ubuntu.com lucid-backports Release                       
Hit http://us.archive.ubuntu.com precise Release                               
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]           
Hit http://us.archive.ubuntu.com lucid-backports/main Sources                  
Hit http://us.archive.ubuntu.com lucid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com lucid-backports/universe Sources              
Hit http://us.archive.ubuntu.com lucid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com lucid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com lucid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com lucid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com lucid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com lucid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com lucid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com lucid-backports/multiverse i386 Packages      
Ign http://us.archive.ubuntu.com lucid-backports/main TranslationIndex         
Ign http://us.archive.ubuntu.com lucid-backports/multiverse TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/restricted TranslationIndex   
Ign http://us.archive.ubuntu.com lucid-backports/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages               
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages             
Hit http://us.archive.ubuntu.com precise/main i386 Packages                    
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages              
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:4 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [191 kB]
Get:5 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [592 kB]
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://archive.canonical.com precise/partner Translation-en_US             
Ign http://archive.canonical.com precise/partner Translation-en                
Get:6 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [9,418 B]
Get:7 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Get:8 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [194 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/main i386 Packages [603 kB] 
Get:10 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [10.4 kB]
Get:11 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.1 kB]
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex         
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex     
Hit http://us.archive.ubuntu.com precise/main Translation-en                   
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en             
Hit http://us.archive.ubuntu.com precise/restricted Translation-en             
Hit http://us.archive.ubuntu.com precise/universe Translation-en               
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en           
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en     
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en       
Hit http://extras.ubuntu.com precise Release.gpg                               
Hit http://extras.ubuntu.com precise Release                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                       
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en_US        
Ign http://us.archive.ubuntu.com lucid-backports/main Translation-en           
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/multiverse Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en_US  
Ign http://us.archive.ubuntu.com lucid-backports/restricted Translation-en     
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en_US    
Ign http://us.archive.ubuntu.com lucid-backports/universe Translation-en       
Ign http://extras.ubuntu.com precise/main Translation-en_US                    
Ign http://extras.ubuntu.com precise/main Translation-en                       
Err http://packages.medibuntu.org precise Release.gpg                          
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Hit http://packages.medibuntu.org precise Release                              
Ign http://packages.medibuntu.org precise/free amd64 Packages/DiffIndex        
Ign http://packages.medibuntu.org precise/non-free amd64 Packages/DiffIndex
Ign http://packages.medibuntu.org precise/free i386 Packages/DiffIndex    
Ign http://packages.medibuntu.org precise/non-free i386 Packages/DiffIndex     
Ign http://packages.medibuntu.org precise/free TranslationIndex                
Ign http://packages.medibuntu.org precise/non-free TranslationIndex            
Hit http://packages.medibuntu.org precise/free amd64 Packages                  
Hit http://packages.medibuntu.org precise/non-free amd64 Packages              
Hit http://packages.medibuntu.org precise/free i386 Packages                   
Hit http://packages.medibuntu.org precise/non-free i386 Packages               
Err http://ppa.launchpad.net precise Release.gpg                               
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Ign http://ppa.launchpad.net precise/main Sources/DiffIndex                    
Ign http://ppa.launchpad.net precise/main amd64 Packages/DiffIndex             
Ign http://ppa.launchpad.net precise/main i386 Packages/DiffIndex              
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main amd64 Packages                       
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_US                    
Ign http://ppa.launchpad.net precise/main Translation-en                       
Err http://security.ubuntu.com precise-security Release.gpg                    
  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)
Get:12 http://security.ubuntu.com precise-security Release [49.6 kB]           
Ign http://packages.medibuntu.org precise/free Translation-en_US               
Ign http://security.ubuntu.com precise-security/universe amd64 Packages/DiffIndex
Ign http://packages.medibuntu.org precise/free Translation-en
Ign http://security.ubuntu.com precise-security/main amd64 Packages/DiffIndex  
Ign http://security.ubuntu.com precise-security/multiverse amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/restricted amd64 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/universe i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/main i386 Packages/DiffIndex   
Ign http://security.ubuntu.com precise-security/multiverse i386 Packages/DiffIndex
Ign http://security.ubuntu.com precise-security/restricted i386 Packages/DiffIndex
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex    
Hit http://security.ubuntu.com precise-security/universe TranslationIndex      
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [71.0 kB]
Ign http://packages.medibuntu.org precise/non-free Translation-en_US
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [233 kB]
Ign http://packages.medibuntu.org precise/non-free Translation-en              
Get:15 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:16 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:17 http://security.ubuntu.com precise-security/universe i386 Packages [72.9 kB]
Get:18 http://security.ubuntu.com precise-security/main i386 Packages [243 kB]
Get:19 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,369 B]
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 2,351 kB in 22s (103 kB/s)                
W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

W: Failed to fetch http://packages.medibuntu.org/dists/precise/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://ppa.launchpad.net/n-muench/vlc/ubuntu/dists/precise/Release.gpg  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.
default@default-laptop:~$ 

```

Thank you very much  ubuntu forums.

---

### Post by QIII on 2013-04-01
This is a very old thread.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

Thanks,

QIII

*Thread **closed.***

---

