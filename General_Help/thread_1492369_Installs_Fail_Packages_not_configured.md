---
title: "Installs Fail Packages not configured"
date: 2010-05-24
forum: General Help
---

### Post by richk1693 on 2010-05-24
When I try to install or uninstall anything it always starts working then jumps to 90% and gives me the following error

This may very well by my fault I'm very new to linux and ubuntu both. I've tried searching all over the Internet with no success. If someone could help me it would be greatly appreciated.
```
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-lazr.restfulclient
 python-launchpadlib
 python-apport
 apport
 apport-gtk
 ubuntuone-client

```

---

### Post by bumanie on 2010-05-24
You may have broken packages. Not sure that this will fix the issue, but try this code in terminal > sudo dpkg --configure -aIt will look for broken packages and download them if any are broken.

---

### Post by richk1693 on 2010-05-24
> **bumanie said:**
> You may have broken packages. Not sure that this will fix the issue, but try this code in terminal It will look for broken packages and download them if any are broken.


I tried rebooting and going into recovery mode and chose repair broken packages. I got errors along the same lines about python and the others. I tried the command you told me and it returned the same errors. The exact output:
```
richard@richard-desktop:~$ sudo dpkg --configure -a
Setting up python-lazr.restfulclient (0.9.11-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lazr.restfulclient (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-launchpadlib:
 python-launchpadlib depends on python-lazr.restfulclient (>= 0.9.11); however:
  Package python-lazr.restfulclient is not configured yet.
dpkg: error processing python-launchpadlib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on python-launchpadlib (>= 1.5.7); however:
  Package python-launchpadlib is not configured yet.
dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python-apport (>= 0.120); however:
  Package python-apport is not configured yet.
dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python-apport (>= 0.80); however:
  Package python-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntuone-client:
 ubuntuone-client depends on python-apport; however:
  Package python-apport is not configured yet.
dpkg: error processing ubuntuone-client (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-lazr.restfulclient
 python-launchpadlib
 python-apport
 apport
 apport-gtk
 ubuntuone-client
richard@richard-desktop:~$ 

```

If there is any further information that could be of use please ask and I'll get it to you as fast as I can.

---

### Post by bumanie on 2010-05-24
Ok - try > sudo apt-get update && sudo apt-get upgrade in terminal. It seems a number of things have not installed correctly for whatever reason. This may not work, but it won't do any further damage.

---

### Post by akakingess on 2010-05-24
Are you trying to install from the repositories? In other words, are you going to System--->Administration--->Synaptic Package Manager? If you are, than you should choose the package to install, and it will pull up a list of dependencies for that package and you should let it install all of those automatically. That should clear up any dependency issues if "sudo dpkg --configure -a" didn't fix it. Let us know how you are going about installing.

---

### Post by richk1693 on 2010-05-24
> **akakingess said:**
> Are you trying to install from the repositories? In other words, are you going to System--->Administration--->Synaptic Package Manager? If you are, than you should choose the package to install, and it will pull up a list of dependencies for that package and you should let it install all of those automatically. That should clear up any dependency issues if "sudo dpkg --configure -a" didn't fix it. Let us know how you are going about installing.

I was installing via terminal.


Edit: Output of the command
```
richard@richard-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://archive.ubuntu.com karmic Release.gpg                     
Ign http://archive.ubuntu.com/ubuntu/ karmic/main Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ karmic/universe Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ karmic/restricted Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ karmic/multiverse Translation-en_US
Hit http://archive.ubuntu.com karmic Release
Hit http://archive.ubuntu.com karmic/main Packages
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://archive.ubuntu.com karmic/universe Packages               
Hit http://archive.ubuntu.com karmic/restricted Packages
Hit http://archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up python-lazr.restfulclient (0.9.11-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-lazr.restfulclient (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 python-lazr.restfulclient
E: Sub-process /usr/bin/dpkg returned an error code (1)
richard@richard-desktop:~$ 

```

---

### Post by akakingess on 2010-05-24
If you are using apt-get then it should still download and install the dependencies for it so there is definitely something else going on. I would recommend uninstalling/purging that software and starting again from scratch?

---

### Post by richk1693 on 2010-05-24
> **akakingess said:**
> If you are using apt-get then it should still download and install the dependencies for it so there is definitely something else going on. I would recommend uninstalling/purging that software and starting again from scratch?
As in total fresh install of ubuntu?

---

### Post by akakingess on 2010-05-24
Oh no, I just meant the package that you were installing or trying to install, in case it had done some directory/file creation and then gotten interrupted. I would only recommend reinstalling Ubuntu as an easy alternative if you have a separate /home partition.

---

### Post by richk1693 on 2010-05-24
> **akakingess said:**
> Oh no, I just meant the package that you were installing or trying to install, in case it had done some directory/file creation and then gotten interrupted. I would only recommend reinstalling Ubuntu as an easy alternative if you have a separate /home partition.

This same error happens with all packages. I've tried several and they  all return the same errors on install or uninstall. I'm currently dual booting windows 7 and ubuntu. Reinstalling ubuntu wouldn't be that much of a problem, although I'm not sure how to format linux without losing windows.

---

### Post by akakingess on 2010-05-24
You can reinstall Ubuntu and it will in the process reinstall Grub which should automatically notice the Windows OS and add it to the Grub menu, so if you don't have much installed or saved under the Ubuntu stuff, than you should be OK reinstalling Linux, although as always backing up critical data is recommended (even on the Windows side, although you shouldn't be touching that partition).

---

