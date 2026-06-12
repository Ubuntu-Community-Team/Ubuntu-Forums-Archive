---
title: "Unable to install wine"
date: 2012-04-26
forum: General Help
---

### Post by fackamato on 2012-04-26
Hi,

I upgraded to Xubuntu 12.04 from 11.10 and now I cannot install wine. I'm on AMD64. Here's the errors I get:

```
fackamato@fackamato-fat:~$ sudo apt-get install wine
[sudo] password for fackamato: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ sudo apt-get install wine1.5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5 : Depends: wine1.5-i386 (= 1.5.2-0ubuntu1~ppa1~precise1)
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ sudo apt-get install wine1.5-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5-i386:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Recommends: gettext:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ 

```

Here are my sources:

```
$ cat /etc/apt/sources.list | grep -v '#'
deb http://ie.archive.ubuntu.com/ubuntu/ precise main restricted
deb http://ie.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb http://ie.archive.ubuntu.com/ubuntu/ precise universe
deb http://ie.archive.ubuntu.com/ubuntu/ precise-updates universe
deb http://ie.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb http://ie.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb http://archive.canonical.com/ubuntu precise partner
deb http://extras.ubuntu.com/ubuntu precise main
deb http://ie.archive.ubuntu.com/ubuntu/ precise-proposed restricted main multiverse universe

fackamato@fackamato-fat:/etc/apt/sources.list.d$ ls -l | grep -v save
total 36
-rw-r--r-- 1 root root  58 Apr 26 21:16 dropbox.list
-rw-r--r-- 1 root root  49 Apr 26 17:41 dropbox.list.distUpgrade
-rw-r--r-- 1 root root 121 Apr 26 21:16 google-chrome.list
-rw-r--r-- 1 root root 176 Apr 26 17:41 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 154 Apr 26 21:16 scottritchie-build-tests-precise.list
-rw-r--r-- 1 root root   0 Apr 26 21:14 ubuntu-wine-ppa-precise.list

```

Anyone have a clue? I tried sudo apt-get update && sudo apt-get upgrade (or dist-upgrade) but there are no updates.

---

### Post by Toz on 2012-04-26
What does this return?
```
apt-cache policy wine
```

Your ubuntu-wine-ppa-precise.list file is 0 size. Try deleting the file and re-running
```
apt-get update
```

---

### Post by fackamato on 2012-04-27
> **Toz said:**
> What does this return?
```
apt-cache policy wine
```

Your ubuntu-wine-ppa-precise.list file is 0 size. Try deleting the file and re-running
```
apt-get update
```

True. I removed all 3rd party PPA's and re-ran apt-get update:

```
fackamato@fackamato-fat:~$ clear;sudo apt-get update

Ign http://extras.ubuntu.com precise InRelease
Ign http://archive.canonical.com precise InRelease                                                                   
Ign http://ppa.launchpad.net precise InRelease                                                                       
Ign http://archive.ubuntu.com precise InRelease                                                                       
Ign http://archive.ubuntu.com precise-updates InRelease                                                               
Ign http://archive.ubuntu.com precise-backports InRelease                                                             
Ign http://archive.ubuntu.com precise-security InRelease                                                              
Ign http://archive.ubuntu.com precise-proposed InRelease                                                                                    
Hit http://archive.canonical.com precise Release.gpg                                                                                        
Hit http://extras.ubuntu.com precise Release.gpg                                                                                            
Hit http://ppa.launchpad.net precise Release.gpg                                           
Hit http://archive.ubuntu.com precise Release.gpg                                          
Hit http://archive.ubuntu.com precise-updates Release.gpg                                  
Hit http://archive.canonical.com precise Release                                           
Hit http://extras.ubuntu.com precise Release                                                                      
Hit http://ppa.launchpad.net precise Release                                                                      
Hit http://archive.ubuntu.com precise-backports Release.gpg                                                       
Hit http://archive.ubuntu.com precise-security Release.gpg                                 
Hit http://archive.canonical.com precise/partner amd64 Packages                                                  
Ign http://linux.dropbox.com precise InRelease                                                                   
Hit http://extras.ubuntu.com precise/main amd64 Packages                                   
Hit http://archive.ubuntu.com precise-proposed Release.gpg                                 
Hit http://archive.ubuntu.com precise Release                                                                    
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                                
Hit http://archive.canonical.com precise/partner i386 Packages                                                                          
Ign http://archive.canonical.com precise/partner TranslationIndex                                                
Hit http://archive.ubuntu.com precise-updates Release                                                            
Hit http://archive.ubuntu.com precise-backports Release                                    
Hit http://extras.ubuntu.com precise/main i386 Packages                                                                                 
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                              
Hit http://ppa.launchpad.net precise/main i386 Packages                                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                       
Hit http://archive.ubuntu.com precise-security Release                                                           
Hit http://archive.ubuntu.com precise-proposed Release                                                                                  
Hit http://archive.ubuntu.com precise/main amd64 Packages                                                                               
Hit http://archive.ubuntu.com precise/restricted amd64 Packages                                                  
Hit http://archive.ubuntu.com precise/universe amd64 Packages                                                    
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages                                                  
Hit http://archive.ubuntu.com precise/main i386 Packages                                                         
Hit http://linux.dropbox.com precise Release.gpg                                                                 
Hit http://archive.ubuntu.com precise/restricted i386 Packages                                                   
Hit http://archive.ubuntu.com precise/universe i386 Packages                               
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                             
Hit http://archive.ubuntu.com precise/main TranslationIndex                                                      
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex                                                
Hit http://archive.ubuntu.com precise/restricted TranslationIndex                                                
Hit http://archive.ubuntu.com precise/universe TranslationIndex                                                  
Hit http://archive.ubuntu.com precise-updates/main amd64 Packages                                                
Hit http://archive.ubuntu.com precise-updates/restricted amd64 Packages                    
Hit http://archive.ubuntu.com precise-updates/universe amd64 Packages                                            
Hit http://archive.ubuntu.com precise-updates/multiverse amd64 Packages                                          
Hit http://archive.ubuntu.com precise-updates/main i386 Packages                                                 
Hit http://archive.ubuntu.com precise-updates/restricted i386 Packages                                           
Hit http://archive.ubuntu.com precise-updates/universe i386 Packages                                             
Hit http://archive.ubuntu.com precise-updates/multiverse i386 Packages                                           
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex                                              
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex                                        
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex                                        
Hit http://linux.dropbox.com precise Release                                                                     
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex                                           
Hit http://archive.ubuntu.com precise-backports/main amd64 Packages                        
Hit http://archive.ubuntu.com precise-backports/restricted amd64 Packages                                        
Hit http://archive.ubuntu.com precise-backports/universe amd64 Packages                                          
Hit http://archive.ubuntu.com precise-backports/multiverse amd64 Packages                                        
Hit http://archive.ubuntu.com precise-backports/main i386 Packages                                               
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages                                         
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages                                           
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages                                         
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex                                            
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex                                      
Hit http://linux.dropbox.com precise/main amd64 Packages                                                         
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex                                      
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex                  
Hit http://archive.ubuntu.com precise-security/main amd64 Packages                         
Hit http://archive.ubuntu.com precise-security/restricted amd64 Packages                   
Hit http://archive.ubuntu.com precise-security/universe amd64 Packages                     
Hit http://archive.ubuntu.com precise-security/multiverse amd64 Packages                   
Hit http://archive.ubuntu.com precise-security/main i386 Packages                                                
Hit http://archive.ubuntu.com precise-security/restricted i386 Packages                                          
Hit http://archive.ubuntu.com precise-security/universe i386 Packages                                            
Hit http://archive.ubuntu.com precise-security/multiverse i386 Packages                                          
Hit http://archive.ubuntu.com precise-security/main TranslationIndex                                             
Hit http://archive.ubuntu.com precise-security/multiverse TranslationIndex                 
Hit http://archive.ubuntu.com precise-security/restricted TranslationIndex                 
Ign http://archive.canonical.com precise/partner Translation-en_US                         
Hit http://archive.ubuntu.com precise-security/universe TranslationIndex                   
Hit http://archive.ubuntu.com precise-proposed/restricted amd64 Packages                                         
Hit http://archive.ubuntu.com precise-proposed/main amd64 Packages                                               
Hit http://archive.ubuntu.com precise-proposed/multiverse amd64 Packages                                         
Hit http://archive.ubuntu.com precise-proposed/universe amd64 Packages                                           
Hit http://archive.ubuntu.com precise-proposed/restricted i386 Packages                                          
Hit http://archive.ubuntu.com precise-proposed/main i386 Packages                          
Hit http://linux.dropbox.com precise/main i386 Packages                                                          
Ign http://linux.dropbox.com precise/main TranslationIndex                                                       
Ign http://archive.canonical.com precise/partner Translation-en                                                  
Ign http://extras.ubuntu.com precise/main Translation-en_US                                
Ign http://ppa.launchpad.net precise/main Translation-en_US          
Hit http://archive.ubuntu.com precise-proposed/multiverse i386 Packages
Hit http://archive.ubuntu.com precise-proposed/universe i386 Packages
Hit http://archive.ubuntu.com precise-proposed/main TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/restricted TranslationIndex
Hit http://archive.ubuntu.com precise-proposed/universe TranslationIndex
Hit http://archive.ubuntu.com precise/main Translation-en            
Ign http://extras.ubuntu.com precise/main Translation-en             
Ign http://ppa.launchpad.net precise/main Translation-en             
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Hit http://archive.ubuntu.com precise-security/main Translation-en
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise-security/universe Translation-en
Hit http://archive.ubuntu.com precise-proposed/main Translation-en
Hit http://archive.ubuntu.com precise-proposed/multiverse Translation-en
Hit http://archive.ubuntu.com precise-proposed/restricted Translation-en
Hit http://archive.ubuntu.com precise-proposed/universe Translation-en
Ign http://linux.dropbox.com precise/main Translation-en_US
Ign http://linux.dropbox.com precise/main Translation-en
Reading package lists... Done
fackamato@fackamato-fat:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.4-0ubuntu4
  Version table:
     1.4-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
fackamato@fackamato-fat:~$ 

```

I have "unsupported" & backports enabled - would this matter?

---

### Post by Toz on 2012-04-27
Try:
```
sudo apt-get purge wine
```
...then
```
sudo apt-get install -f
```

If everything is okay, then try installing wine again:
```
sudo apt-get install wine
```

---

### Post by fackamato on 2012-04-27
> **Toz said:**
> Try:
```
sudo apt-get purge wine
```
...then
```
sudo apt-get install -f
```

If everything is okay, then try installing wine again:
```
sudo apt-get install wine
```

```
fackamato@fackamato-fat:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fackamato@fackamato-fat:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fackamato@fackamato-fat:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ 

fackamato@fackamato-fat:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse
  Version table:
     1.5.2-0ubuntu1~ppa1~precise1+pulse 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages
     1.5.2-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/ precise/main amd64 Packages
     1.4-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
fackamato@fackamato-fat:~$ apt-cache policy wine1.5
wine1.5:
  Installed: (none)
  Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse
  Version table:
     1.5.2-0ubuntu1~ppa1~precise1+pulse 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages
     1.5.2-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/ precise/main amd64 Packages
fackamato@fackamato-fat:~$ 
fackamato@fackamato-fat:~$ sudo apt-get install wine1.5-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5-i386:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Recommends: gettext:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ sudo apt-cache policy wine1.5-i386
wine1.5-i386:i386:
  Installed: (none)
  Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse
  Version table:
     1.5.2-0ubuntu1~ppa1~precise1+pulse 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main i386 Packages
     1.5.2-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/ precise/main i386 Packages


```

Since I want wine to run 32-bit applications on a 64-bit system - perhaps there's some multilib/multiarch repo/option I have to enable?

---

### Post by techsupport on 2012-04-27
> **fackamato said:**
> ```
fackamato@fackamato-fat:~$ sudo apt-get purge wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fackamato@fackamato-fat:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fackamato@fackamato-fat:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ 

fackamato@fackamato-fat:~$ apt-cache policy wine
wine:
  Installed: (none)
  Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse
  Version table:
     1.5.2-0ubuntu1~ppa1~precise1+pulse 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages
     1.5.2-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/ precise/main amd64 Packages
     1.4-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ precise/universe amd64 Packages
fackamato@fackamato-fat:~$ apt-cache policy wine1.5
wine1.5:
  Installed: (none)
  Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse
  Version table:
     1.5.2-0ubuntu1~ppa1~precise1+pulse 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main amd64 Packages
     1.5.2-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/ precise/main amd64 Packages
fackamato@fackamato-fat:~$ 
fackamato@fackamato-fat:~$ sudo apt-get install wine1.5-i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.5-i386:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or
                              libgl1:i386
                     Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Recommends: gettext:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ sudo apt-cache policy wine1.5-i386
wine1.5-i386:i386:
  Installed: (none)
  Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse
  Version table:
     1.5.2-0ubuntu1~ppa1~precise1+pulse 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main i386 Packages
     1.5.2-0ubuntu1~ppa1~precise1 0
        500 http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/ precise/main i386 Packages


```Since I want wine to run 32-bit applications on a 64-bit system - perhaps there's some multilib/multiarch repo/option I have to enable?

I just installed Wine from the PPA like this, and installed fine: (down the list)

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

---

### Post by fackamato on 2012-04-27
> **techsupport said:**
> I just installed Wine from the PPA like this, and installed fine: (down the list)

[http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

I tried everything but it doesn't work.

Could you please post your /etc/apt/sources.list and which files do you have in /etc/apt/sources.list.d/ ?

---

### Post by Sworddragon on 2012-04-27
> **fackamato said:**
> Since I want wine to run 32-bit applications on a 64-bit system - perhaps there's some multilib/multiarch repo/option I have to enable?

Yes, on 64 bit systems you have to enable multiarch to get the needed packages. Check if /etc/dpkg/dpkg.cfg.d/multiarch with the content "foreign-architecture i386" exists. If not create it and try again (you have to run "apt-get update" again).

---

### Post by fackamato on 2012-04-27
> **Sworddragon said:**
> Yes, on 64 bit systems you have to enable multiarch to get the needed packages. Check if /etc/dpkg/dpkg.cfg.d/multiarch with the content "foreign-architecture i386" exists. If not create it and try again (you have to run "apt-get update" again).

```
fackamato@fackamato-fat:~$ cat /etc/dpkg/dpkg.cfg.d/multiarch
foreign-architecture i386

```

So that looks OK I guess.

edit: This doesn't seem to be wine specific:

```
fackamato@fackamato-fat:~$ sudo apt-get install acroread
[sudo] password for fackamato: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 acroread : Depends: ia32-libs (>= 20080808) but it is not going to be installed
            Depends: nspluginwrapper but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
fackamato@fackamato-fat:~$ 

```

---

### Post by techsupport on 2012-04-27
What is this in the source.list 

-rw-r--r-- 1 root root 154 Apr 26 21:16 scottritchie-build-tests-precise.list

Can PPA purge that and roll your Ubuntu back?

---

### Post by fackamato on 2012-04-27
> **techsupport said:**
> What is this in the source.list 

-rw-r--r-- 1 root root 154 Apr 26 21:16 scottritchie-build-tests-precise.list

Can PPA purge that and roll your Ubuntu back?

D'oh. I forgot about PPA purging. I'm trying that now, thanks.

edit: So I purged that PPA, and the Ubuntu Wine PPA. Still the same. Fekk, I think I just might reinstall from scratch. This is looking like RPM dependency hell. I suppose having PPA's enabled and upgrading from 11.10 to 12.04 isn't that.. good.

---

### Post by mikodo on 2012-04-27
When you purged Wine, you left packages without thier needed dependencies on your system. It seems, you need to correct this situation, of broken package dependencies.

Consider, removing the unmet dependency packages first, with your favorite package manager, before installing another version of Wine. Then, with the new install, the packages with thier dependencies, should be installed.

See here, from your earlier posting:
```
fackamato@fackamato-fat:~$ sudo apt-get purge wine Reading package lists... Done Building dependency tree        Reading state information... Done Package wine is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. fackamato@fackamato-fat:~$ sudo apt-get install -f Reading package lists... Done Building dependency tree        Reading state information... Done 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. fackamato@fackamato-fat:~$ sudo apt-get install wine Reading package lists... Done Building dependency tree        Reading state information... Done Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  wine : Depends: wine1.5 but it is not going to be installed E: Unable to correct problems, you have held broken packages. fackamato@fackamato-fat:~$   fackamato@fackamato-fat:~$ apt-cache policy wine wine:   Installed: (none)   Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse   Version table:      1.5.2-0ubuntu1~ppa1~precise1+pulse 0         500 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main amd64 Packages      1.5.2-0ubuntu1~ppa1~precise1 0         500 [http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/](http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/) precise/main amd64 Packages      1.4-0ubuntu4 0         500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages fackamato@fackamato-fat:~$ apt-cache policy wine1.5 wine1.5:   Installed: (none)   Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse   Version table:      1.5.2-0ubuntu1~ppa1~precise1+pulse 0         500 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main amd64 Packages      1.5.2-0ubuntu1~ppa1~precise1 0         500 [http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/](http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/) precise/main amd64 Packages fackamato@fackamato-fat:~$  fackamato@fackamato-fat:~$ sudo apt-get install wine1.5-i386 Reading package lists... Done Building dependency tree        Reading state information... Done Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  wine1.5-i386:i386 : Depends: libgl1-mesa-glx:i386 but it is not going to be installed or                               libgl1:i386                      Depends: libglu1-mesa:i386 but it is not going to be installed or                               libglu1:i386                      Recommends: gettext:i386 but it is not going to be installed E: Unable to correct problems, you have held broken packages. fackamato@fackamato-fat:~$ sudo apt-cache policy wine1.5-i386 wine1.5-i386:i386:   Installed: (none)   Candidate: 1.5.2-0ubuntu1~ppa1~precise1+pulse   Version table:      1.5.2-0ubuntu1~ppa1~precise1+pulse 0         500 [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) precise/main i386 Packages      1.5.2-0ubuntu1~ppa1~precise1 0         500 [http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/](http://ppa.launchpad.net/scottritchie/build-tests/ubuntu/) precise/main i386 Packages
```

---

### Post by timtoo on 2012-05-09
Having the same problem on amd64 (kubuntu), I uninstalled lots of stuff that had seemed to have dependency problems, such as googleearth and picasa. Then the problem became:

```
The following packages have unmet dependencies:
 wine1.5-i386:i386 : Depends: libgphoto2-2:i386 (>= 2.4.10.1) but it is not going to be installed
                     Depends: libgphoto2-port0:i386 (>= 2.4.10.1) but it is not going to be installed
```

So I did an "apt-get install libgphoto2-port0:i386" to force that to install, and apt then went and removed a bunch of stuff that was depending on "libgphoto2-port0" (primarily digikam, but also a few other things).

After doing that I reinstalled all the stuff that had been uninstalled. And everything seems to be working again. Including wine. 

Anyone else reading this may not have the exact same problem, but it's likely a :386 package dependency hidden somewhere refusing to upgrade/install you need to track down.

---

### Post by baijea on 2012-09-18
Hi,

the solution to a similar problem I had is listed in [http://ubuntuforums.org/showpost.php?p=12246372&postcount=7](http://ubuntuforums.org/showpost.php?p=12246372&postcount=7).

Hope this helps!

---

