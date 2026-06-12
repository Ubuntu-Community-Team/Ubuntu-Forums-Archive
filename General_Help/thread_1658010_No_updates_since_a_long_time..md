---
title: "No updates since a long time."
date: 2011-01-02
forum: General Help
---

### Post by kanishkdudeja on 2011-01-02
Im not receiving any package updates since a month in my update manager.

Is it the same for everybody?

or is this because of this:

```
W:GPG error: http://repository.glx-dock.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877,

 W:Failed to fetch http://ppa.launchpad.net/specto/ppa/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

, W:Failed to fetch http://ppa.launchpad.net/specto/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

these are errors which my update manager comes up with when i try to check for updates.

---

### Post by cheapie on 2011-01-02
That PPA doesn't support versions above Karmic. That's because it's now in the official repos.

Go to System>Administration>Synaptic Package Manager, then Settings>Repositories, switch to the "Other Software" tab, find lines that look like this:

[http://ppa.launchpad.net/specto/ppa/ubuntu/](http://ppa.launchpad.net/specto/ppa/ubuntu/) maverick main
and
[http://ppa.launchpad.net/specto/ppa/ubuntu/](http://ppa.launchpad.net/specto/ppa/ubuntu/) maverick main (Source Code),
and uncheck them.

---

### Post by kanishkdudeja on 2011-01-02
okay..

ive done it..

but im not receiving updates..

is it only me whos not receiving or have the updates stopped coming ?

---

### Post by karthick87 on 2011-01-02
Can you post the output of,

```
sudo apt-get update
```

---

### Post by kanishkdudeja on 2011-01-02
```
kanishk@Inspiron-1525:~$ sudo apt-get update
[sudo] password for kanishk: 
Hit http://archive.canonical.com maverick Release.gpg                          
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Get:1 http://repository.glx-dock.org maverick Release.gpg [198B]               
Ign http://repository.glx-dock.org/ubuntu/ maverick/cairo-dock Translation-en  
Hit http://download.virtualbox.org maverick Release.gpg                        
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_IN    
Hit http://archive.canonical.com maverick Release                              
Ign http://www.geekconnection.org karmic/ Release.gpg                          
Ign http://www.geekconnection.org/remastersys/repository/ karmic/ Translation-en
Ign http://repository.glx-dock.org/ubuntu/ maverick/cairo-dock Translation-en_IN
Hit http://repository.glx-dock.org maverick Release                            
Ign http://repository.glx-dock.org maverick Release                            
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/non-free Translation-en_IN
Hit http://archive.canonical.com maverick/partner i386 Packages                
Ign http://www.geekconnection.org/remastersys/repository/ karmic/ Translation-en_IN
Ign http://www.geekconnection.org karmic/ Release                              
Ign http://repository.glx-dock.org maverick/cairo-dock i386 Packages/DiffIndex 
Hit http://download.virtualbox.org maverick Release                            
Hit http://repository.glx-dock.org maverick/cairo-dock i386 Packages           
Ign http://www.geekconnection.org karmic/ Packages/DiffIndex                   
Hit http://download.virtualbox.org maverick/non-free i386 Packages             
Ign http://www.geekconnection.org karmic/ Packages                             
Ign http://www.geekconnection.org karmic/ Packages                             
Hit http://www.geekconnection.org karmic/ Packages                             
Get:2 http://dl.google.com stable Release.gpg [197B]                           
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_IN  
Hit http://archive.ubuntu.com maverick Release.gpg                             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en             
Ign http://archive.ubuntu.com/ubuntu/ maverick/main Translation-en_IN          
Hit http://extras.ubuntu.com maverick Release.gpg                              
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_IN    
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en       
Ign http://archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_IN    
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en         
Ign http://archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_IN      
Get:3 http://dl.google.com stable Release [1,347B]                             
Hit http://archive.ubuntu.com maverick-updates Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en     
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_IN  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_IN           
Hit http://extras.ubuntu.com maverick Release                                  
Get:4 http://dl.google.com stable/main i386 Packages [1,076B]                  
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en 
Ign http://archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_IN
Hit http://archive.ubuntu.com maverick-security Release.gpg                    
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en    
Hit http://extras.ubuntu.com maverick/main Sources                             
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/main Translation-en_IN 
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_IN
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_IN
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://archive.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_IN
Hit http://archive.ubuntu.com maverick Release                                 
Hit http://archive.ubuntu.com maverick-updates Release                         
Hit http://archive.ubuntu.com maverick-security Release                        
Hit http://archive.ubuntu.com maverick/main Sources                            
Hit http://archive.ubuntu.com maverick/universe Sources                        
Hit http://archive.ubuntu.com maverick/multiverse Sources                      
Hit http://archive.ubuntu.com maverick/main i386 Packages                      
Hit http://archive.ubuntu.com maverick/restricted i386 Packages                
Hit http://archive.ubuntu.com maverick/universe i386 Packages                  
Hit http://archive.ubuntu.com maverick/multiverse i386 Packages                
Hit http://archive.ubuntu.com maverick-updates/main Sources                    
Hit http://archive.ubuntu.com maverick-updates/universe Sources                
Hit http://archive.ubuntu.com maverick-updates/multiverse Sources              
Hit http://archive.ubuntu.com maverick-updates/main i386 Packages              
Hit http://archive.ubuntu.com maverick-updates/restricted i386 Packages        
Hit http://archive.ubuntu.com maverick-updates/universe i386 Packages          
Hit http://archive.ubuntu.com maverick-updates/multiverse i386 Packages        
Hit http://archive.ubuntu.com maverick-security/main Sources                   
Hit http://archive.ubuntu.com maverick-security/universe Sources               
Hit http://archive.ubuntu.com maverick-security/multiverse Sources             
Hit http://archive.ubuntu.com maverick-security/main i386 Packages             
Hit http://archive.ubuntu.com maverick-security/restricted i386 Packages       
Hit http://archive.ubuntu.com maverick-security/universe i386 Packages         
Hit http://archive.ubuntu.com maverick-security/multiverse i386 Packages       
Fetched 2,818B in 11s (242B/s)                                                 
Reading package lists... Done
W: GPG error: http://repository.glx-dock.org maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1392A97E41317877

```

---

### Post by karthick87 on 2011-01-02
Run the following command in your terminal,
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1392A97E41317877
```

```
sudo apt-get update
```

---

### Post by kanishkdudeja on 2011-01-02
ive done it but still no updates..

---

### Post by kanishkdudeja on 2011-01-02
well,

my problem is pretty similar to this:

[http://ubuntuforums.org/showthread.php?t=1653875](http://ubuntuforums.org/showthread.php?t=1653875)

---

### Post by cheapie on 2011-01-02
I'm having the same problem, but I'm running maverick.

Here's my sources.list:

```

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
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
deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-proposed restricted main multiverse universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports restricted main multiverse universe
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://us.archive.ubuntu.com/ubuntu maverick-backports main restricted universe multiverse

# deb http://ftp.us.debian.org/debian lenny main
# deb-src http://ftp.de.debian.org/debian lenny main
# deb http://download.virtualbox.org/virtualbox/debian maverick non-free
# deb-src http://download.virtualbox.org/virtualbox/debian maverick non-free
deb http://download.virtualbox.org/virtualbox/debian maverick contrib
# deb-src http://download.virtualbox.org/virtualbox/debian maverick contrib
deb http://us.archive.ubuntu.com/ubuntu karmic main
deb-src http://us.archive.ubuntu.com/ubuntu karmic main

```

And my preferences:

```

Package: *
Pin: release a=karmic
Pin-Priority: 50

Package: same-gnome
Pin: release a=karmic
Pin-Priority: 1500

Package: gnome-games
Pin: release a=karmic
Pin-Priority: 1500

```

Apt-get update output:
```

root@cheapie-laptop:/home/cheapie/Desktop# apt-get update
Hit http://ppa.launchpad.net maverick Release.gpg                                                                                                                                              
Ign http://ppa.launchpad.net/damnvid/ppa/ubuntu/ maverick/main Translation-en                                                                                                                  
Ign http://ppa.launchpad.net/damnvid/ppa/ubuntu/ maverick/main Translation-en_US                                                                              
Hit http://download.virtualbox.org maverick Release.gpg                                                                                                       
Hit http://extras.ubuntu.com maverick Release.gpg                                                                                                             
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                             
Hit http://us.archive.ubuntu.com maverick Release.gpg                                                                                                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en                                                                                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                                       
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en                                                                          
Ign http://download.virtualbox.org/virtualbox/debian/ maverick/contrib Translation-en_US                                                                       
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US                                                                                           
Hit http://extras.ubuntu.com maverick Release                                                                                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en                                                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US                                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en                                                                                    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US                                                                                 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en                                                                
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US                                                             
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                                                                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en                                                                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US                                                                               
Hit http://security.ubuntu.com maverick-security Release.gpg                                                                                                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en                                                                                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US                                                                                
Hit http://download.virtualbox.org maverick Release                                                                                                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en                                                                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en                                                                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US                                                                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en                                                                              
Hit http://extras.ubuntu.com maverick/main i386 Packages                                                                                                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US                                                                           
Hit http://us.archive.ubuntu.com karmic-backports Release.gpg                                                                            
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/main Translation-en                                                            
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en                                                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en                                                       
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US                                                    
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US                                                      
Hit http://download.virtualbox.org maverick/contrib i386 Packages                                                                        
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/main Translation-en_US                                                         
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/multiverse Translation-en                                
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/multiverse Translation-en_US                             
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/restricted Translation-en                                
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/restricted Translation-en_US                             
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/universe Translation-en                                  
Ign http://us.archive.ubuntu.com/ubuntu/ karmic-backports/universe Translation-en_US                               
Hit http://security.ubuntu.com maverick-security Release                                                           
Get:1 http://us.archive.ubuntu.com maverick-proposed Release.gpg [198B]                                            
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en               
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US          
Hit http://security.ubuntu.com maverick-security/main Sources                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en         
Get:2 http://dl.google.com stable Release.gpg [197B]                                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US      
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg                            
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US               
Hit http://security.ubuntu.com maverick-security/restricted Sources                        
Hit http://security.ubuntu.com maverick-security/universe Sources                          
Hit http://security.ubuntu.com maverick-security/multiverse Sources                        
Hit http://security.ubuntu.com maverick-security/main i386 Packages                        
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages                  
Hit http://security.ubuntu.com maverick-security/universe i386 Packages                    
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages                  
Get:3 http://dl.google.com stable Release [1,347B]                                         
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Hit http://ppa.launchpad.net maverick Release                        
Get:4 http://dl.google.com stable/main i386 Packages [735B]          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ karmic/main Translation-en
Hit http://ppa.launchpad.net maverick/main Sources
Ign http://us.archive.ubuntu.com/ubuntu/ karmic/main Translation-en_US
Hit http://us.archive.ubuntu.com maverick Release
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://ppa.launchpad.net maverick/main i386 Packages             
Hit http://us.archive.ubuntu.com karmic-backports Release
Get:5 http://us.archive.ubuntu.com maverick-proposed Release [31.4kB]
Hit http://us.archive.ubuntu.com maverick-backports Release
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/main i386 Packages
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com karmic-backports/main i386 Packages
Hit http://us.archive.ubuntu.com karmic-backports/restricted i386 Packages                                                                                                                     
Hit http://us.archive.ubuntu.com karmic-backports/universe i386 Packages                                                                                                                       
Hit http://us.archive.ubuntu.com karmic-backports/multiverse i386 Packages                                                                                                                     
Get:6 http://us.archive.ubuntu.com maverick-proposed/restricted i386 Packages [1,797B]                                                                                                         
Get:7 http://us.archive.ubuntu.com maverick-proposed/main i386 Packages [36.7kB]                                                                                                               
Get:8 http://us.archive.ubuntu.com maverick-proposed/multiverse i386 Packages [608B]                                                                                                           
Get:9 http://us.archive.ubuntu.com maverick-proposed/universe i386 Packages [17.5kB]                                                                                                           
Hit http://us.archive.ubuntu.com maverick-backports/restricted i386 Packages                                                                                                                   
Hit http://us.archive.ubuntu.com maverick-backports/main i386 Packages                                                                                                                         
Hit http://us.archive.ubuntu.com maverick-backports/multiverse i386 Packages                                                                                                                   
Hit http://us.archive.ubuntu.com maverick-backports/universe i386 Packages                                                                                                                     
Hit http://us.archive.ubuntu.com karmic/main Sources                                                                                                                                           
Hit http://us.archive.ubuntu.com karmic/main i386 Packages                                                                                                                                     
Fetched 90.4kB in 6s (14.0kB/s)                                                                                                                                                                
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick-backports_main_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick-backports_restricted_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick-backports_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse i386 Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_maverick-backports_multiverse_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

---

### Post by kanishkdudeja on 2011-01-02
@cheapie:

even im running maverick.

---

