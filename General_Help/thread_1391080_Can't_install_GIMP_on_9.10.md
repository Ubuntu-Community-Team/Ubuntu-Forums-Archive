---
title: "Can't install GIMP on 9.10"
date: 2010-01-26
forum: General Help
---

### Post by metalllama on 2010-01-26
I went into terminal and tried to install GIMP with apt, and I et this error:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (<= 2.6.7-z) but 2.6.8-1~getdeb1 is to be installed
        Depends: gimp-data (<= 2.6.7-z) but 2.6.8-1~getdeb1 is to be installed
E: Broken packages

Can someone tell me what exactly is going wrong here?

---

### Post by audiomick on 2010-01-26
have you tried using synaptic package manager?

---

### Post by metalllama on 2010-01-26
Yeah, I did try that, and I get the same error.

---

### Post by t4thfavor on 2010-01-26
Weird error, try this, I know it fixes alot of package based problems.

sudo apt-get install --fix-missing

---

### Post by metalllama on 2010-01-26
> **t4thfavor said:**
> Weird error, try this, I know it fixes alot of package based problems.

sudo apt-get install --fix-missing
That seemingly did nothing, this is what it gave me:

The following packages were automatically installed and are no longer required:
  kdelibs-data nvidia-kernel-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.

I am still getting the same error when I try to install gimp.

---

### Post by philinux on 2010-01-26
Post back the output of this.

```
sudo apt-get update && sudo apt-get upgrade
```

Also gimp is installed by default, are you trying to install a different version from getdeb?

Apps>graphics>gimp

---

### Post by metalllama on 2010-01-26
> **philinux said:**
> Post back the output of this.

```
sudo apt-get update && sudo apt-get upgrade
```

Also gimp is installed by default, are you trying to install a different version from getdeb?

Apps>graphics>gimp

The funny thing is, I had gimp when I was using 9.04. I just upgraded to 9.10 like a week ago and I noticed it was not installed anymore.

Here is that output:
```

Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://us.archive.ubuntu.com karmic Release.gpg                  
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Hit http://security.ubuntu.com karmic-security Release.gpg           
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://archive.canonical.com karmic Release                      
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US   
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg          
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg         
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Get:2 http://dl.google.com stable Release [2,540B]                   
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com hardy-backports Release
Hit http://archive.canonical.com karmic/partner Packages             
Hit http://security.ubuntu.com karmic-security/main Packages                   
Get:3 http://dl.google.com stable/main Packages [905B]                         
Hit http://archive.canonical.com karmic/partner Sources             
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://security.ubuntu.com karmic-security/universe Packages
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
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Fetched 3,634B in 1s (2,008B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libcairo2 libcairo2-dev libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11
  pulseaudio-utils quassel quassel-data rhythmbox rhythmbox-dbg
  software-center
17 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,903kB of archives.
After this operation, 106kB disk space will be freed.
Do you want to continue [Y/n]? y

```

Then it fetched and unpacked everything

```
Preparing to replace software-center 1.0.2 (using .../software-center_1.0.3_all.deb) ...
Unpacking replacement software-center ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Setting up libcairo2 (1.8.8-2ubuntu1.1) ...

Setting up libcairo2-dev (1.8.8-2ubuntu1.1) ...
Setting up libpulse0 (1:0.9.19-0ubuntu4.1) ...

Setting up libpulse-browse0 (1:0.9.19-0ubuntu4.1) ...

Setting up pulseaudio-utils (1:0.9.19-0ubuntu4.1) ...
Setting up libpulse-mainloop-glib0 (1:0.9.19-0ubuntu4.1) ...

Setting up quassel-data (0.5.0-0ubuntu1.1) ...
Setting up quassel (0.5.0-0ubuntu1.1) ...
Setting up rhythmbox (0.12.5-0ubuntu5.2) ...

Setting up rhythmbox-dbg (0.12.5-0ubuntu5.2) ...
Setting up software-center (1.0.3) ...

Setting up pulseaudio-module-udev (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio (1:0.9.19-0ubuntu4.1) ...
 * PulseAudio configured for per-user sessions

Setting up pulseaudio-module-gconf (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio-module-bluetooth (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio-esound-compat (1:0.9.19-0ubuntu4.1) ...
Setting up pulseaudio-module-x11 (1:0.9.19-0ubuntu4.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place 

```

I will try to install gimp now

---

### Post by metalllama on 2010-01-26
I still get the same error when I try to install gimp.

---

### Post by philinux on 2010-01-26
> **metalllama said:**
> I still get the same error when I try to install gimp.

Are you using

```
sudo apt-get install gimp
```

Anyway try this.

```
sudo apt-get install -f
```

This will attempt to fix broken packages.

---

### Post by plucky on 2010-01-26
> Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages


I don't think this will cause your problem,but you need to remove the references to hardy-backports from your sources.list.

Open **System > Administration > Software Sources** and un-tick the box that refers to Hardy-backports on the **Other Software** or **Updates** pages.

---

### Post by happyhamster on 2010-01-26
> 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-backports/multiverse Packages

- There are some old hardy repos being used still. Go to System-->Administration-->Software Sources and see if you can disable them (under the Ubuntu Software or Third-Party Software tabs).
If they don't show there, do it manually by editing your sources.list:

gksudo gedit /etc/apt/sources.list

- Find the hardy lines, and turn them into comments by putting a # character before them. Save, and run:

sudo apt-get update
sudo apt-get upgrade


[edit: Plucky beat me to it :)]

---

### Post by metalllama on 2010-01-26
Yeah, that is the command I am using to get gimp, and I get the error from the first post.

Here is the output from the other command;
```
god@god-desktop:~$ sudo apt-get install -f
[sudo] password for god: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kdelibs-data nvidia-kernel-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I think it may have something to do with my software sources list, but I'm really not sure.

---

### Post by metalllama on 2010-01-26
> **happyhamster said:**
> - There are some old hardy repos being used still. Go to System-->Administration-->Software Sources and see if you can disable them (under the Ubuntu Software or Third-Party Software tabs).
If they don't show there, do it manually by editing your sources.list:

gksudo gedit /etc/apt/sources.list

- Find the hardy lines, and turn them into comments by putting a # character before them. Save, and run:

sudo apt-get update
sudo apt-get upgrade


[edit: Plucky beat me to it :)]

Okay, well I took the Hardy sources out, and ran update and upgrade, and here is what I got:

```
god@god-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://dl.google.com stable/main Translation-en_US                         
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://us.archive.ubuntu.com karmic Release                                
Hit http://archive.canonical.com karmic Release                      
Get:2 http://dl.google.com stable Release [2,540B]                   
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://archive.canonical.com karmic/partner Packages                       
Get:3 http://dl.google.com stable/main Packages [905B]                         
Hit http://security.ubuntu.com karmic-security/restricted Packages   
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/restricted Sources    
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://us.archive.ubuntu.com karmic/restricted Packages          
Hit http://us.archive.ubuntu.com karmic/main Sources                 
Hit http://us.archive.ubuntu.com karmic/restricted Sources           
Hit http://us.archive.ubuntu.com karmic/universe Packages            
Hit http://us.archive.ubuntu.com karmic/universe Sources             
Hit http://archive.canonical.com karmic/partner Sources                        
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
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
Fetched 3,634B in 1s (3,121B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Is there a source that I am missing that I should have? I have never taken any lines out of my sources.list or really messed with it though, so I don't know how they would just disappear.

---

### Post by philinux on 2010-01-26
This is what my standard Karmic sources list has in it.

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release Candidate amd64 (20091020.3)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-security multiverse
```

---

### Post by happyhamster on 2010-01-26
Does running "sudo apt-get install gimp" still give the same error message? Do you have manually installed packages on your system (from getdeb) perhaps? 

Take a look in synaptic: at the bottom left there is a Custom Filters tab, which will allow you to see any broken packages and such.

---

### Post by metalllama on 2010-01-26
> **happyhamster said:**
> Does running "sudo apt-get install gimp" still give the same error message? Do you have manually installed packages on your system (from getdeb) perhaps? 

Take a look in synaptic: at the bottom left there is a Custom Filters tab, which will allow you to see any broken packages and such.

I am still getting the same error message from "sudo apt-get install gimp." I do have some manually added repositories, here is my sources.list. 

Oh, and synaptic tells me there are no broken packages.
```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
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
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu karmic partner
deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security main restricted
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb-src http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse
deb-src http://security.ubuntu.com/ubuntu karmic-security multiverse
# deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu karmic main # disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu karmic main # disabled on upgrade to jaunty
# deb http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu jaunty main # disabled on upgrade to jaunty
# deb http://archive.getdeb.net/ubuntu karmic-getdeb apps # disabled on upgrade to karmic
```

---

### Post by philinux on 2010-01-26
```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Dont** hit the **Y** key at the end of this. But post back what it wants to do.

---

### Post by metalllama on 2010-01-26
> **philinux said:**
> ```
sudo apt-get update && sudo apt-get dist-upgrade
```

**Dont** hit the **Y** key at the end of this. But post back what it wants to do.

Here it is :```
god@god-desktop:~$ sudo apt-get update && sudo apt-get dist-upgrade
Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Hit http://archive.canonical.com karmic Release                                
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release                                
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://us.archive.ubuntu.com karmic-updates Release              
Hit http://security.ubuntu.com karmic-security/main Packages                   
Get:2 http://dl.google.com stable Release [2,540B]                             
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages                    
Hit http://us.archive.ubuntu.com karmic/main Sources                           
Hit http://us.archive.ubuntu.com karmic/restricted Sources                     
Hit http://us.archive.ubuntu.com karmic/universe Packages                      
Hit http://archive.canonical.com karmic/partner Sources                        
Hit http://security.ubuntu.com karmic-security/restricted Packages   
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/restricted Sources    
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://us.archive.ubuntu.com karmic/universe Sources             
Hit http://us.archive.ubuntu.com karmic/multiverse Packages          
Hit http://us.archive.ubuntu.com karmic/multiverse Sources           
Hit http://us.archive.ubuntu.com karmic-updates/main Packages        
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages  
Hit http://us.archive.ubuntu.com karmic-updates/main Sources         
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources   
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages    
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources     
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Get:3 http://dl.google.com stable/main Packages [905B]
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 3,634B in 1s (3,105B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by philinux on 2010-01-26
Ok thats fine then. Nothing out of the ordinary there.

What does this output.

```
apt-cache policy gimp
```

---

### Post by metalllama on 2010-01-26
I get this
```
gimp:
  Installed: (none)
  Candidate: 2.6.7-1ubuntu1.1
  Version table:
     2.6.7-1ubuntu1.1 0
        500 http://us.archive.ubuntu.com karmic-updates/main Packages
        500 http://security.ubuntu.com karmic-security/main Packages
     2.6.7-1ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages
     2.6.6-0ubuntu1.1 0
        100 /var/lib/dpkg/status

```

---

### Post by happyhamster on 2010-01-26
> 
The following packages have unmet dependencies:
gimp: Depends: libgimp2.0 (<= 2.6.7-z) but 2.6.8-1~getdeb1 is to be installed
Depends: gimp-data (<= 2.6.7-z) but 2.6.8-1~getdeb1 is to be installed
E: Broken packages

Do a search in synaptic for libgimp2.0 and gimp-data. If the version shown is .6.8-1~getdeb1, select the Package menu at the top, choose Force version. Is the correct version available there? You could force that version (and synaptic should warn you if other packages depend on it).

[edit: and try "sudo apt-get autoclean" to clean apt's cache]

---

### Post by metalllama on 2010-01-26
Wow, there was a lot of crap in the apt cache lol.

I went into synaptic and checked for different versions, and forced the version to 2.6.7 and that fixed it, and I got it installed. 

Thanks so much for your help folks :D

---

### Post by jamesisin on 2010-01-26
Excellent news.  Please mark your thread as SOLVED in Thread Tools above.

---

