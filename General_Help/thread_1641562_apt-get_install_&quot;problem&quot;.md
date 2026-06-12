---
title: "apt-get install &quot;problem&quot;"
date: 2010-12-09
forum: General Help
---

### Post by Xinerama on 2010-12-09
I've been having a problem installing packages.  More precisely it's the part where apt-get tries to unpack the package.
It just seems to hang and it's been happening frequently.

```

root@elias-desktop:/home/elias/Desktop# apt-get install nfoview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libdate-calc-perl libcarp-clan-perl libnet-ip-perl
  libnet-dns-perl libfile-find-rule-perl libtommath0 libdigest-hmac-perl
  libnumber-compare-perl libdigest-sha1-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xfonts-terminus
Suggested packages:
  xfonts-terminus-oblique
The following NEW packages will be installed:
  xfonts-terminus
The following packages will be upgraded:
  nfoview
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,289kB of archives.
After this operation, 2,470kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: warning: files list file for package `nfoview' missing, assuming package has no files currently installed.
(Reading database ... 313491 files and directories currently installed.)
Preparing to replace nfoview 1.8-1 (using .../archives/nfoview_1.8-1_all.deb) ...
Unpacking replacement nfoview ...

```
Should I try "sudo apt-get" I always "su" in the terminal when I want to become root.

---

### Post by miegiel on 2010-12-09
> **Xinerama said:**
> I've been having a problem installing packages.  More precisely it's the part where apt-get tries to unpack the package.
It just seems to hang and it's been happening frequently.

```

root@elias-desktop:/home/elias/Desktop# apt-get install nfoview
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libtext-glob-perl libdate-calc-perl libcarp-clan-perl libnet-ip-perl
  libnet-dns-perl libfile-find-rule-perl libtommath0 libdigest-hmac-perl
  libnumber-compare-perl libdigest-sha1-perl libbit-vector-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  xfonts-terminus
Suggested packages:
  xfonts-terminus-oblique
The following NEW packages will be installed:
  xfonts-terminus
The following packages will be upgraded:
  nfoview
1 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,289kB of archives.
After this operation, 2,470kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 
dpkg: warning: files list file for package `nfoview' missing, assuming package has no files currently installed.
(Reading database ... 313491 files and directories currently installed.)
Preparing to replace nfoview 1.8-1 (using .../archives/nfoview_1.8-1_all.deb) ...
Unpacking replacement nfoview ...

```
Should I try "sudo apt-get" I always "su" in the terminal when I want to become root.

I always do *sudo apt-get up.... etc.* Only on rare ocasions I become root by using *su*. Other things you could try.

[LIST]
[*]Search the forum or google for "dpkg: warning: files list file for package"
[*]sudo apt-get autoremove
[*]sudo apt-get autoclean
[*]Try using a different mirror to install from and get your updates.
[/LIST]


Before installing anything I also always do
```
sudo apt-get update
sudo apt-get upgrade
```
That might help too in your case.

---

### Post by amsterdamharu on 2010-12-09
```
sudo rm /var/cache/apt/archives/nfoview_1.8-1_all.deb
```
And then try again to install it.

If that didn't do the trick you can wipe all of the archive with the command:

```
sudo aptitude clean
```

---

### Post by Xinerama on 2010-12-09
Alright guys thanks for helping me out with this.  I finally got it working again.  I changed my server and removed the old package from /var/cache/apt/archives.  The crazy thing is though that when I went to install it apt said it was already installed.  And sure enough it was.

One last thing though, and maybe I need to search around for this answer.

Whenever I try to reboot after having these problems, which have been happening very frequently these days, I get this error: 
```

Checking for running unattended upgrades.

```
And the system hangs.  Is there anyway to disable this feature.  Because, when I want to reboot, that's exactly what I want to do.  I don't want to wait around.

---

### Post by Xinerama on 2010-12-09
Okay maybe I found a solution here [http://serverfault.com/questions/111201/how-to-get-automatic-upgrades-to-work-on-ubuntu-server]("http://serverfault.com/questions/111201/how-to-get-automatic-upgrades-to-work-on-ubuntu-server")
It talks about editing /etc/apt/apt.conf.d/10periodic and changing the values from 0s to 1s.
My file looked like this
```

gksu /etc/apt/apt.conf.d/10periodic &

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";

```
Then
```

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "1";
APT::Periodic::Unattended-Upgrade "1";

```
 The reason it should be a "1" instead of a "0" is:
> It should say UnattendedUpgradeInterval='1', indicating that you configured APT correctly to allow for unattended upgrades.

I hope it works.

---

### Post by Xinerama on 2010-12-10
It's working fine.  The only thing that will install on its own now are the security updates. 
Thanks everyone that read through this and those that helped.

---

### Post by miegiel on 2010-12-10
> **Xinerama said:**
> It's working fine.  The only thing that will install on its own now are the security updates. 
Thanks everyone that read through this and those that helped.

My */etc/apt/apt.conf.d/10periodic* looks like this :
```
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0"; 
```
Maybe removing the line
```
APT::Periodic::Unattended-Upgrade "1";
```
and changing the lines
```
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "1";
```
back to 0 will solve your problem too. Then you wouldn't need to worry about automatically installing updates that you don't want yet.

---

### Post by Xinerama on 2010-12-10
I removed the "Unattended Upgrade" line but left everything else.  
I'm going to give it a shot.  Also, I kind of like to know what's being installed, especially kernel minor/major patches. ;)

---

