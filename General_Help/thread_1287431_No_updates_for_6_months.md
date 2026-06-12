---
title: "No updates for 6 months"
date: 2009-10-10
forum: General Help
---

### Post by stefangr1 on 2009-10-10
I usually install updates on my system about once a month. Normally, it would replace a lot of packages, like 20-50. For the last months, however (I don't remember for how long, but it must be like 4-6 months), my system reports that it hasen't found any updates at all, which is really starting to worry me now.


I'm running the long term support Ubuntu 8.04. As the information below shows, no updates were found. When I look at my firefox version, however (just to give an example),it is only Firefox/3.0.10.

Any idea what's wrong here?



stefan@stefan:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release.gpg                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Translation-en_US            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release.gpg                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Translation-en_US           
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release                           
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Translation-en_US    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-backports/multiverse Sources
Reading package lists... Done



stefan@stefan:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by plucky on 2009-10-10
You have no security updates listed.Open **System > Administration > Software Sources** and select the updates tag and make sure the first two boxes are ticked and the check for updates is also ticked.

Also post output of a terminal for ```
lsb_release -a
```


Good Luck

---

### Post by VCoolio on 2009-10-10
Also firefox is a wrong example: it won't automatically update to 3.5. You have to install the package firefox-3.5 for that (it can live next to your current version).

---

### Post by stefangr1 on 2009-10-10
The security and recommended updates were indeed uncommented, apparently. Now I changed that, updates are found again. The output of lsb_release -a is:


stefan@stefan:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy

---

### Post by slakkie on 2009-10-10
I had updates last week.

```

Wed, Oct  7 2009 13:41:24 +0200

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 9 packages, and remove 0 packages.
4096B of disk space will be freed
===============================================================================
[UPGRADE] libglib2.0-0 2.16.6-0ubuntu1.1 -> 2.16.6-0ubuntu1.2
[UPGRADE] libglib2.0-data 2.16.6-0ubuntu1.1 -> 2.16.6-0ubuntu1.2
[UPGRADE] libsmbclient 3.0.28a-1ubuntu4.8 -> 3.0.28a-1ubuntu4.9
[UPGRADE] samba 3.0.28a-1ubuntu4.8 -> 3.0.28a-1ubuntu4.9
[UPGRADE] samba-common 3.0.28a-1ubuntu4.8 -> 3.0.28a-1ubuntu4.9
[UPGRADE] smbclient 3.0.28a-1ubuntu4.8 -> 3.0.28a-1ubuntu4.9
[UPGRADE] smbfs 3.0.28a-1ubuntu4.8 -> 3.0.28a-1ubuntu4.9
[UPGRADE] tzdata 2009m-0ubuntu0.8.04 -> 2009n-0ubuntu0.8.04
[UPGRADE] wget 1.10.2-3ubuntu1 -> 1.10.2-3ubuntu1.1
===============================================================================

```

Be aware that there is an upcoming point release 8.04.4 somewhere jan/feb/mar 2010 (see [http://www.ubuntu.com/products/ubuntu/release-cycle](http://www.ubuntu.com/products/ubuntu/release-cycle) ).

Do you have pinning enabled of some sort? Or put packages on hold? I see you are still running 8.04.2, while I'm running 8.04.3. 

Please run 
```

sudo mv /etc/apt/preferences /etc/apt/preferences.OLD
sudo aptitude

```

When in aptitude hit, ctrl t, then select cancel pending actions. Could be that you are holding packages at a particular version..

also, dpkg --get-selections | grep hold and see if anythings shows up.

---

