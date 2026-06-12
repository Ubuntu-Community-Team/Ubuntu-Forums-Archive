---
title: "OpenBVE dependencies cannot be resolved."
date: 2011-02-13
forum: General Help
---

### Post by Bernie Gallagher on 2011-02-13
Yeah, I've been downloading some new games from the Ubuntu Software Center today.  

I tried to install OpenBVE (a railroad simulator) and got the error: "Package dependencies cannot be resolved".

The OpenBVE site mentions dependencies, but is a little unclear on exactly what I need and exactly where to download them.  

Can anyone share a few clues?

---

### Post by sikander3786 on 2011-02-13
From Terminal, please post the output of these command.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update && sudo apt-get install openbve
```

---

### Post by Bernie Gallagher on 2011-02-13
Here's all three commands issued in a row:

```
bernie@Klavierstein:~$ sudo apt-get install -f
[sudo] password for bernie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bernie@Klavierstein:~$ sudo dpkg --configure -a
bernie@Klavierstein:~$ sudo apt-get update && sudo apt-get install openbve
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Hit http://packages.medibuntu.org karmic Release.gpg                           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://archive.canonical.com karmic Release                                
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://us.archive.ubuntu.com karmic Release                                
Ign http://packages.medibuntu.org karmic/free Translation-en_US                
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US            
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://packages.medibuntu.org karmic Release                               
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources         
Hit http://security.ubuntu.com karmic-security/restricted Sources   
Hit http://security.ubuntu.com karmic-security/universe Packages    
Hit http://us.archive.ubuntu.com karmic/main Packages               
Hit http://security.ubuntu.com karmic-security/universe Sources     
Hit http://security.ubuntu.com karmic-security/multiverse Packages 
Hit http://security.ubuntu.com karmic-security/multiverse Sources  
Hit http://us.archive.ubuntu.com karmic/restricted Packages        
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://us.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages            
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://packages.medibuntu.org karmic/non-free Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openbve: Depends: libtaoframework-openal1.1-cil (< 2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed
           Depends: libtaoframework-opengl2.1-cil (>= 2.0.0.svn20071027) but it is not installable
           Depends: libtaoframework-opengl2.1-cil (< 2.0.0.svn20071028) but it is not installable
           Depends: libtaoframework-sdl1.2-cil (< 2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed
E: Broken packages
bernie@Klavierstein:~$ 
```

---

### Post by sikander3786 on 2011-02-13
Try using aptitude. It would propose a solution at least.

```
sudo aptitude install openbve
```

---

### Post by Bernie Gallagher on 2011-02-13
This looks promising.  Should I answer Y?

```
bernie@Klavierstein:~$ sudo aptitude install openbve
[sudo] password for bernie: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  openbve 
The following NEW packages will be installed:
  bve-route-cross-city-south{a} bve-train-br-class-323{a} libgluezilla{a} 
  libmono-accessibility2.0-cil{a} libmono-i18n2.0-cil{a} 
  libmono-system-runtime2.0-cil{a} libmono-webbrowser0.5-cil{a} 
  libmono-winforms2.0-cil{a} libnunit2.4-cil{a} libopenal1{a} 
  libsdl-ttf2.0-0{a} libtaoframework-openal1.1-cil{a} 
  libtaoframework-sdl1.2-cil{a} openbve-data{a} 
The following packages will be REMOVED:
  linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 15 newly installed, 2 to remove and 0 not upgraded.
Need to get 16.9MB of archives. After unpacking 8,528kB will be used.
The following packages have unmet dependencies:
  openbve: Depends: libtaoframework-openal1.1-cil (< 2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed.
           Depends: libtaoframework-opengl2.1-cil (>= 2.0.0.svn20071027) which is a virtual package.
           Depends: libtaoframework-opengl2.1-cil (< 2.0.0.svn20071028) which is a virtual package.
           Depends: libtaoframework-sdl1.2-cil (< 2.0.0.svn20071028) but 2.1.svn20090801-1build1 is to be installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
openbve [Not Installed]

Leave the following dependencies unresolved:
bve-route-cross-city-south recommends bve-engine
bve-train-br-class-323 recommends bve-engine
Score is -10281

Accept this solution? [Y/n/q/?] 
```

---

### Post by sikander3786 on 2011-02-13
Yes you can safely accept as no packages are being _removed_. After completion, if there are still some unment dependencies, run these commands.

```
sudo aptitude install -f
```

```
sudo dpkg --configure -a
```

Good Luck!

---

### Post by Bernie Gallagher on 2011-02-13
Now this looks scary, but it looks like it installed something...

```
Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 82.0MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 151519 files and directories currently installed.)
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

bernie@Klavierstein:~$  
```

---

### Post by sikander3786 on 2011-02-13
Yes, really seems scary. Say no.

And please post the ouput of these commands in order to find some other workaround.

```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
```

---

### Post by Bernie Gallagher on 2011-02-13
```
bernie@Klavierstein:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic universe
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
bernie@Klavierstein:~$ ls -l /etc/apt/sources.list.d
total 4
-rw-r--r-- 1 root root 273 2010-11-26 20:54 medibuntu.list
bernie@Klavierstein:~$ 
```

---

### Post by sikander3786 on 2011-02-13
> **Bernie Gallagher said:**
> Now this looks scary, but it looks like it installed something...

```
Accept this solution? [Y/n/q/?] Y
The following packages will be REMOVED:
  linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 82.0MB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 151519 files and directories currently installed.)
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

bernie@Klavierstein:~$  
```
It didn't install anything, it just removed the linux headers packages. Install those or your might not be able to boot successfully.

```
sudo apt-get install linux-headers-2.6.31-14{u} linux-headers-2.6.31-14-generic{u}
```

Before installing those packages, you can once more try to install openbve and see what happens this time.

```
sudo aptitude install openbve
```

---

### Post by Bernie Gallagher on 2011-02-13
Actually, it's not really scary.  I already clobbered my filesystem a couple of times by being a clueless noob with sudo and had to reinstall Ubuntu from scratch from the iso (I work off an external USB drive, so I won't lose anything important if I kill my system, I learned the safety of doing that from using Windoze) :-p  So I'm not too scared any more of trying weird things.  I'll let you know in a few minutes what happened...

---

### Post by Bernie Gallagher on 2011-02-13
Okay.  Good news and bad news.  

Good news:  My system rebooted and everything is fine.

Bad news: OpenBVE is still MIA (doesn't show up among my list of applications).

---

