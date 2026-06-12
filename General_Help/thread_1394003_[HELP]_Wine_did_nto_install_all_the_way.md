---
title: "[HELP] Wine did nto install all the way"
date: 2010-01-30
forum: General Help
---

### Post by retro_killa on 2010-01-30
I went to the Wine HQ website & I did the step by step how to install wine on Ubuntu 9.10. Please help me fix this issue I would love to get Photoshop running on Wine thanks a lot. 

**This is the log from the terminal**

```
warren@ACER-Aspire-9300:~$ sudo add-apt-repository ppa:ubuntu-wine/ppa
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv 883E8688397576B6C509DF495A9A06AEF9CB8DB0
gpg: requesting key F9CB8DB0 from hkp server keyserver.ubuntu.com
gpg: key F9CB8DB0: "Launchpad PPA for Ubuntu Wine Team" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
warren@ACER-Aspire-9300:~$ sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release.gpg                      
Ign http://ppa.launchpad.net karmic/main Translation-en_US           
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
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
Hit http://ppa.launchpad.net karmic Release    
Hit http://us.archive.ubuntu.com karmic Release                     
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://us.archive.ubuntu.com karmic-updates Release              
Hit http://ppa.launchpad.net karmic/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
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
Reading package lists... Done
warren@ACER-Aspire-9300:~$ sudi aot-get install wine
No command 'sudi' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
sudi: command not found
warren@ACER-Aspire-9300:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
warren@ACER-Aspire-9300:~$ sudo apt-get uninstall wine
E: Invalid operation uninstall
warren@ACER-Aspire-9300:~$ sudo apt-get un-install wine
E: Invalid operation un-install
warren@ACER-Aspire-9300:~$ sudo apt-get remove wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
The following packages were automatically installed and are no longer required:
  wine-gecko
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
warren@ACER-Aspire-9300:~$ apt-get autoremove
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
warren@ACER-Aspire-9300:~$ apt-get autoremove wine
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
warren@ACER-Aspire-9300:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: wine1.2 but it is not going to be installed
E: Broken packages
warren@ACER-Aspire-9300:~$ 


```

---

### Post by Woody1987 on 2010-01-30
try sudo apt-get -f install

---

### Post by NightwishFan on 2010-01-30
I had this problem. I use the Wine packages from:
[https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages](https://launchpad.net/~ubuntu-wine/+archive/ppa/+packages)

Unless you have a known reason to use a newer wine, I actually suggest you try the stable Wine 1.1 from the repository. If it does work, it mostly works better.

---

