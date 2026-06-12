---
title: "adding repository problem"
date: 2010-12-05
forum: General Help
---

### Post by psihokiller4 on 2010-12-05
I cannot add this repo why?

```
military@military-PC-linux:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
military@military-PC-linux:~$ 

```


```
military@military-PC-linux:~$ uname -a
Linux military-PC-linux 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:48:22 UTC 2010 i686 GNU/Linux
military@military-PC-linux:~$ 

```


I have similar repo: [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)




well I want to play avp 3 if any one knows any additional way around or I'll try to install wine beta

---

### Post by sikander3786 on 2010-12-05
That PPA seems to be added successfully....?

Please post the output of this one.

```
sudo apt-get update
```

---

### Post by psihokiller4 on 2010-12-05
```
military@military-PC-linux:~$ sudo apt-get update
[sudo] password for military: 
Hit http://archive.canonical.com lucid Release.gpg
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US       
Ign http://deb.playonlinux.com lucid Release.gpg                               
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/pjbroad/ppa/ubuntu/ lucid/main Translation-en_US  
Hit http://ppa.launchpad.net lucid Release.gpg                       
Hit http://archive.ubuntu.com lucid Release.gpg                      
Ign http://archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US   
Hit http://security.ubuntu.com lucid-security Release.gpg            
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://archive.canonical.com lucid Release                       
Ign http://ppa.launchpad.net/psyke83/ppa/ubuntu/ lucid/main Translation-en_US  
Hit http://ppa.launchpad.net lucid Release.gpg                       
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
Ign http://deb.playonlinux.com/ lucid/main Translation-en_US                   
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US       
Hit http://archive.ubuntu.com lucid-updates Release.gpg                        
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://archive.canonical.com lucid/partner Packages              
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com lucid-proposed Release.gpg
Get:1 http://deb.playonlinux.com lucid Release [1,722B]              
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/main Translation-en_US    
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security/restricted Packages              
Hit http://archive.canonical.com lucid/partner Sources                         
Ign http://archive.ubuntu.com/ubuntu/ lucid-proposed/universe Translation-en_US
Hit http://archive.ubuntu.com lucid-backports Release.gpg                      
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/main Translation-en_US
Ign http://deb.playonlinux.com lucid/main Packages                   
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://ppa.launchpad.net lucid/main Sources                      
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/restricted Sources     
Hit http://security.ubuntu.com lucid-security/main Sources           
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/multiverse Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-backports/universe Translation-en_US
Hit http://archive.ubuntu.com lucid Release                          
Hit http://archive.ubuntu.com lucid-updates Release                            
Hit http://archive.ubuntu.com lucid-proposed Release                           
Ign http://deb.playonlinux.com lucid/main Packages                             
Hit http://ppa.launchpad.net lucid/main Packages                               
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://archive.ubuntu.com lucid-backports Release
Hit http://deb.playonlinux.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/main Packages
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid-updates/main Packages
Hit http://archive.ubuntu.com lucid-updates/restricted Packages
Hit http://archive.ubuntu.com lucid-updates/universe Packages
Hit http://archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://archive.ubuntu.com lucid-updates/main Sources
Hit http://archive.ubuntu.com lucid-updates/restricted Sources
Hit http://archive.ubuntu.com lucid-updates/universe Sources
Hit http://archive.ubuntu.com lucid-updates/multiverse Sources
Hit http://archive.ubuntu.com lucid-proposed/restricted Packages
Hit http://archive.ubuntu.com lucid-proposed/main Packages
Hit http://archive.ubuntu.com lucid-proposed/multiverse Packages
Hit http://archive.ubuntu.com lucid-proposed/universe Packages
Hit http://archive.ubuntu.com lucid-proposed/restricted Sources
Hit http://archive.ubuntu.com lucid-proposed/main Sources
Hit http://archive.ubuntu.com lucid-proposed/multiverse Sources
Hit http://archive.ubuntu.com lucid-proposed/universe Sources
Hit http://archive.ubuntu.com lucid-backports/restricted Packages
Hit http://archive.ubuntu.com lucid-backports/main Packages
Hit http://archive.ubuntu.com lucid-backports/multiverse Packages
Hit http://archive.ubuntu.com lucid-backports/universe Packages
Hit http://archive.ubuntu.com lucid-backports/restricted Sources
Hit http://archive.ubuntu.com lucid-backports/main Sources
Hit http://archive.ubuntu.com lucid-backports/multiverse Sources
Hit http://archive.ubuntu.com lucid-backports/universe Sources
Fetched 1B in 1s (1B/s)
Reading package lists... Done
military@military-PC-linux:~$ 
```


yes ok but I cannot find it in

System --> Administration --> Software Sources

2 unchecked + CD
[http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/)
[http://si.archive.ubuntu.com/ubuntu/](http://si.archive.ubuntu.com/ubuntu/)


and 7 checked repo
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu)
[http://ppa.launchpad.net/pjbroad/ppa/ubuntu](http://ppa.launchpad.net/pjbroad/ppa/ubuntu)
[http://ppa.launchpad.net/pjbroad/ppa/ubuntu](http://ppa.launchpad.net/pjbroad/ppa/ubuntu)
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu)
[http://ppa.launchpad.net/psyke83/ppa/ubuntu](http://ppa.launchpad.net/psyke83/ppa/ubuntu)
[http://deb.playonlinux.com/](http://deb.playonlinux.com/)

---

### Post by psihokiller4 on 2010-12-05
ok now I found page from where I can add this 2 repos

[https://launchpad.net/~ubuntu-wine/+archive/ppa](https://launchpad.net/~ubuntu-wine/+archive/ppa)

problem solved don't know why only

```
ppa:ubuntu-wine/ppa
```* this doesn't work and I have to add:*

```
deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) lucid main
```and this works problem solved

---

### Post by sikander3786 on 2010-12-05
Seems like it already added here.

> ```
Ign http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ lucid/main Translation-en_US
```

Remove the previous versions of wine (if any).

```
sudo apt-get remove --purge wine
```

And install the latest i.e, 1.3.

```
sudo apt-get install wine1.3
```

---

