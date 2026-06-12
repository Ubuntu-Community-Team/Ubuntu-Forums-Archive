---
title: "Problems updating maverick"
date: 2011-04-12
forum: General Help
---

### Post by beliyyal on 2011-04-12
Hey guys, how's it going? Well, I am having a bit of a problem here. Every time I try to check for updates in the update manager, I get this error:
```
Failed to download repository information

Check your Internet connection.
```
And in the details, it says:
```
W:GPG error: http://deb.torproject.org experimental-lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810, W:Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```
I tried to update in terminal too, this is what I got:
```
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Get:1 http://deb.torproject.org experimental-lucid Release.gpg [489B]          
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/loell/ppa/ubuntu/ maverick/main Translation-en    
Ign http://ppa.launchpad.net/loell/ppa/ubuntu/ maverick/main Translation-en_US 
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://deb.torproject.org/torproject.org/ experimental-lucid/main Translation-en
Ign http://deb.torproject.org/torproject.org/ experimental-lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                              
Get:2 http://deb.torproject.org experimental-lucid Release [2,247B]            
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://deb.torproject.org experimental-lucid Release                       
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://us.archive.ubuntu.com maverick-updates Release                      
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Ign http://ppa.launchpad.net maverick/main Sources                             
Ign http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://us.archive.ubuntu.com maverick/restricted Sources         
Hit http://us.archive.ubuntu.com maverick/universe Sources           
Hit http://us.archive.ubuntu.com maverick/multiverse Sources         
Hit http://us.archive.ubuntu.com maverick/main i386 Packages         
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages   
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages     
Ign http://deb.torproject.org experimental-lucid/main i386 Packages/DiffIndex
Ign http://ppa.launchpad.net maverick/main Sources                   
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources       
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources 
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources   
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources 
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages 
Ign http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://ppa.launchpad.net maverick/main Sources                   
  404  Not Found
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
Ign http://deb.torproject.org experimental-lucid/main i386 Packages
Ign http://deb.torproject.org experimental-lucid/main i386 Packages
Hit http://deb.torproject.org experimental-lucid/main i386 Packages
Fetched 2,736B in 4s (585B/s)
W: GPG error: http://deb.torproject.org experimental-lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 74A941BA219EC810
W: Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

Does anyone know how to fix this?

---

### Post by sanguinoso on 2011-04-12
The tor project error is because you don't have their GPG key. Run this to add the key ```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

```

As for the rest, can you post the results to the command: ```
cat /etc/apt/sources.list
```

---

### Post by beliyyal on 2011-04-12
> **sanguinoso said:**
> As for the rest, can you post the results to the command: ```
cat /etc/apt/sources.list
```

```
dalton@Beliyyal:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

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

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main
# deb-src http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu lucid main
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb http://deb.torproject.org/torproject.org experimental-lucid main
deb http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu maverick main
deb-src http://ppa.launchpad.net/jre-phoenix/ppa/ubuntu maverick main
```

> **sanguinoso said:**
> The tor project error is because you don't have their GPG key. Run this to add the key ```
gpg --keyserver keys.gnupg.net --recv 886DDD89
gpg --export A3C4F0F979CAA22CDBA8F512EE8CBC9E886DDD89 | sudo apt-key add -

```
Thanks for the tor key :D

---

### Post by Old_Grey_Wolf on 2011-04-12
If that didn't work, the key can be added with these commands
```
gpg --keyserver keyserver.ubuntu.com --recv 74A941BA219EC810
gpg --export --armor 74A941BA219EC810 | sudo apt-key add -
```

---

### Post by sanguinoso on 2011-04-15
Try commenting out the last two lines in the file with ```
sudo gedit /etc/apt/sources.list
``` 

(Place a '#' (without the quotes) in front of the line.)

Then run from the terminal 
```
sudo apt-get update
```

---

### Post by KegHead on 2011-04-15
Hi!

Also run in terminal;

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo aptitude install linux-image -f

This will bring you up to date!

KegHead

---

### Post by sanguinoso on 2011-04-15
> **KegHead said:**
> Hi!

Also run in terminal;

sudo apt-get upgrade -f

sudo apt-get dist-upgrade -f

sudo aptitude install linux-image -f

This will bring you up to date!

KegHead

While true, the point I had in asking for just the update to see if the repositories were working again so that beliyyal could continue using the update manager.

---

### Post by beliyyal on 2011-04-15
> **sanguinoso said:**
> Try commenting out the last two lines in the file with ```
sudo gedit /etc/apt/sources.list
``` 

(Place a '#' (without the quotes) in front of the line.)

Then run from the terminal 
```
sudo apt-get update
```
Ok, I did this, but this is what I got in terminal:```
dalton@Beliyyal:~$ sudo apt-get update
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://deb.torproject.org experimental-lucid Release.gpg                   
Ign http://deb.torproject.org/torproject.org/ experimental-lucid/main Translation-en
Ign http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/loell/ppa/ubuntu/ maverick/main Translation-en    
Ign http://ppa.launchpad.net/loell/ppa/ubuntu/ maverick/main Translation-en_US 
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://extras.ubuntu.com maverick Release                                  
Ign http://deb.torproject.org/torproject.org/ experimental-lucid/main Translation-en_US
Hit http://deb.torproject.org experimental-lucid Release                       
Hit http://security.ubuntu.com maverick-security/main Sources                  
Ign http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Ign http://deb.torproject.org experimental-lucid/main i386 Packages  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release                    
Ign http://ppa.launchpad.net maverick/main i386 Packages                       
Ign http://deb.torproject.org experimental-lucid/main i386 Packages  
Hit http://us.archive.ubuntu.com maverick-updates Release
Ign http://ppa.launchpad.net maverick/main Sources                             
Hit http://us.archive.ubuntu.com maverick/main Sources               
Hit http://deb.torproject.org experimental-lucid/main i386 Packages  
Hit http://us.archive.ubuntu.com maverick/restricted Sources         
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Ign http://ppa.launchpad.net maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Err http://ppa.launchpad.net maverick/main Sources
  404  Not Found
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Err http://ppa.launchpad.net maverick/main i386 Packages
  404  Not Found
W: Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/loell/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by sanguinoso on 2011-04-15
The problem is I believe that that particular repository hasn't updated their source for maverick yet. You can see the distros here [http://ppa.launchpad.net/loell/ubuntu/dists/](http://ppa.launchpad.net/loell/ubuntu/dists/). Can you go into Update Manager -> Settings -> Other Software and see if there is a [http://ppa.launchpad.net/loell/](http://ppa.launchpad.net/loell/) entry?

---

### Post by beliyyal on 2011-04-16
> **sanguinoso said:**
> The problem is I believe that that particular repository hasn't updated their source for maverick yet. You can see the distros here [http://ppa.launchpad.net/loell/ubuntu/dists/](http://ppa.launchpad.net/loell/ubuntu/dists/). Can you go into Update Manager -> Settings -> Other Software and see if there is a [http://ppa.launchpad.net/loell/](http://ppa.launchpad.net/loell/) entry?

[img]http://img840.imageshack.us/img840/214/screenshotsoftwaresourc.png[/img]

---

### Post by beliyyal on 2011-04-19
bump

---

### Post by plucky on 2011-04-19
Why don't you un-tick both the PPAs for the Loell project because,as sanguinoso says, those PPAs do not exist?

and that is the cause of > Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found

[http://ppa.launchpad.net/loell/ubuntu/dists/](http://ppa.launchpad.net/loell/ubuntu/dists/)

Also I would disable the Tor project PPA as it is for Lucid.

Good Luck

---

### Post by sanguinoso on 2011-04-19
> **plucky said:**
> Why don't you un-tick both the PPAs for the Loell project because,as sanguinoso says, those PPAs do not exist?

and that is the cause of 

[http://ppa.launchpad.net/loell/ubuntu/dists/](http://ppa.launchpad.net/loell/ubuntu/dists/)

Also I would disable the Tor project PPA as it is for Lucid.

Good Luck

This is correct, untick those two and re run your updates.

---

