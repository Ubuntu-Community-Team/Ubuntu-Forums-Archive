---
title: "Help me reinstall software mananger!"
date: 2012-03-08
forum: General Help
---

### Post by 4042966262 on 2012-03-08
**oh no!! what should i do!?:confused:**
coffeegulpers@coffeegulpers:~$ sudo apt-get remove software-center
[sudo] password for coffeegulpers: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center ubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 8 not upgraded.
After this operation, 1,675 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 229229 files and directories currently installed.)
Removing ubuntu-desktop ...
Removing software-center ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
coffeegulpers@coffeegulpers:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: software-center-aptdaemon-plugins but it is not installable
                   Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
                   Depends: python-gi-cairo but it is not installable
                   Depends: python-apt (>= 0.8.3ubuntu4) but 0.8.0ubuntu9 is to be installed
                   Depends: python-debtagshw but it is not installable
E: Unable to correct problems, you have held broken packages.
coffeegulpers@coffeegulpers:~$

---

### Post by jerrrys on 2012-03-08
I seen you post before you edited.  In terminal enter and post:

**cat /etc/apt/sources.list**

---

### Post by 4042966262 on 2012-03-08
> **jerrrys said:**
> I seen you post before you edited.  In terminal enter and post:

**cat /etc/apt/sources.list**

coffeegulpers@coffeegulpers:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric-security multiverse
# deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) jaunty main
deb [http://apt.boxee.tv](http://apt.boxee.tv) hardy main
deb-src [http://apt.boxee.tv](http://apt.boxee.tv) hardy main
deb [http://apt.boxee.tv](http://apt.boxee.tv) intrepid main
deb-src [http://apt.boxee.tv](http://apt.boxee.tv) intrepid main
deb [http://ppa.launchpad.net/cdekter/ppa/ubuntu](http://ppa.launchpad.net/cdekter/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/cdekter/ppa/ubuntu](http://ppa.launchpad.net/cdekter/ppa/ubuntu) oneiric main
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
coffeegulpers@coffeegulpers:~$

---

### Post by jerrrys on 2012-03-08
Your running Oneiric, you want only oneiric software sources.

Open a terminal and enter:

gksudo nautilus

and navigate to /etc/apt/sources.list

Make a copy of the sources.list folder.  Then open up the sources.list and comment (#) out anything thats not oneiric.

reload sources by using your package manager or in terminal enter:

sudo apt-get update

Any errors?

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by 4042966262 on 2012-03-08
new sources..
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu oneiric main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu oneiric-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu oneiric universe
deb-src http://archive.ubuntu.com/ubuntu oneiric universe
deb http://archive.ubuntu.com/ubuntu oneiric-updates universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu oneiric multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric multiverse
deb http://archive.ubuntu.com/ubuntu oneiric-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu oneiric main
deb-src http://extras.ubuntu.com/ubuntu oneiric main

deb http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb-src http://archive.ubuntu.com/ubuntu oneiric-security main restricted
deb http://archive.ubuntu.com/ubuntu oneiric-security universe
deb-src http://archive.ubuntu.com/ubuntu oneiric-security universe
deb http://archive.ubuntu.com/ubuntu oneiric-security multiverse
deb-src http://archive.ubuntu.com/ubuntu oneiric-security multiverse
# deb http://archive.canonical.com/ lucid partner
#deb-src http://archive.canonical.com/ lucid partner
#deb http://archive.canonical.com/ lucid partner
#deb-src http://archive.canonical.com/ lucid partner
#deb http://ppa.launchpad.net/jonabeck/ppa/ubuntu jaunty main
#deb http://apt.boxee.tv hardy main
#deb-src http://apt.boxee.tv hardy main
#deb http://apt.boxee.tv intrepid main
#deb-src http://apt.boxee.tv intrepid main
deb http://ppa.launchpad.net/cdekter/ppa/ubuntu oneiric main
deb-src http://ppa.launchpad.net/cdekter/ppa/ubuntu oneiric main
#deb http://download.tuxfamily.org/3v1deb feisty eyecandy
#deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

[B]update code-no errors
[/B]```
coffeegulpers@coffeegulpers:~$ sudo apt-get update
[sudo] password for coffeegulpers: 
Ign http://dl.google.com stable InRelease                                      
Ign http://ppa.launchpad.net oneiric InRelease                                 
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://ppa.launchpad.net oneiric InRelease                       
Ign http://extras.ubuntu.com oneiric InRelease                                 
Ign http://archive.ubuntu.com oneiric InRelease                                
Ign http://archive.ubuntu.com oneiric-updates InRelease              
Ign http://archive.ubuntu.com oneiric-security InRelease                       
Get:1 http://dl.google.com stable Release.gpg [198 B]                          
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Get:2 http://extras.ubuntu.com oneiric Release.gpg [72 B]                      
Hit http://archive.ubuntu.com oneiric Release.gpg                              
Get:3 http://dl.google.com stable Release [1,347 B]                            
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric Release                                   
Get:4 http://archive.ubuntu.com oneiric-updates Release.gpg [198 B]            
Get:5 http://dl.google.com stable/main i386 Packages [759 B]                   
Hit http://ppa.launchpad.net oneiric Release.gpg                               
Hit http://extras.ubuntu.com oneiric/main Sources                              
Hit http://archive.ubuntu.com oneiric-security Release.gpg                     
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://extras.ubuntu.com oneiric/main i386 Packages                        
Ign http://extras.ubuntu.com oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric Release                                  
Hit http://ppa.launchpad.net oneiric Release                                   
Get:6 http://archive.ubuntu.com oneiric-updates Release [40.8 kB]              
Hit http://ppa.launchpad.net oneiric Release                                   
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric-security Release                         
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/main Sources                   
Hit http://archive.ubuntu.com oneiric/restricted Sources                       
Hit http://archive.ubuntu.com oneiric/universe Sources                         
Hit http://archive.ubuntu.com oneiric/multiverse Sources             
Hit http://archive.ubuntu.com oneiric/main i386 Packages             
Hit http://archive.ubuntu.com oneiric/restricted i386 Packages                 
Hit http://archive.ubuntu.com oneiric/universe i386 Packages                   
Hit http://archive.ubuntu.com oneiric/multiverse i386 Packages                 
Hit http://ppa.launchpad.net oneiric/main Sources                              
Hit http://ppa.launchpad.net oneiric/main i386 Packages                        
Ign http://ppa.launchpad.net oneiric/main TranslationIndex                     
Hit http://archive.ubuntu.com oneiric/main TranslationIndex                    
Hit http://archive.ubuntu.com oneiric/multiverse TranslationIndex              
Hit http://archive.ubuntu.com oneiric/restricted TranslationIndex    
Hit http://archive.ubuntu.com oneiric/universe TranslationIndex      
Get:7 http://archive.ubuntu.com oneiric-updates/main Sources [128 kB]
Ign http://extras.ubuntu.com oneiric/main Translation-en_US                    
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://extras.ubuntu.com oneiric/main Translation-en                      
Get:8 http://archive.ubuntu.com oneiric-updates/restricted Sources [1,337 B]   
Ign http://dl.google.com stable/main Translation-en                            
Get:9 http://archive.ubuntu.com oneiric-updates/universe Sources [46.5 kB]     
Get:10 http://archive.ubuntu.com oneiric-updates/multiverse Sources [3,648 B]  
Get:11 http://archive.ubuntu.com oneiric-updates/main i386 Packages [294 kB]   
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Ign http://ppa.launchpad.net oneiric/main Translation-en_US                    
Ign http://ppa.launchpad.net oneiric/main Translation-en                       
Get:12 http://archive.ubuntu.com oneiric-updates/restricted i386 Packages [2,968 B]
Get:13 http://archive.ubuntu.com oneiric-updates/universe i386 Packages [102 kB]
Get:14 http://archive.ubuntu.com oneiric-updates/multiverse i386 Packages [6,359 B]
Get:15 http://archive.ubuntu.com oneiric-updates/main TranslationIndex [74 B]  
Get:16 http://archive.ubuntu.com oneiric-updates/multiverse TranslationIndex [72 B]
Get:17 http://archive.ubuntu.com oneiric-updates/restricted TranslationIndex [71 B]
Get:18 http://archive.ubuntu.com oneiric-updates/universe TranslationIndex [73 B]
Hit http://archive.ubuntu.com oneiric-security/main Sources                    
Hit http://archive.ubuntu.com oneiric-security/restricted Sources              
Hit http://archive.ubuntu.com oneiric-security/universe Sources                
Hit http://archive.ubuntu.com oneiric-security/multiverse Sources              
Hit http://archive.ubuntu.com oneiric-security/main i386 Packages              
Hit http://archive.ubuntu.com oneiric-security/restricted i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/universe i386 Packages          
Hit http://archive.ubuntu.com oneiric-security/multiverse i386 Packages        
Hit http://archive.ubuntu.com oneiric-security/main TranslationIndex           
Hit http://archive.ubuntu.com oneiric-security/multiverse TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/restricted TranslationIndex     
Hit http://archive.ubuntu.com oneiric-security/universe TranslationIndex       
Hit http://archive.ubuntu.com oneiric/main Translation-en                      
Hit http://archive.ubuntu.com oneiric/multiverse Translation-en                
Hit http://archive.ubuntu.com oneiric/restricted Translation-en                
Hit http://archive.ubuntu.com oneiric/universe Translation-en                  
Get:19 http://archive.ubuntu.com oneiric-updates/main Translation-en [138 kB]  
Hit http://archive.ubuntu.com oneiric-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/restricted Translation-en        
Hit http://archive.ubuntu.com oneiric-updates/universe Translation-en          
Hit http://archive.ubuntu.com oneiric-security/main Translation-en             
Hit http://archive.ubuntu.com oneiric-security/multiverse Translation-en       
Hit http://archive.ubuntu.com oneiric-security/restricted Translation-en       
Hit http://archive.ubuntu.com oneiric-security/universe Translation-en         
Fetched 766 kB in 25s (29.8 kB/s)                                              
Reading package lists... Done
coffeegulpers@coffeegulpers:~$ 

```

---

### Post by pavi_elex on 2012-03-09
which version are you using of ubuntu?
Go to synaptic package manager --> Edit --> fix broken packages
Now try to install
Just try to install any other software from terminal, are you facing this problem in software-center only or every software is giving trouble?
i have fresh apt of some versions of ubuntu, i can share it with you.

---

### Post by 4042966262 on 2012-03-10
just tried..

coffeegulpers@coffeegulpers:~$ sudo apt-get install software-center
[sudo] password for coffeegulpers: 
Sorry, try again.
[sudo] password for coffeegulpers: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
coffeegulpers@coffeegulpers:~$ sudo apt-get install software-center
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
coffeegulpers@coffeegulpers:~$ sudo apt-get install software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 software-center : Depends: software-center-aptdaemon-plugins but it is not installable
                   Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
                   Depends: python-gi-cairo but it is not installable
                   Depends: python-apt (>= 0.8.3ubuntu4) but 0.8.0ubuntu9 is to be installed
                   Depends: python-debtagshw but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by 4042966262 on 2012-03-10
oops double post!

---

### Post by 4042966262 on 2012-03-10
> **pavi_elex said:**
> which version are you using of ubuntu?
Go to synaptic package manager --> Edit --> fix broken packages
Now try to install
Just try to install any other software from terminal, are you facing this problem in software-center only or every software is giving trouble?
i have fresh apt of some versions of ubuntu, i can share it with you.

ubuntu 11.10 its all software..

---

### Post by jerrrys on 2012-03-11
Doesn't always work, but you can force the install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=force+install+package+program&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=force+install+package+program&sa=Search&cof=FORID:9)

---

### Post by 4042966262 on 2012-03-11
> **jerrrys said:**
> Doesn't always work, but you can force the install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=force+install+package+program&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=force+install+package+program&sa=Search&cof=FORID:9)
**i tried thia**

tagzmeadmin@coffeegulpers:~$ gsku nautilus
No command 'gsku' found, did you mean:
 Command 'gski' from package 'ski' (universe)
 Command 'gksu' from package 'gksu' (main)
gsku: command not found
tagzmeadmin@coffeegulpers:~$ gsku nautilus
No command 'gsku' found, did you mean:
 Command 'gski' from package 'ski' (universe)
 Command 'gksu' from package 'gksu' (main)
gsku: command not found
tagzmeadmin@coffeegulpers:~$ gksudo nautilus
Initializing nautilus-gdu extension
** (nautilus:17266): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
totem-video-thumbnailer: 'file:///home/coffeegulpers/Downloads/20120129-message-audio-high.mp3' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///home/coffeegulpers/Downloads/Rappin%20Drakken%20Lyrics.mp3' isn't thumbnailable
Reason: Media contains no supported video streams.
totem-video-thumbnailer: 'file:///home/coffeegulpers/Downloads/You%20Kick%20My%20Dog%20Prank.mp3' isn't thumbnailable
Reason: Media contains no supported video streams.

--- Hash table keys for warning below:
--> inode/directory
--> Tagzme Admin
--> Kimballs (password coffee)
--> l2049
--> tagzmeadmin
--> kimballspc
--> root

--- Hash table keys for warning below:
--> file:///
--> file:///root
--> file:///home
--> file:///home/coffeegulpers
Shutting down nautilus-gdu extension
Error: Couldn't open file '/home/coffeegulpers/Downloads/303-418.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/Alex_Rider_08_-_Crocodile_Tear.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/CAcert_Styleguide.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/DIRECTV_D10-300.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/Employment_Application.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/HC00520693.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/How to Talk So People Listen The Real Key to Job Success ~ [TSG].pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/howtousepinterestforbusiness.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/Hunger Games 3 - Mockingjay.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/Interview Skills That Win The Job.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/Publix420.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/readme_1.8.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/river_addon-1.8.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/socialize-1.8.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/tagzme.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/tagzme_stickers.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/tagzme_stickers (1).pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/The_Hunger_Games_1_-_The_Hunger_Games.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/home/coffeegulpers/Downloads/The_Hunger_Games_2_-_Catching_Fire.pdf': Permission denied.
Error loading document: Error opening file: Permission denied

** (nautilus:17266): WARNING **: bookmark uri is file:///root, but expected file:///

(nautilus:17266): Eel-WARNING **: "unique eel_ref_str" hash table still has 7 elements at quit time (keys above)

(nautilus:17266): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time (keys above)
tagzmeadmin@coffeegulpers:~$ gksudo nautilus
Initializing nautilus-gdu extension
** (nautilus:17394): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged

--- Hash table keys for warning below:
--> inode/directory
--> Tagzme Admin
--> l2049
--> Kimballs (password coffee)
--> tagzmeadmin
--> kimballspc
--> root

--- Hash table keys for warning below:
--> file:///
--> file:///home
--> file:///home/coffeegulpers
Shutting down nautilus-gdu extension

** (nautilus:17394): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

(nautilus:17394): Eel-WARNING **: "unique eel_ref_str" hash table still has 7 elements at quit time (keys above)

(nautilus:17394): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time (keys above)
tagzmeadmin@coffeegulpers:~$ gksudo nautilus
Initializing nautilus-gdu extension
** (nautilus:17436): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
sudo apt-get update; sudo apt-get --purge --reinstall install software-center software-properties-common software-properties-gtk


--- Hash table keys for warning below:
--> inode/directory
--> Tagzme Admin
--> Kimballs (password coffee)
--> l2049
--> tagzmeadmin
--> kimballspc
--> root

--- Hash table keys for warning below:
--> file:///
--> file:///home/tagzmeadmin/Desktop/boxee/usr/share
--> file:///home/tagzmeadmin
--> file:///home
--> file:///root
--> file:///home/tagzmeadmin/Desktop
--> file:///home/tagzmeadmin/Desktop/boxee/usr
--> file:///home/tagzmeadmin/Desktop/boxee
Shutting down nautilus-gdu extension

(nautilus:17436): Eel-WARNING **: "unique eel_ref_str" hash table still has 7 elements at quit time (keys above)

(nautilus:17436): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 8 elements at quit time (keys above)
tagzmeadmin@coffeegulpers:~$ sudo apt-get update; sudo apt-get --purge --reinstall install software-center software-properties-common software-properties-gtk
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [759 B]            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources                       
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Fetched 2,376 B in 9s (261 B/s)                                                
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
tagzmeadmin@coffeegulpers:~$ 
tagzmeadmin@coffeegulpers:~$ sudo apt-get update; sudo apt-get --purge --reinstall install software-center software-properties-common software-properties-gtk
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347 B]                            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                                 
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [759 B]         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease                                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease                        
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security InRelease             
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                     
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg                              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release.gpg           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release                                  
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                          
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Sources          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main i386 Packages    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/main Translation-en   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en                       
Fetched 2,304 B in 6s (358 B/s)                                                
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
[B]
The following packages have unmet dependencies:
 software-center : Depends: software-center-aptdaemon-plugins but it is not installable
                   Depends: gir1.2-glib-2.0 (>= 1.31) but 1.30.0-0ubuntu2 is to be installed
                   Depends: python-gi-cairo but it is not installable
                   Depends: python-apt (>= 0.8.3ubuntu4) but 0.8.0ubuntu9 is to be installed
                   Depends: python-debtagshw but it is not installable
E: Unable to correct problems, you have held broken packages.[/B]
tagzmeadmin@coffeegulpers:~$ 

what in the world... sorry that made no sonce to me.
i tried this

---

