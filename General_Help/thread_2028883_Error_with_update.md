---
title: "Error with update"
date: 2012-07-19
forum: General Help
---

### Post by cal1j on 2012-07-19
Hi guys, I am relatively new to Linux and recently put Lubuntu on an HP Mini 110. While the system updated fine to start with, it recently started giving me errors when I run the update command:

sudo apt-get update && sudo apt-get upgrade

Thinking it was a problem with my etc/apt/sources.list, I replaced my sources list with a list I generated from the below. 

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

A friend recommended that I run: 

sudo dpkg --configure -a

I ran that and it didn't fix my issue. Attached is a .txt file showing the complete update and error and my sources list is shown below.

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse 

###### Ubuntu Update Repos
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-proposed main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-backports main restricted universe multiverse 

###### Ubuntu Partner Repo
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner

###### Ubuntu Extras Repo
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Audacity - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
deb [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) precise main 

#### Google Linux Software Repositories - [http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)
## Run this command: wget -q [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) -O- | sudo apt-key add -
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

#### LibreOffice - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main

#### Mozilla Daily Build Team - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) precise main

#### UNetbootin - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) precise main

#### VirtualBox - [http://www.virtualbox.org](http://www.virtualbox.org)
## Run this command: wget -q [http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc](http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc) -O- | sudo apt-key add -
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) precise contrib


####### 3rd Party Source Repos

#### Audacity (Source) - [http://audacity.sourceforge.net/](http://audacity.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BB901940
deb-src [http://ppa.launchpad.net/audacity-team/daily/ubuntu](http://ppa.launchpad.net/audacity-team/daily/ubuntu) precise main 

#### LibreOffice (Source) - [http://www.documentfoundation.org/download/](http://www.documentfoundation.org/download/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444
deb-src [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu) precise main

#### Mozilla Daily Build Team (Source) - [http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa](http://edge.launchpad.net/~ubuntu-mozilla-daily/+archive/ppa)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys  247510BE
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) precise main

#### UNetbootin (Source) - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
## Run this command: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FC91AE7E
deb-src [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) precise main

---

### Post by ptn107 on 2012-07-19
Remove everything from the 'unofficial' sections.  You are just setting yourself up for problems using those.  For the most part the versions provided by Ubuntu are just fine.  Then try updating again.

---

### Post by z3nhakr on 2012-07-19
what happens when you run "sudo apt-get check"?

---

### Post by cal1j on 2012-07-19
This is the error when I ran the above command... btw, thanks for a reply!!!


calvin@calvin-HP-Mini-110-1100:~$ sudo apt-get check
[sudo] password for calvin: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/dl.google.com_linux_deb_dists_stable_non-free_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
calvin@calvin-HP-Mini-110-1100:~$

---

### Post by cal1j on 2012-07-19
Do you mean by "unofficial", do you mean 3rd party ones?

---

### Post by NikTh on 2012-07-19
Hi , 
please open a terminal and run these command one at time (one line = one command) . Copy-paste them from here to your terminal for more accuracy. 

```
sudo wget "http://pastebin.com/raw.php?i=aDE6mdsP" -O /etc/apt/sources.list
sudo apt-get update
```give the results of last command . 
**Please put the results inside [CODE] tags , by highlighting the text and click [SIZE=3]#[/SIZE] symbol on top of message pane. **
Thanks

---

### Post by cal1j on 2012-07-19
This is the result of the above...


calvin@calvin-HP-Mini-110-1100:~$ sudo wget "http://pastebin.com/raw.php?i=aDE6mdsP" -O /etc/apt/sources.list
[sudo] password for calvin: 
--2012-07-19 23:40:47--  [http://pastebin.com/raw.php?i=aDE6mdsP](http://pastebin.com/raw.php?i=aDE6mdsP)
Resolving pastebin.com (pastebin.com)... 72.20.36.113
Connecting to pastebin.com (pastebin.com)|72.20.36.113|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `/etc/apt/sources.list'

    [ <=>                                                                                ] 961         --.-K/s   in 0s      

2012-07-19 23:40:48 (19.8 MB/s) - `/etc/apt/sources.list' saved [961]

calvin@calvin-HP-Mini-110-1100:~$ sudo apt-get update
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) precise InRelease
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release.gpg [198 B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg [198 B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release.gpg [198 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) precise Release      
Ign [http://archive.canonical.com](http://archive.canonical.com) precise Release
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release.gpg [198 B]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources/DiffIndex
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise Release [49.6 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages/DiffIndex
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner TranslationIndex
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner Sources 
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security Release [49.6 kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) precise/partner i386 Packages               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates Release [49.6 kB]     
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Sources [934 kB]             
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en_US              
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Sources [5,470 B]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Sources [5,019 kB]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Sources [155 kB]                                                     
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main i386 Packages [1,274 kB]                                                   
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted i386 Packages [8,431 B]                                              
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe i386 Packages [4,796 kB]                                               
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse i386 Packages [121 kB]                                               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main TranslationIndex                                                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted TranslationIndex                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe TranslationIndex                                                          
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Sources [30.0 kB]                                                 
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Sources [14 B]                                              
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Sources [7,849 B]                                             
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Sources [713 B]                                             
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main i386 Packages [97.6 kB]                                           
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted i386 Packages [14 B]                                        
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe i386 Packages [24.4 kB]                                       
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse i386 Packages [1,394 B]                                     
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main TranslationIndex [73 B]                                           
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse TranslationIndex [71 B]                                     
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted TranslationIndex [70 B]                                     
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe TranslationIndex [73 B]                                       
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Sources [133 kB]                                                   
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Sources [1,379 B]                                            
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Sources [36.4 kB]                                              
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Sources [1,058 B]                                            
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main i386 Packages [330 kB]                                             
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted i386 Packages [2,439 B]                                      
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe i386 Packages [95.2 kB]                                        
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse i386 Packages [2,047 B]                                      
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B]                                         
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B]                                   
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B]                                   
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B]                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/main Translation-en                                                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/multiverse Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/restricted Translation-en                                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise/universe Translation-en                                                            
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/main Translation-en [50.5 kB]                                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/multiverse Translation-en                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/restricted Translation-en                                                 
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-security/universe Translation-en [15.6 kB]                                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/main Translation-en                                                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/multiverse Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en                                                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en                                                    
Fetched 13.3 MB in 1min 10s (187 kB/s)                                                                                      
Reading package lists... Done
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by NikTh on 2012-07-19
Run these commands 
```
sudo apt-get clean 
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
``` 

Post the results of last command. 
**PLEASE put the results inside [CODE] tags by highlighting the text and click # symbol on top of message pane.**
Thanks

---

### Post by cal1j on 2012-07-20
> **NikTh said:**
> Run these commands 
```
sudo apt-get clean 
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update
``` 

Post the results of last command. 
**PLEASE put the results inside [CODE] tags by highlighting the text and click # symbol on top of message pane.**
Thanks
# The first line simply allowed me to back up the /var/lib/apt/lists/*
calvin@calvin-HP-Mini-110-1100:~$  gedit /var/lib/apt/lists/*
calvin@calvin-HP-Mini-110-1100:~$ sudo apt-get clean 
calvin@calvin-HP-Mini-110-1100:~$ sudo rm -rf /var/lib/apt/lists/*
calvin@calvin-HP-Mini-110-1100:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com precise InRelease
Ign http://us.archive.ubuntu.com precise-security InRelease
Ign http://us.archive.ubuntu.com precise-updates InRelease
Get:1 http://us.archive.ubuntu.com precise Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise-security Release.gpg [198 B]
Ign http://archive.canonical.com precise InRelease    
Get:3 http://archive.canonical.com precise Release.gpg [198 B]
Get:4 http://archive.canonical.com precise Release [7,078 B]
Get:5 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Get:6 http://us.archive.ubuntu.com precise Release [49.6 kB]        
Get:7 http://archive.canonical.com precise/partner Sources [3,430 B]
Get:8 http://archive.canonical.com precise/partner i386 Packages [4,982 B]     
Ign http://archive.canonical.com precise/partner TranslationIndex              
Get:9 http://us.archive.ubuntu.com precise-security Release [49.6 kB]          
Get:10 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]          
Ign http://archive.canonical.com precise/partner Translation-en_US            
Ign http://archive.canonical.com precise/partner Translation-en
Get:11 http://us.archive.ubuntu.com precise/main Sources [934 kB]
Get:12 http://us.archive.ubuntu.com precise/restricted Sources [5,470 B]       
Get:13 http://us.archive.ubuntu.com precise/universe Sources [5,019 kB]        
Get:14 http://us.archive.ubuntu.com precise/multiverse Sources [155 kB]        
Get:15 http://us.archive.ubuntu.com precise/main i386 Packages [1,274 kB]      
Get:16 http://us.archive.ubuntu.com precise/restricted i386 Packages [8,431 B] 
Get:17 http://us.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]  
Get:18 http://us.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]  
Get:19 http://us.archive.ubuntu.com precise/main TranslationIndex [3,706 B]    
Get:20 http://us.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:21 http://us.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:22 http://us.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:23 http://us.archive.ubuntu.com precise-security/main Sources [30.0 kB]    
Get:24 http://us.archive.ubuntu.com precise-security/restricted Sources [14 B] 
Get:25 http://us.archive.ubuntu.com precise-security/universe Sources [7,849 B]
Get:26 http://us.archive.ubuntu.com precise-security/multiverse Sources [713 B]
Get:27 http://us.archive.ubuntu.com precise-security/main i386 Packages [97.6 kB]
Get:28 http://us.archive.ubuntu.com precise-security/restricted i386 Packages [14 B]
Get:29 http://us.archive.ubuntu.com precise-security/universe i386 Packages [24.4 kB]
Get:30 http://us.archive.ubuntu.com precise-security/multiverse i386 Packages [1,394 B]
Get:31 http://us.archive.ubuntu.com precise-security/main TranslationIndex [73 B]
Get:32 http://us.archive.ubuntu.com precise-security/multiverse TranslationIndex [71 B]
Get:33 http://us.archive.ubuntu.com precise-security/restricted TranslationIndex [70 B]
Get:34 http://us.archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:35 http://us.archive.ubuntu.com precise-updates/main Sources [134 kB]      
Get:36 http://us.archive.ubuntu.com precise-updates/restricted Sources [1,379 B]
Get:37 http://us.archive.ubuntu.com precise-updates/universe Sources [37.6 kB] 
Get:38 http://us.archive.ubuntu.com precise-updates/multiverse Sources [1,058 B]
Get:39 http://us.archive.ubuntu.com precise-updates/main i386 Packages [332 kB]
Get:40 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [2,439 B]
Get:41 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [97.1 kB]
Get:42 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [2,047 B]
Get:43 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:44 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:45 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:46 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Get:47 http://us.archive.ubuntu.com precise/main Translation-en [726 kB]       
Get:48 http://us.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]
Get:49 http://us.archive.ubuntu.com precise/restricted Translation-en [2,395 B]
Get:50 http://us.archive.ubuntu.com precise/universe Translation-en [3,341 kB] 
Get:51 http://us.archive.ubuntu.com precise-security/main Translation-en [50.5 kB]
Get:52 http://us.archive.ubuntu.com precise-security/multiverse Translation-en [587 B]
Get:53 http://us.archive.ubuntu.com precise-security/restricted Translation-en [14 B]
Get:54 http://us.archive.ubuntu.com precise-security/universe Translation-en [15.6 kB]
Get:55 http://us.archive.ubuntu.com precise-updates/main Translation-en [156 kB]
Get:56 http://us.archive.ubuntu.com precise-updates/multiverse Translation-en [912 B]
Get:57 http://us.archive.ubuntu.com precise-updates/restricted Translation-en [798 B]
Get:58 http://us.archive.ubuntu.com precise-updates/universe Translation-en [58.2 kB]
Fetched 17.7 MB in 51s (341 kB/s)                                              
Reading package lists... Done
calvin@calvin-HP-Mini-110-1100:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 fbreader : Depends: libzlcore0.12 but it is not installed
 libzltext0.12 : Depends: libzlcore0.12 (= 0.12.10dfsg-6) but it is not installed
 libzlui-qt4 : Depends: libzlcore0.12 (= 0.12.10dfsg-6) but it is not installed
E: Unmet dependencies. Try using -f.
calvin@calvin-HP-Mini-110-1100:~$

---

### Post by NikTh on 2012-07-20
Hi , 
try to follow what apt-get suggests. 
```
sudo apt-get -f install
sudo apt-get update
``` 
Thanks

---

