---
title: "First time post and problems."
date: 2012-03-14
forum: General Help
---

### Post by lukeone on 2012-03-14
Hi.  This is my first post.  I have problems.  I'm running Xubuntu 11.10.  Synaptic and update manager don't work.  I have the little red dot with the white line through it indicator too.

I'm asking this question very generally because I have tried many of the solutions on this forum and it got worse, so I think I need to go through this more step by step.  

Also I have 5 or six broken packages and can't delete all of them.

Any help will be appreciated.

---

### Post by plucky on 2012-03-14
> **lukeone said:**
> Hi.  This is my first post.  I have problems.  I'm running Xubuntu 11.10.  Synaptic and update manager don't work.  I have the little red dot with the white line through it indicator too.

I'm asking this question very generally because I have tried many of the solutions on this forum and it got worse, so I think I need to go through this more step by step.  

Also I have 5 or six broken packages and can't delete all of them.

Any help will be appreciated.

Welcome to the Forum.

Open a terminal and post output for ```
sudo apt-get update
```

---

### Post by lukeone on 2012-03-14
Ign [http://dl.google.com](http://dl.google.com) stable InRelease
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]                          
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,351 B]                            
Get:3 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,256 B]                 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Get:4 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Fetched 2,877 B in 1s (2,013 B/s)
Reading package lists... Done

This is different from what I've been getting. Before I was getting errors

---

### Post by 2F4U on 2012-03-14
The next step would be to run

sudo apt-get upgrade

That would try to install the available updates.

---

### Post by AnojiRox on 2012-03-14
try this:
sudo apt-get -f install
it SHOULD fix the broken packages.

---

### Post by lukeone on 2012-03-14
> **2F4U said:**
> The next step would be to run

sudo apt-get upgrade

That would try to install the available updates.
sudo apt-get upgrade gives me this:

The following packages have unmet dependencies:
 libglib2.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-configuration4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-drawing4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-xml4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by lukeone on 2012-03-14
> **AnojiRox said:**
> try this:
sudo apt-get -f install
it SHOULD fix the broken packages.

sudo apt-get -f install gives me this:

The following packages have unmet dependencies:
 libglib2.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-configuration4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-drawing4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
 libmono-system-xml4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by jerome1232 on 2012-03-14
should've been

```
sudo apt-get install -f
```

edit: In the future, it's best for readability to wrap terminal output in code tags, switch to advanced mode, highlight all output, and click the # button.

---

### Post by lukeone on 2012-03-14
```

sudo apt-get install -f
``` Gets me this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-14 libmono-cairo4.0-cil linux-headers-3.0.0-14-generic
  libmono-system-drawing4.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmono-system4.0-cil
The following packages will be REMOVED:
  libgtk2.0-cil
The following NEW packages will be installed:
  libmono-system4.0-cil
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 664 kB of archives.
After this operation, 799 kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric/main libmono-system4.0-cil all 2.10.5-1 [664 kB]
Fetched 664 kB in 1s (587 kB/s)                
(Reading database ... 240072 files and directories currently installed.)
Removing libgtk2.0-cil ...
E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libgtk2.0-cil
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by lukeone on 2012-03-15
So what are these errors?

---

### Post by plucky on 2012-03-16
> E: File does not exist: /usr/share/cli-common/packages.d/policy.2.6.gtk-dotnet.installcligac
dpkg: error processing libgtk2.0-cil (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 libgtk2.0-cil

Try from a terminal ```
sudo apt-get remove libgtk2.0-cil
```

and if that fails:-

Try re-installing that package as it seems to be missing a file (policy.2.6.gtk-dotnet.installcligac) and the removal process is failing.

Try ```
sudo apt-get install --reinstall libgtk2.0-cil
```

If that doesn't work,run ```
sudo apt-get clean
``` and then run the install command again,so it has to download a new version of the package.

Good Luck

---

### Post by lukeone on 2012-03-16
It's a mess here's what I get.


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglib2.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-configuration4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-drawing4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-xml4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
lou_cone@user-Dell-DXC061:~$ sudo apt-get install --reinstall libgtk2.0-cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglib2.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-configuration4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-drawing4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-xml4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
xxx@user-Dell-DXC061:~$ sudo apt-get clean
xxx@user-Dell-DXC061:~$ apt-get clean
E: Could not open lock file /var/cache/apt/archives/lock - open (13: Permission denied)
E: Unable to lock the download directory
xxx@user-Dell-DXC061:~$ sudo apt-get install --reinstall  libgtk2.--cil
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtk2.--cil
E: Couldn't find any package by regex 'libgtk2.--cil'

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglib2.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-configuration4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-drawing4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-security4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
 libmono-system-xml4.0-cil : Depends: libmono-system4.0-cil (>= 2.10.1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
xxx@user-Dell-DXC061:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

---

### Post by plucky on 2012-03-16
> sudo apt-get install --reinstall  [color=red]libgtk2.--cil[/color]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtk2.--cil
E: Couldn't find any package by regex 'libgtk2.--cil'

The package has to be the correct syntax,which is why it was unable to locate the package.

And use sudo with every command or you will get the permission denied error.

Good Luck

---

### Post by jerome1232 on 2012-03-16
> **lukeone said:**
> It's a mess here's what I get.



The great thing about code tags, is you can copy past them into your terminal. A great way of avoiding typos

---

### Post by cottfcfan on 2012-03-16
Just a suggestion. Try changing your server in Software sources, and make sure your independant & Canonical partners repos are enabled.
Then:
```
sudo apt-get update
```
and try again.

---

### Post by QIII on 2012-03-16
```
sudo apt-get dist-upgrade
```

will do everything upgrade does, with the addition (among other things) of attempting to resolve dependencies.

It will NOT try to upgrade you to the next version of Ubuntu.  That is a different command.

That may possibly get you to a state where this will work.

---

### Post by lukeone on 2012-04-02
This seems to have worked.  Thanks!

---

