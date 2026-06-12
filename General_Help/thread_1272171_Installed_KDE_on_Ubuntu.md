---
title: "Installed KDE on Ubuntu"
date: 2009-09-21
forum: General Help
---

### Post by UKBB on 2009-09-21
I followed these instructions to install KDE on Ubuntu. 

[http://news.softpedia.com/news/How-to-Install-KDE-4-3-on-Ubuntu-9-04-118645.shtml](http://news.softpedia.com/news/How-to-Install-KDE-4-3-on-Ubuntu-9-04-118645.shtml)

I got an error that the docs didn't install but when the pc rebooted I was able to complete the instructions and now KDE works. The only problem is that I don't have docs and every time I try to install a program it fails because the docs aren't there. I also see 2 updates available when I hover the mouse over the update icon. When I open update manager they show up under blocked updates. Is there any way to get the docs to install and clear the blocked updates from the update manager?

---

### Post by DasEi on 2009-09-21
try sudo init 1  in trml , then  choose repair broken packages,  without x it should update successful then

---

### Post by UKBB on 2009-09-21
I gave that a whirl and now it's really mad at me and I still see "1 Blocked Update"

[IMG]http://img.photobucket.com/albums/v211/ukbankerboy/kdeubuntusnapshot.png[/IMG]

---

### Post by UKBB on 2009-09-22
Anyone?

---

### Post by ianmillington on 2009-09-22
Hmmmm, I'm running kubuntu 9.04 with KDE4.3.1. I may be wrong but I thought that the repository referred to is primarily intended as an update to an existing KDE installation as opposed to a new installation. 

On looking at the packages that you say failed, I recognise some of them from this mornings update. It may simply be an update that has failed. Can I recommend that you open a terminal and do 

sudo apt-get update

and then 

sudo apt-get dist-upgrade

What output do you get?

---

### Post by UKBB on 2009-09-22
> **ianmillington said:**
> Hmmmm, I'm running kubuntu 9.04 with KDE4.3.1. I may be wrong but I thought that the repository referred to is primarily intended as an update to an existing KDE installation as opposed to a new installation. 

On looking at the packages that you say failed, I recognise some of them from this mornings update. It may simply be an update that has failed. Can I recommend that you open a terminal and do 

sudo apt-get update

and then 

sudo apt-get dist-upgrade

What output do you get?

	 	 	 	 	  ukbb@ukbb-desktop:~/Documents$ sudo apt-get update 
 [sudo] password for ukbb:  
 Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release.gpg 
 Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Translation-en_US                           
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg                                 
 Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                      
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                      
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US           
 Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty Release                                          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                             
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                  
 Hit [http://le-web.org](http://le-web.org) stable Release.gpg                                        
 Ign [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                    
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                     
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US     
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US       
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US     
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                          
 Hit [http://apt.boxee.tv](http://apt.boxee.tv) jaunty/main Packages                                    
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US            
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
 Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg [189B] 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US       
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US   
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US     
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US 
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US    
 Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US  
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                 
 Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                               
 Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release [49.6kB]              
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages              
 Ign [http://le-web.org](http://le-web.org) stable/main Translation-en_US                       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources 
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources            
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages             
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources              
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages           
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources            
 Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages [177kB] 
 Hit [http://le-web.org](http://le-web.org) stable Release                                  
 Ign [http://le-web.org](http://le-web.org) stable/main Packages                                      
 Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages [2589B]   
 Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources [50.3kB] 
 Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources [623B] 
 Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages [56.0kB] 
 Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources [14.9kB]     
 Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages [8128B]   
 Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources [2505B]   
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages              
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages        
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages          
 Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages        
 Hit [http://le-web.org](http://le-web.org) stable/main Packages                                   
 Fetched 362kB in 4s (85.7kB/s)                 
 Reading package lists... Done 
 ukbb@ukbb-desktop:~/Documents$ sudo apt-get dist-upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Calculating upgrade... Done 
 The following NEW packages will be installed: 
   libkonqsidebarplugin4 
 The following packages will be upgraded: 
   konqueror 
 1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded. 
 1 not fully installed or removed. 
 Need to get 1309kB of archives. 
 After this operation, 69.6kB disk space will be freed. 
 Do you want to continue [Y/n]? y 
 Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main libkonqsidebarplugin4 4:4.3.1-0ubuntu1~jaunty1~ppa2 [71.0kB] 
 Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main konqueror 4:4.3.1-0ubuntu1~jaunty1~ppa2 [1238kB] 
 Fetched 1309kB in 9s (133kB/s)                                                  
 Selecting previously deselected package libkonqsidebarplugin4. 
 (Reading database ... 207202 files and directories currently installed.) 
 Unpacking libkonqsidebarplugin4 (from .../libkonqsidebarplugin4_4%3a4.3.1-0ubuntu1~jaunty1~ppa2_i386.deb) ... 
 Replacing files in old package konqueror ... 
 Preparing to replace konqueror 4:4.2.2-0ubuntu4 (using .../konqueror_4%3a4.3.1-0ubuntu1~jaunty1~ppa2_i386.deb) ... 
 Unpacking replacement konqueror ... 
 Processing triggers for man-db ... 
 Setting up libkonqsidebarplugin4 (4:4.3.1-0ubuntu1~jaunty1~ppa2) ... 
  
 Setting up konqueror (4:4.3.1-0ubuntu1~jaunty1~ppa2) ... 
  
 Setting up kubuntu-docs (9.04.2) ... 
 ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory 
 dpkg: error processing kubuntu-docs (--configure): 
  subprocess post-installation script returned error exit status 1 
 Processing triggers for libc6 ... 
 ldconfig deferred processing now taking place 
 Errors were encountered while processing: 
  kubuntu-docs 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 ukbb@ukbb-desktop:~/Documents$

---

### Post by wojox on 2009-09-22
Try:

```
sudo apt-get -f install
```

To force the install. Then run apt-get upgrade again.

---

### Post by MorayJ on 2009-09-22
I think that I just used this command to install it - maybe not useful to you at the moment:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by UKBB on 2009-09-22
v> **wojox said:**
> Try:

```
sudo apt-get -f install
```To force the install. Then run apt-get upgrade again.


  	 	 	 	 	 	  ukbb@ukbb-desktop:~/Documents$ sudo apt-get -f install 
 [sudo] password for ukbb:  
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 The following packages were automatically installed and are no longer required: 
   python-alsaaudio python-awn-extras python-sqlalchemy python-awn libawn0 
   python-utidylib libtidy-0.99-0 libawn-extras0 python-feedparser 
   avant-window-navigator-data python-dateutil python-awnlib sqlite3 
   python-xlib python-chardet qt4-qtconfig 
 Use 'apt-get autoremove' to remove them. 
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
 1 not fully installed or removed. 
 After this operation, 0B of additional disk space will be used. 
 Setting up kubuntu-docs (9.04.2) ... 
 ln: target `/usr/share/doc/kde/HTML/en/kubuntu/' is not a directory: No such file or directory 
 dpkg: error processing kubuntu-docs (--configure): 
  subprocess post-installation script returned error exit status 1 
 Errors were encountered while processing: 
  kubuntu-docs 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
 ukbb@ukbb-desktop:~/Documents$

---

### Post by wojox on 2009-09-23
[http://ubuntuforums.org/showthread.php?t=1227027](http://ubuntuforums.org/showthread.php?t=1227027)

---

### Post by UKBB on 2009-09-23
> **wojox said:**
> [http://ubuntuforums.org/showthread.php?t=1227027](http://ubuntuforums.org/showthread.php?t=1227027)
 
Thanks, that seemed to work. And thanks to all that responded.

---

