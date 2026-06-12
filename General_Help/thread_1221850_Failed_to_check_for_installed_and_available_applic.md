---
title: "Failed to check for installed and available applications"
date: 2009-07-24
forum: General Help
---

### Post by On Boards on 2009-07-24
hello , i've removed some games and software's that i don't use/need .. now every time i try to open the add/remove menu i get this message 

```

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.


```
i entered the terminal 

:~$ sudo apt-get update
```
[sudo] password : 
Get:1 http://packages.medibuntu.org jaunty Release.gpg [197B]
Hit http://us.archive.ubuntu.com jaunty Release.gpg    
Ign http://packages.medibuntu.org jaunty/free Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US           
Get:2 http://us.archive.ubuntu.com jaunty-updates Release.gpg [189B]           
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Get:3 http://packages.medibuntu.org jaunty Release [11.7kB]
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Err http://packages.medibuntu.org jaunty Release
  
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com jaunty-security Release.gpg [189B]
Ign http://us.archive.ubuntu.com jaunty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Get:5 http://us.archive.ubuntu.com jaunty Release [74.6kB]
Get:6 http://us.archive.ubuntu.com jaunty-updates Release [49.6kB]
Ign http://us.archive.ubuntu.com jaunty Release 
Err http://us.archive.ubuntu.com jaunty-updates Release
  
Get:7 http://us.archive.ubuntu.com jaunty-security Release [49.6kB]
Err http://us.archive.ubuntu.com jaunty-security Release
  
Hit http://us.archive.ubuntu.com jaunty/main Packages
Hit http://us.archive.ubuntu.com jaunty/restricted Packages                    
Hit http://us.archive.ubuntu.com jaunty/main Sources                           
Hit http://us.archive.ubuntu.com jaunty/restricted Sources                     
Hit http://us.archive.ubuntu.com jaunty/universe Packages                      
Hit http://us.archive.ubuntu.com jaunty/universe Sources                       
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages                    
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources                     
Fetched 579B in 8s (65B/s)                                                     
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
laptop:~$ 
```then sudo apt-get update
```

Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
~$ 


```thanks

---

### Post by LowSky on 2009-07-24
could you post the contents of this file
/etc/apt/sources.list with the following command


```
sudo gedit /etc/apt/sources.list
```

Also try running this command to fix apt-get

```
sudo dpkg --configure -a 
```

---

### Post by On Boards on 2009-07-24
sources.list

```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://sa.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://sa.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse


```

---

### Post by drs305 on 2009-07-24
I checked and that file is available on the server. Try moving that file to your Desktop and running your commands again. 

```
sudo mv /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages $HOME/Desktop/

```
Once things are working again open nautilus as root (gksudo nautilus) and use SHIFT-DEL to remove that file from your Desktop.

Added: We later worked on this problem and solved it by clearing the files in /var/lib/apt/lists.

---

### Post by On Boards on 2009-07-24
thanks drs

```
mv: cannot stat `/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty_restricted_binary-i386_Packages': No such file or directory

```

---

### Post by On Boards on 2009-07-27
hello , i repeated the same procedure but the problem still exist

---

### Post by On Boards on 2009-07-28
[SIZE=3]removing the files in /var/lib/apt/lists (but keeping the 'partial' folder)  was what fixed it ..a big thank you to drs305 .. 
[/SIZE]

---

