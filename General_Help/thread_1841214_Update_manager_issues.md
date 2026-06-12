---
title: "Update manager issues"
date: 2011-09-09
forum: General Help
---

### Post by TrialSizeDoveBar on 2011-09-09
Error is as follows: 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/edevelop.org_pkg-e_ubuntu_dists_feisty_e17_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

I've tried the following to no avail

sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update

---

### Post by Rubi1200 on 2011-09-09
Hi and welcome to the forums :-)

Try the following:

```
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update
```
Report back with error messages.

---

### Post by dcstar on 2011-09-09
> **TrialSizeDoveBar said:**
> Error is as follows: 

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/edevelop.org_pkg-e_ubuntu_dists_**feisty**_e17_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


7.04 stopped being supported in October 2008, there are NO repositories to connect to any more.

---

### Post by TrialSizeDoveBar on 2011-09-09
same error:

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/edevelop.org_pkg-e_ubuntu_dists_feisty_e17_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'


I'm not sure why it's checking for feisty packages, I'm definitely using natty.

---

### Post by Rubi1200 on 2011-09-09
Post the output of this command:

```
cat /etc/apt/sources.list
```

---

### Post by TrialSizeDoveBar on 2011-09-09
```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty universe
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ natty-updates multiverse

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
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
deb http://afterxleep.com/apt feisty main
deb http://apt.mepis.org/6.0/ mepis main
deb http://archive.canonical.com/ubuntu feisty-commercial main
deb http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
deb-src http://archive.czessi.net/ubuntu feisty main restricted universe multiverse preview
deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
deb http://au.ubuntu.cafuego.net feisty-cafuego secondlife all internode google bcm43xx
deb-src http://au.ubuntu.cafuego.net feisty-cafuego secondlife all internode google bcm43xx
deb http://blognux.free.fr/debian unstable main
deb http://bluez.sourceforge.net/download/debian/ ./
deb http://cl.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb http://cl.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe
deb-src http://cl.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe
deb http://cl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://cl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://cl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://cl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://deb.opera.com/opera etch non-free
deb http://debian.o-hand.com feisty/
deb http://debs.peadrop.com feisty backports
deb-src http://debs.peadrop.com feisty backports
deb http://dl.google.com/linux/deb/ stable non-free
deb http://dl.ivtvdriver.org/ubuntu feisty all
deb-src http://dl.ivtvdriver.org/ubuntu feisty all
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb http://download.tuxfamily.org/3v1deb feisty eyecandy suspend2
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy suspend2
deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb http://edevelop.org/pkg-e/ubuntu feisty e17
deb-src http://edevelop.org/pkg-e/ubuntu feisty e17
deb http://elisa.fluendo.com/packages feisty main
deb http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz
deb-src http://ftp.musicbrainz.org/pub/musicbrainz/users/luks/ubuntu feisty musicbrainz
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets all
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty screenlets all
deb http://home.eng.iastate.edu/~superm1 feisty all
deb-src http://home.eng.iastate.edu/~superm1 feisty all
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free
deb http://mirror.ubuntulinux.nl feisty-seveas all
deb-src http://mirror.ubuntulinux.nl feisty-seveas all
deb http://morgoth.free.fr/ubuntu feisty-backports main
deb-src http://morgoth.free.fr/ubuntu feisty-backports main
deb http://people.ubuntu.com/~seb128/deb ./
deb-src http://people.ubuntu.com/~seb128/deb ./
deb http://pkg-initng.alioth.debian.org/debian/ experimental main
deb http://pkg-voip.buildserver.net/ubuntu feisty main
deb-src http://pkg-voip.buildserver.net/ubuntu feisty main
deb http://repository.debuntu.org/ feisty multiverse
deb-src http://repository.debuntu.org/ feisty multiverse
deb http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe
deb http://snapshots.ekiga.net/ubuntu/ feisty main
deb-src http://snapshots.ekiga.net/ubuntu/ feisty main
deb http://snapshots.seconix.com/ubuntu/ feisty main
deb-src http://snapshots.seconix.com/ubuntu/ feisty main
deb http://snapshots.voxgratia.org/ubuntu/ feisty main
deb-src http://snapshots.voxgratia.org/ubuntu/ feisty main
deb http://ubuntu.beryl-project.org feisty main
deb-src http://ubuntu.beryl-project.org feisty main
deb http://ubuntu.geole.info/ feisty universe multiverse
deb http://ubuntu.moshen.de feisty multimedia misc eyecandy
deb-src http://ubuntu.moshen.de feisty multimedia misc eyecandy
deb http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-intern uniklu
deb-src http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/ feisty uniklu-intern uniklu
deb http://ubuntusoftware.info/ feisty all
deb http://vdlinux.sourceforge.jp/ experimental all
deb-src http://vdlinux.sourceforge.jp/ experimental all
deb http://wine.budgetdedicated.com/apt feisty main
deb-src http://wine.budgetdedicated.com/apt feisty main
deb http://www.getautomatix.com/apt feisty main
deb http://www.imbrandon.com/packages feisty all beryl
deb-src http://www.imbrandon.com/packages feisty all beryl
deb http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
deb-src http://www.in.fh-merseburg.de/~jahn/opensync-0.21/ feisty main
deb-src http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/ ./
deb http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/ ./
deb http://www.linux2go.dk/ubuntu feisty main
deb-src http://www.linux2go.dk/ubuntu feisty main
deb http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
deb-src http://www.mpe.mpg.de/~ach/kubuntu/feisty ./
deb http://www.tvfreeplayer.com/linux/falcon feisty all mods vlc
deb-src http://www.tvfreeplayer.com/linux/falcon feisty all mods vlc
deb http://www.uv.es/cuan/repos feisty extras
deb-src http://www.uv.es/cuan/repos feisty extras

```

---

### Post by Enigmapond on 2011-09-09
Are you running 10.10 or 11.04? You have both repos listed.

---

### Post by howefield on 2011-09-09
Remove the lines with feisty in them or place a # sign in front of them. 

```
gksudo gedit /etc/apt/sources.list
``` 

Save and try again.

---

### Post by TrialSizeDoveBar on 2011-09-09
Works great now, thanks guys!  Installed updates and rebooted, no errors.  Though when I did the update in terminal there were a few errors, doesn't seem to be causing any trouble right now.

```
Ign http://security.ubuntu.com natty-security InRelease
Ign http://deb.opera.com etch InRelease                                        
Get:1 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Ign http://deb.opera.com etch Release.gpg                                      
Ign http://blognux.free.fr unstable InRelease                                  
Get:2 http://security.ubuntu.com natty-security Release [31.4 kB]              
Ign http://deb.opera.com etch Release                                          
Ign http://deb.opera.com etch/non-free TranslationIndex                        
Ign http://blognux.free.fr unstable Release.gpg                                
Get:3 http://security.ubuntu.com natty-security/main Sources [66.2 kB]         
Ign http://apt.mepis.org mepis InRelease                                       
Get:4 http://security.ubuntu.com natty-security/restricted Sources [14 B]      
Get:5 http://security.ubuntu.com natty-security/universe Sources [10.6 kB]     
Get:6 http://security.ubuntu.com natty-security/multiverse Sources [650 B]     
Get:7 http://security.ubuntu.com natty-security/main i386 Packages [174 kB]    
Ign http://www.kiberpipa.org ./ InRelease                                      
Ign http://blognux.free.fr unstable Release                                    
Ign http://www.kiberpipa.org ./ Release.gpg                                    
Err http://deb.opera.com etch/non-free i386 Packages                           
  404  Not Found
Ign http://www.kiberpipa.org ./ Release                                        
Get:8 http://security.ubuntu.com natty-security/restricted i386 Packages [14 B]
Get:9 http://security.ubuntu.com natty-security/universe i386 Packages [36.2 kB]
Get:10 http://security.ubuntu.com natty-security/multiverse i386 Packages [2,071 B]
Ign http://security.ubuntu.com natty-security/main TranslationIndex            
Ign http://security.ubuntu.com natty-security/multiverse TranslationIndex      
Ign http://security.ubuntu.com natty-security/restricted TranslationIndex      
Ign http://security.ubuntu.com natty-security/universe TranslationIndex        
Ign http://www.kiberpipa.org ./ Sources/DiffIndex                              
Ign http://deb.opera.com etch/non-free Translation-en_US                       
Err http://www.kiberpipa.org ./ Sources                                        
  
Ign http://deb.opera.com etch/non-free Translation-en                          
Err http://www.kiberpipa.org ./ Sources                                        
  
Err http://apt.mepis.org mepis Release.gpg                                     
  Something wicked happened resolving 'apt.mepis.org:http' (-5 - No address associated with hostname)
Err http://www.kiberpipa.org ./ Sources                                        
  
Hit http://www.kiberpipa.org ./ Sources                                        
Ign http://blognux.free.fr unstable/main TranslationIndex                      
Ign http://security.ubuntu.com natty-security/main Translation-en_US           
Ign http://security.ubuntu.com natty-security/main Translation-en              
Ign http://security.ubuntu.com natty-security/multiverse Translation-en_US     
Ign http://security.ubuntu.com natty-security/multiverse Translation-en        
Ign http://security.ubuntu.com natty-security/restricted Translation-en_US     
Ign http://apt.mepis.org mepis Release                                         
Ign http://security.ubuntu.com natty-security/restricted Translation-en        
Ign http://security.ubuntu.com natty-security/universe Translation-en_US       
Ign http://security.ubuntu.com natty-security/universe Translation-en          
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://us.archive.ubuntu.com natty InRelease                               
Ign http://us.archive.ubuntu.com natty-updates InRelease                       
Get:11 http://extras.ubuntu.com natty Release.gpg [72 B]                       
Hit http://us.archive.ubuntu.com natty Release.gpg                             
Hit http://extras.ubuntu.com natty Release                                     
Get:12 http://us.archive.ubuntu.com natty-updates Release.gpg [198 B]          
Hit http://us.archive.ubuntu.com natty Release                                 
Hit http://extras.ubuntu.com natty/main Sources                                
Get:13 http://us.archive.ubuntu.com natty-updates Release [31.4 kB]            
Hit http://extras.ubuntu.com natty/main i386 Packages                          
Ign http://extras.ubuntu.com natty/main TranslationIndex                       
Ign http://apt.mepis.org mepis/main TranslationIndex                           
Hit http://us.archive.ubuntu.com natty/main Sources                            
Hit http://us.archive.ubuntu.com natty/restricted Sources                      
Hit http://us.archive.ubuntu.com natty/universe Sources                        
Hit http://us.archive.ubuntu.com natty/multiverse Sources                      
Hit http://us.archive.ubuntu.com natty/main i386 Packages                      
Hit http://us.archive.ubuntu.com natty/restricted i386 Packages                
Hit http://us.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://us.archive.ubuntu.com natty/multiverse i386 Packages                
Ign http://us.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://us.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://us.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://us.archive.ubuntu.com natty/universe TranslationIndex               
Get:14 http://us.archive.ubuntu.com natty-updates/main Sources [105 kB]        
Get:15 http://us.archive.ubuntu.com natty-updates/restricted Sources [14 B]    
Get:16 http://us.archive.ubuntu.com natty-updates/universe Sources [24.9 kB]   
Get:17 http://us.archive.ubuntu.com natty-updates/multiverse Sources [1,890 B] 
Get:18 http://us.archive.ubuntu.com natty-updates/main i386 Packages [315 kB]  
Ign http://extras.ubuntu.com natty/main Translation-en_US                      
Ign http://extras.ubuntu.com natty/main Translation-en                         
Get:19 http://us.archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:20 http://us.archive.ubuntu.com natty-updates/universe i386 Packages [90.9 kB]
Get:21 http://us.archive.ubuntu.com natty-updates/multiverse i386 Packages [4,258 B]
Ign http://us.archive.ubuntu.com natty-updates/main TranslationIndex           
Ign http://us.archive.ubuntu.com natty-updates/multiverse TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/restricted TranslationIndex     
Ign http://us.archive.ubuntu.com natty-updates/universe TranslationIndex       
Ign http://dl.google.com stable InRelease                                      
Get:22 http://dl.google.com stable Release.gpg [189 B]                         
Get:23 http://dl.google.com stable Release [2,544 B]                           
Err http://blognux.free.fr unstable/main i386 Packages                         
  404  Not Found
Ign http://us.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://us.archive.ubuntu.com natty/main Translation-en                     
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en_US            
Ign http://us.archive.ubuntu.com natty/multiverse Translation-en               
Ign http://us.archive.ubuntu.com natty/restricted Translation-en_US            
Ign http://us.archive.ubuntu.com natty/restricted Translation-en               
Ign http://us.archive.ubuntu.com natty/universe Translation-en_US              
Ign http://us.archive.ubuntu.com natty/universe Translation-en                 
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en_US          
Ign http://us.archive.ubuntu.com natty-updates/main Translation-en             
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/multiverse Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com natty-updates/restricted Translation-en       
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en_US      
Ign http://us.archive.ubuntu.com natty-updates/universe Translation-en         
Get:24 http://dl.google.com stable/non-free i386 Packages [1,010 B]            
Ign http://dl.google.com stable/non-free TranslationIndex                      
Ign http://blognux.free.fr unstable/main Translation-en_US                     
Ign http://download.skype.com stable InRelease                                 
Ign http://people.ubuntu.com ./ InRelease                                      
Ign http://vdlinux.sourceforge.jp experimental InRelease                       
Ign http://pkg-initng.alioth.debian.org experimental InRelease                 
Ign http://download.skype.com stable Release.gpg                               
Ign http://download.skype.com stable Release                                   
Ign http://blognux.free.fr unstable/main Translation-en                        
Ign http://download.skype.com stable/non-free i386 Packages/DiffIndex          
Ign http://download.skype.com stable/non-free TranslationIndex                 
Hit http://download.skype.com stable/non-free i386 Packages                    
Ign http://vdlinux.sourceforge.jp experimental Release.gpg                     
Ign http://dl.google.com stable/non-free Translation-en_US                     
Ign http://people.ubuntu.com ./ Release.gpg                                    
Ign http://dl.google.com stable/non-free Translation-en                        
Ign http://vdlinux.sourceforge.jp experimental Release                         
Ign http://download.skype.com stable/non-free Translation-en_US                
Ign http://people.ubuntu.com ./ Release                                        
Ign http://download.skype.com stable/non-free Translation-en                   
Ign http://vdlinux.sourceforge.jp experimental/all TranslationIndex            
Err http://vdlinux.sourceforge.jp experimental/all Sources                     
  404  Not Found
Err http://vdlinux.sourceforge.jp experimental/all i386 Packages               
  404  Not Found
Err http://people.ubuntu.com ./ Sources                                        
  404  Not Found
Err http://people.ubuntu.com ./ Packages                                       
  404  Not Found
Ign http://people.ubuntu.com ./ Translation-en_US                              
Ign http://vdlinux.sourceforge.jp experimental/all Translation-en_US           
Err http://apt.mepis.org mepis/main i386 Packages                              
  Something wicked happened resolving 'apt.mepis.org:http' (-5 - No address associated with hostname)
Ign http://vdlinux.sourceforge.jp experimental/all Translation-en              
Ign http://people.ubuntu.com ./ Translation-en                                 
Err http://apt.mepis.org mepis/main Translation-en_US                          
  Something wicked happened resolving 'apt.mepis.org:http' (-5 - No address associated with hostname)
Err http://apt.mepis.org mepis/main Translation-en                             
  Something wicked happened resolving 'apt.mepis.org:http' (-5 - No address associated with hostname)
Err http://pkg-initng.alioth.debian.org experimental Release.gpg               
  Could not connect to debian.space-based.de:80 (88.198.131.59), connection timed out
Fetched 899 kB in 2min 15s (6,621 B/s)                   
Reading package lists... Done

```

---

### Post by howefield on 2011-09-09
All the lines giving errors can be treated the same as the feisty ones, removed or commented out.

They are probably outdated PPAs no longer used, hence the error.

---

### Post by Rubi1200 on 2011-09-10
Glad you got things sorted out and are back up and running.

Enjoy :-)

---

