---
title: "upgrading from 10.04 to 10.10"
date: 2010-12-08
forum: General Help
---

### Post by gulabpasha on 2010-12-08
Hi,

I'm currently using Ubuntu 10.04 with LAMP and i have hosted my few websites in it.

What if I use do-release-upgrade, Do i have to configure each and every settings again or do-release-upgrade will automatically migrate all my settings.

Please help.

Thanks,
Gulab Pasha

---

### Post by zvacet on 2010-12-08
It should keep your setting,but I don´t see reason for upgrade if you use that ubuntu for web hosting.I zhink that LTS is better choise for you.Let somebody correct me if I´m wrong.

---

### Post by andymorton on 2010-12-08
If 10.04 LTS is working well for you then there's really no reason to upgrade. 10.10 doesn't seem to be as stable as the LTS

andy

---

### Post by gulabpasha on 2010-12-08
Hi,

Thanks for your quick reply, There is small issue with my current OS Ubuntu 10.04. It is very slow to access (any service like ssh, or web). It take ages to load my web pages.


And I receive lot of  packages missing error while i try to install any package.

(ptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be upgraded:
  imagemagick libmagickcore2 libmagickcore2-extra libmagickwand2 libssl-dev libssl0.9.8 openssl 
The following partially installed packages will be configured:
  grub-pc 
7 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 7,658kB of archives. After unpacking 4,096B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libssl-dev 0.9.8k-7ubuntu8.5 [2,006kB]
Get:2 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libssl0.9.8 0.9.8k-7ubuntu8.5 [3,015kB]                                                                                                 
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libssl0.9.8 0.9.8k-7ubuntu8.5
  Connection failed
Get:3 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libssl0.9.8 0.9.8k-7ubuntu8.5 [3,015kB]
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libmagickcore2 7:6.5.7.8-1ubuntu1.1                                                                                                       
  Connection failed
Get:4 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libmagickwand2 7:6.5.7.8-1ubuntu1.1 [355kB]
Get:5 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libmagickcore2 7:6.5.7.8-1ubuntu1.1 [1,666kB]                                                                                            
Get:6 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main imagemagick 7:6.5.7.8-1ubuntu1.1 [101kB]                                                                                                
Get:7 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main libmagickcore2-extra 7:6.5.7.8-1ubuntu1.1 [113kB]                                                                                       
Get:8 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main openssl 0.9.8k-7ubuntu8.5 [400kB]                                                                                                       
Fetched 5,595kB in 12min 8s (7,683B/s)
Preconfiguring packages ...
(Reading database ... 
dpkg: warning: files list file for package `libio-string-perl' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `rkhunter' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `wwwconfig-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ruby1.8-dev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libxau6' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblaunchpad-integration1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `liblockfile1' missing, assuming package has no files currently installed.


Etc

And I get the below error as well

dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
Reading package lists... Done
)

I don't I can't boot my ubuntu10.04 from GUI mode, It stuck on the welcome page but i access it through ssh.

I have enough good configuration machine, I just want my system to work fast and stay upgraded.

Hope do-release upgrade will fix all the issues.


Thanks,
Gulab Pasha

---

### Post by zvacet on 2010-12-08
You can try to change your entries in source list.Replace all lines so one you have look like

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
```

and they should look like

```
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
```


after that

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by gulabpasha on 2010-12-09
Hi,

I followed all the possible things to fix and make my OS run faster but still I get the same error while i try to use apt-get upgrade.

Because of that I'm planning to migrate (upgrade) my curresnt ubuntu 10.04 to ubuntu 10.10.

Please find the out put of my sources.list and upgrade error.


root@sfdlabs:~# cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://software.open-xchange.com/OX6/unsupported/6.18/Ubuntu10.04/](http://software.open-xchange.com/OX6/unsupported/6.18/Ubuntu10.04/) /
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
## main & restricted repositories
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted

## universe repositories
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe

deb [http://repo.varnish-cache.org/debian/](http://repo.varnish-cache.org/debian/) lucid varnish-2.1




root@sfdlabs:~# apt-get update && apt-get upgrade
Hit [http://software.open-xchange.com](http://software.open-xchange.com)  Release.gpg                                                                                      
Hit [http://repo.varnish-cache.org](http://repo.varnish-cache.org) lucid Release.gpg                                                                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                                        
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                                               
Ign [http://software.open-xchange.com/OX6/unsupported/6.18/Ubuntu10.04/](http://software.open-xchange.com/OX6/unsupported/6.18/Ubuntu10.04/)  Translation-en_IN                        
Ign [http://repo.varnish-cache.org/debian/](http://repo.varnish-cache.org/debian/) lucid/varnish-2.1 Translation-en_IN                                    
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN                                     
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_IN                                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN                                            
Hit [http://software.open-xchange.com](http://software.open-xchange.com)  Release                                                                    
Hit [http://repo.varnish-cache.org](http://repo.varnish-cache.org) lucid Release                                                                                      
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                                                                                 
Hit [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN                                                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                                                   
Hit [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN                                                                                          
Ign [http://software.open-xchange.com](http://software.open-xchange.com)  Packages                                                                   
Ign [http://repo.varnish-cache.org](http://repo.varnish-cache.org) lucid/varnish-2.1 Packages                                                     
Ign [http://software.open-xchange.com](http://software.open-xchange.com)  Packages                                                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN                                        
Ign [http://repo.varnish-cache.org](http://repo.varnish-cache.org) lucid/varnish-2.1 Packages                                                     
Hit [http://software.open-xchange.com](http://software.open-xchange.com)  Packages                                             
Hit [http://repo.varnish-cache.org](http://repo.varnish-cache.org) lucid/varnish-2.1 Packages                               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN                                                                                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://dl.google.com/linux/mod-pagespeed/deb/](http://dl.google.com/linux/mod-pagespeed/deb/) stable/main Translation-en_IN
Ign [http://dl.google.com](http://dl.google.com) stable Release          
Get:2 [http://dl.google.com](http://dl.google.com) stable/main Packages [501B]
Fetched 690B in 2min 2s (6B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please suggest me the best way to over come with the error and make my OS run faster enough.

Thanks,
Gulab Pasha

---

### Post by zvacet on 2010-12-09
First of all,sorry fro mistake I made in last post.I tried to suggest you to replace 

> deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

with 

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe

But it look like they work well except for extras you added.Remove 

> ## universe repositories
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe



because you already have them.I believe you know how to do it but just in case


```
gksudo gedit /etc/apt/sources.list
```

and make changes.Save and close file.

```
sudo apt-get update && sudo apt-get upgrade
```

If you still get error 1 then

```
sudo dpkg --configure -a
```

---

### Post by gulabpasha on 2010-12-10
Hi,

I have commented all the six lines in my sources.list file and apt-get update && apt-get upgrade, but get the same error.

And I also ran dpkg --configure -a still get the same error.

## universe repositories
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid universe

#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates universe

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe

Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc


Please help, 

As i followed all the possible things to fix it,

apt-get install -f
apt-get --fix-missing
dpkg --configure -a

etc.

Thanks,
Gulab

---

### Post by zvacet on 2010-12-12
```
sudo dpkg --configure grub-pc
```

---

### Post by gulabpasha on 2010-12-12
Hi,

Thanks for your reply, and hope this command will not effect to my current OS (sudo dpkg --configure grub-pc).

I mean to say this will not erase my OS.

Looking forward to your more support.

Thanks,
Gulab

---

### Post by zvacet on 2010-12-14
I believe it will not erase your OS.Just trying to configure one exact package,because if you run

```
sudo dpkg --configure -a
```it should configure all uncofigured packages.Last command simply trying to configure just one package.

---

### Post by gulabpasha on 2010-12-15
Hi,

I get the below error when try to execute any of package install command.

root@sfdlabs:~# dpkg --configure grup-pc
dpkg: error processing grup-pc (--configure):
 no package named `grup-pc' is installed, cannot configure
Errors were encountered while processing:
 grup-pc

root@sfdlabs:~# dpkg --configure -a
Setting up grub-pc (1.98-1ubuntu9) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 grub-pc


Please help me.

Thanks,
Gulab Pasha

---

### Post by zvacet on 2010-12-15
You can try to reinstalll grub from live CD following
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

