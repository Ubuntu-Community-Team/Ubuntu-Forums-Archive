---
title: "Upgrade FIrefox 3.0.15 to 3.5.6"
date: 2009-12-19
forum: General Help
---

### Post by webbdawg on 2009-12-19
I want to upgrade FF soI can install the adonn FireFTP. I get the message the FireFTP will not install on the current installed version.

So I run the below and get the message.

> 
dave@laptop:~$ sudo apt-get upgrade firefox
[sudo] password for dave:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  abrowser-3.5-branding firefox-3.0 firefox-3.0-branding firefox-3.5
  xulrunner-1.9 xulrunner-1.9.1
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
dave@laptop:~$


What does it mean??

Thanks
Dave

---

### Post by DeMus on 2009-12-19
> **webbdawg said:**
> I want to upgrade FF soI can install the adonn FireFTP. I get the message the FireFTP will not install on the current installed version.

So I run the below and get the message.



What does it mean??

Thanks
Dave

You are installing through apt-get AND at the same time using some other installation program, like Synaptic. You can only use one at a time so close the other first.

---

### Post by astrobob.tk on 2009-12-19
Hey DeMus,

I also want to upgrade FF from 3.0.16 to the most recent stable version. I tried apt-get upgrade firefox but I get this:

```
$ sudo apt-get upgrade firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```am i doing it wrong ?

---

### Post by DeMus on 2009-12-19
> **astrobob.tk said:**
> Hey DeMus,

I also want to upgrade FF from 3.0.16 to the most recent stable version. I tried apt-get upgrade firefox but I get this:

```
$ sudo apt-get upgrade firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```am i doing it wrong ?

Try update instead of upgrade. I believe that is better in this case.

---

### Post by howefield on 2009-12-19
> **astrobob.tk said:**
> am i doing it wrong ?

Did you do a sudo apt-get update prior to upgrading, to ensure your sources were current ?

---

### Post by astrobob.tk on 2009-12-19
> **howefield said:**
> Did you do a sudo apt-get update prior to upgrading, to ensure your sources were current ?

well yeh & i just rechecked. I did an update & then an upgrade firefox.

```

$ sudo apt-get update
Ign cdrom://Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.2) jaunty/main Translation-en_US
Ign cdrom://Kubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090421.2) jaunty/restricted Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release.gpg                     
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US          
Hit http://lb.archive.ubuntu.com jaunty Release.gpg                  
Ign http://lb.archive.ubuntu.com jaunty/main Translation-en_US       
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://deb.opera.com stable Release.gpg    
Ign http://deb.opera.com stable/non-free Translation-en_US          
Ign http://lb.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://lb.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://lb.archive.ubuntu.com jaunty/multiverse Translation-en_US
Hit http://lb.archive.ubuntu.com jaunty-updates Release.gpg
Ign http://lb.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://lb.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://lb.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://lb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security/main Packages
Hit http://deb.opera.com stable Release        
Hit http://lb.archive.ubuntu.com jaunty Release                    
Hit http://lb.archive.ubuntu.com jaunty-updates Release                        
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Ign http://deb.opera.com stable/non-free Packages                    
Hit http://lb.archive.ubuntu.com jaunty/main Packages                
Hit http://security.ubuntu.com jaunty-security/universe Sources      
Hit http://security.ubuntu.com jaunty-security/multiverse Packages   
Hit http://security.ubuntu.com jaunty-security/multiverse Sources    
Hit http://deb.opera.com stable/non-free Packages                    
Hit http://lb.archive.ubuntu.com jaunty/restricted Packages
Hit http://lb.archive.ubuntu.com jaunty/main Sources
Hit http://lb.archive.ubuntu.com jaunty/restricted Sources
Hit http://lb.archive.ubuntu.com jaunty/universe Packages
Hit http://lb.archive.ubuntu.com jaunty/universe Sources
Hit http://lb.archive.ubuntu.com jaunty/multiverse Packages
Hit http://lb.archive.ubuntu.com jaunty/multiverse Sources
Hit http://lb.archive.ubuntu.com jaunty-updates/main Packages
Hit http://lb.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://lb.archive.ubuntu.com jaunty-updates/main Sources
Hit http://lb.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://lb.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://lb.archive.ubuntu.com jaunty-updates/universe Sources
Hit http://lb.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://lb.archive.ubuntu.com jaunty-updates/multiverse Sources
Reading package lists... Done

$ sudo apt-get upgrade firefox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by webbdawg on 2009-12-19
Thanks DeMus, I was paying around and probably had a process running and did not know it.

So I re ran the upgrade:
> dave@laptop:~$ sudo apt-get upgrade firefox
[sudo] password for dave:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dave@laptop:~$


I think it will not update/upgrade because of the repository version. Even though the Mozilla site says it is available the Ubuntu developers may have not tested and approved it. Therefore it will not upgrade.

I can download the tar.bz file but I am not sure where to unpack the file to and how to install it.

Thanks
Dave

---

### Post by snowpine on 2009-12-19
Firefox 3.0 is the "correct" version for Ubuntu 9.04.

You can either upgrade to 9.10 Karmic Koala or type:

```
sudo apt-get install firefox-3.5
```

It will exist side-by-side with FF 3.0 under the code name Shiretoko.

---

### Post by webbdawg on 2009-12-19
Thanks, This all started because I wanted to install the Add on FireFtp.

---

### Post by webbdawg on 2009-12-19
Fire FTP will not work anyway. I cannot get it to see into the home > .wine > drive c folder

---

