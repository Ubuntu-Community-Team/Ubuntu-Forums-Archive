---
title: "Syanptic manager/Update Help"
date: 2011-09-26
forum: General Help
---

### Post by iNeko on 2011-09-26
Okay so here it goes. I am running on Ubuntu lucid lynx 10.04. I am new to this. 

I wanted to update to 10.10 and then
 I wanted to install a tablet. 
The Genius MousePen 8x6 - Which I know there Is a guide for. 


When I go to the Synaptics Manager I get This
E: The package ttf-lyx needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


One problem. When I go to upgrade in the update manager I get this. 

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first

Also I have gotten this when continueing A partial upgrade

Remove package in bad state

The package 'ttf-lyx' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?


It keeps on telling me I need to Reinstall ttf-lyx as well..

---

### Post by raja.genupula on 2011-09-26
I think you have closed your update in middle , so to avoid that lock i think you should have to restart your system. 

do you got any errors while doing update?
```
sudo apt-get update
```
please post the output if you got any errors.

---

### Post by iNeko on 2011-09-26
> **raja.genupula said:**
> I think you have closed your update in middle , so to avoid that lock i think you should have to restart your system. 

do you got any errors while doing update?
```
sudo apt-get update
```please post the output if you got any errors.


```
neko@ubuntu:~$ sudo apt-get update
Hit http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_US
Hit http://archive.canonical.com maverick Release                        
Hit http://archive.canonical.com maverick/partner Packages               
Hit http://archive.canonical.com maverick/partner Sources                
Hit http://archive.ubuntu.com maverick Release.gpg                       
Hit http://archive.ubuntu.com maverick Release                       
Hit http://archive.ubuntu.com maverick/restricted Sources            
Hit http://archive.ubuntu.com maverick/main Sources                  
Hit http://us.archive.ubuntu.com maverick Release.gpg
Hit http://security.ubuntu.com maverick-security Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg
Hit http://security.ubuntu.com maverick-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security/main Packages
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com maverick-security/restricted Packages
Hit http://us.archive.ubuntu.com maverick Release
Hit http://security.ubuntu.com maverick-security/restricted Sources  
Hit http://us.archive.ubuntu.com maverick-updates Release
Hit http://security.ubuntu.com maverick-security/main Sources        
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/universe Packages
Hit http://us.archive.ubuntu.com maverick/main Packages
Hit http://security.ubuntu.com maverick-security/multiverse Packages
Hit http://us.archive.ubuntu.com maverick/restricted Packages
Hit http://us.archive.ubuntu.com maverick/restricted Sources
Hit http://us.archive.ubuntu.com maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/multiverse Sources
Hit http://us.archive.ubuntu.com maverick/universe Sources
Hit http://us.archive.ubuntu.com maverick/universe Packages
Hit http://us.archive.ubuntu.com maverick/multiverse Packages
Hit http://us.archive.ubuntu.com maverick-updates/main Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Packages
Reading package lists... Done
neko@ubuntu:~$ ^C
neko@ubuntu:~$ 

```

Is what comes back to me. 

When I go to the update manager I get this. 

> 
"Not all updates can be installed"
Run A partial upgrade , to install as many updates as possible. 

This can be caused by 
* A previous upgrade the didn't complete
* A problem with some installed software
*Unofficial software packages not provided by Ubuntu
* Normal changes of pre-release version of Ubuntu

So Then I click "Partial Upgrade"

I get this 

> The package 'ttf-lyx' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Do you want to remove this package now to continue?

I click yes, And then get this. 

> Package in inconsistent state

The package 'ttf-lyx' is in an inconsistent state and needs to be reinstalled, but no archive can be found for it. Please reinstall the package manually or remove it from the system.


---

### Post by raja.genupula on 2011-09-26
```
sudo aptitude remove ttf-lyx
```

or ```
sudo apt-get remove ttf-lyx
```

actually both are same.but give a try to them .

if fails then install this and try to do update again.

[http://pkgs.org/ubuntu-10.10/ubuntu-universe-i386/ttf-lyx_1.6.7-1_all.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-universe-i386/ttf-lyx_1.6.7-1_all.deb.html)

get that software from the above link and install it by opening with software center and then run update again .

all the best.

---

### Post by iNeko on 2011-09-26
> **raja.genupula said:**
> ```
sudo aptitude remove ttf-lyx
```or ```
sudo apt-get remove ttf-lyx
```actually both are same.but give a try to them .

if fails then install this and try to do update again.

[http://pkgs.org/ubuntu-10.10/ubuntu-universe-i386/ttf-lyx_1.6.7-1_all.deb.html](http://pkgs.org/ubuntu-10.10/ubuntu-universe-i386/ttf-lyx_1.6.7-1_all.deb.html)

get that software from the above link and install it by opening with software center and then run update again .

all the best.


How do i open it through software center? 

I tried opening it through the GDebi package installer and it says 


> Error: A Later version is already installed.  

thanks again so much for your help

---

### Post by raja.genupula on 2011-09-26
what version you are using ?

&

give a try with this

```
sudo dpkg-reconfigure ttf-lyx
```

---

### Post by iNeko on 2011-09-26
> **raja.genupula said:**
> what version you are using ?

&

give a try with this

```
sudo dpkg-reconfigure ttf-lyx
```


Ubuntu 10.04 lucid lynx

this is what I got back from your command

```
neko@ubuntu:~$ sudo dpkg-reconfigure ttf-lyx
/usr/sbin/dpkg-reconfigure: ttf-lyx is broken or not fully installed
neko@ubuntu:~$ 

```

---

### Post by raja.genupula on 2011-09-26
Do this, i hope its gonna fixed.

```
sudo apt-get install --reinstall ttf-lyx
```

if its lost anything then we can get it by using that .

Sorry for not mentioning the requirement properly , actually i need your ttf-lyx current  version . 

all the best.

---

### Post by iNeko on 2011-09-26
> **raja.genupula said:**
> Do this, i hope its gonna fixed.

```
sudo apt-get install --reinstall ttf-lyx
```if its lost anything then we can get it by using that .

Sorry for not mentioning the requirement properly , actually i need your ttf-lyx current  version . 

all the best.


This is what I got from the command you gave me

```
neko@ubuntu:~$ sudo apt-get install --reinstall ttf-lyx
[sudo] password for neko: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of ttf-lyx is not possible, it cannot be downloaded.
The following packages will be REMOVED:
  ttf-lyx
0 upgraded, 0 newly installed, 1 to remove and 1225 not upgraded.
1 not fully installed or removed.
After this operation, 365kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 241480 files and directories currently installed.)
Removing ttf-lyx ...
/var/lib/dpkg/info/ttf-lyx.postrm: 6: dpkg-maintscript-helper: not found
dpkg: error processing ttf-lyx (--remove):
 subprocess installed post-removal script returned error exit status 127
Errors were encountered while processing:
 ttf-lyx
E: Sub-process /usr
```And may I ask how I check that? what ttf-lyx im using.

---

### Post by raja.genupula on 2011-09-26
Hi man ,I am really trying to help you with what i know.

[http://ubuntuforums.org/showthread.php?t=987251](http://ubuntuforums.org/showthread.php?t=987251)

[https://bugs.launchpad.net/openoffice/+bug/274556](https://bugs.launchpad.net/openoffice/+bug/274556)

replace that open office word with your ttf-lyx


All The Best.

---

### Post by iNeko on 2011-09-26
> **raja.genupula said:**
> Hi man ,I am really trying to help you with what i know.

[http://ubuntuforums.org/showthread.php?t=987251](http://ubuntuforums.org/showthread.php?t=987251)

[https://bugs.launchpad.net/openoffice/+bug/274556](https://bugs.launchpad.net/openoffice/+bug/274556)

replace that open office word with your ttf-lyx


All The Best.


I Am a girl :] and yes thank you sorry if i sounded rude somehow I am not meaning to be. 
I was actually asking how to see what ttf-lyx I am using? 

I am a super beginner and this. I am not sure what you mean i went onto the links and got slightly confused.

---

### Post by sam81 on 2011-09-26
try moving this file somewhere else:
```
sudo mv /var/lib/dpkg/info/ttf-lyx.postrm /home/yourhome/

```

and then:
```
 sudo apt-get remove ttf-lyx 
```

it worked for me!

---

### Post by AFarris01 on 2011-09-30
I was just having the same issue with my laptop, and moving the ttf-lyx.postrm script did the trick.

silly maintainers and their silly removal script bugs ;)

---

