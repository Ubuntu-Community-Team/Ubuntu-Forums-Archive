---
title: "Can't update Thunderbird to 3.1.4"
date: 2010-09-28
forum: General Help
---

### Post by Ralph L on 2010-09-28
I am running Thunderbird 3.1 on lucid and I want to update to 3.1.4 to see if it fixes a couple things.  I followed the instructions on [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page).

Listed below is a copy of the Terminal output, which shows an error near the end.  I don't know how to interpret this error, nor what to do to fix it.

Any help would be appreciated.

Ralph


ralph@ralph-laptop:~$ echo -e "\ndeb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main" | sudo tee -a /etc/apt/sources.list > /dev/null
ralph@ralph-laptop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
[sudo] password for ralph: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: public key "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1

ralph@ralph-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                             
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                             
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US    
Ign [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://ppa.launchpad.net/f-spot/f-spot-ppa/ubuntu/](http://ppa.launchpad.net/f-spot/f-spot-ppa/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                 
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                                 
Ign [http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/](http://ppa.launchpad.net/ferramroberto/linuxfreedomlucid/ubuntu/) lucid/main Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Get:1 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg [198B]                  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources              
Get:2 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release [961B]                      
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages        
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages
Get:3 [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages [857B]
Fetched 2,016B in 2s (765B/s)  
Reading package lists... Done
ralph@ralph-laptop:~$ sudo apt-get install thunderbird-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libparted0 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  thunderbird-mozilla-build
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
Need to get 12.6MB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/) all/main thunderbird-mozilla-build 3.1.4-0ubuntu1 [12.6MB]
Fetched 12.6MB in 1min 33s (136kB/s)                                           
Selecting previously deselected package thunderbird-mozilla-build.
(Reading database ... 197859 files and directories currently installed.)
Unpacking thunderbird-mozilla-build (from .../thunderbird-mozilla-build_3.1.4-0ubuntu1_i386.deb) ...
dpkg-divert: `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build' clashes with `local diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu'
dpkg: error processing /var/cache/apt/archives/thunderbird-mozilla-build_3.1.4-0ubuntu1_i386.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
dpkg-divert: mismatch on package
  when removing `diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu by thunderbird-mozilla-build'
  found `local diversion of /usr/bin/thunderbird to /usr/bin/thunderbird.ubuntu'
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/thunderbird-mozilla-build_3.1.4-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ralph@ralph-laptop:~$

---

### Post by andrewthomas on 2010-09-29
Use this ppa

[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
```
sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa
```

---

### Post by Ralph L on 2010-09-30
Andrewthomas

Thank you for your response.  I went to the web site you recommended and got the latest unstable version (3.1.5), installed it and it worked very well so far.  However, I don't usually install unstable versions.  Is there a ppa from which I can get the latest stable version?

Thank you again,
Ralph



Use this ppa

[https://launchpad.net/~ubuntu-mozill...y/+archive/ppa](https://launchpad.net/~ubuntu-mozill...y/+archive/ppa)
Code:

sudo add-apt-repository ppa:ubuntu-mozilla-daily/ppa

---

### Post by crichard on 2010-09-30
Why don't you try Thunderbird from Mozilla website? Here is the tutorial to [install Firefox & Thunderbird]("http://surferzworld.com/2010/01/installing-firefox-thunderbird-ubuntu/").. It's better to uninstall the previous versions of installed thunderbird & it's PPAs to avoid conflicts. 
Please Keep in mind, Don't delete **.thunderbird** folder..

---

### Post by Ralph L on 2010-10-11
The scenario I gave below does NOT work. For some reason when TB is installed using sudo, it is only accessible by using sudo. So don't do what I did.


Found an easy way to keep TB up to date.

1.  Bring up Terminal and enter "sudo thunderbird".
2.  Once TB is running go to the TB menu>Help>Check for Updates...
3.  Install the latest stable version of TB

So simple when you know how to do it.

Ralph

---

