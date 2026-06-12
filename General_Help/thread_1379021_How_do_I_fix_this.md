---
title: "How do I fix this?"
date: 2010-01-12
forum: General Help
---

### Post by George-o on 2010-01-12
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

My lock is neither unlocked nor locked?

---

### Post by pastalavista on 2010-01-12
That means you have a package manager (Synaptic, apt-get, aptitude, Software Center, etc) running and you can only run one of those at a time. Close one before you open another.

---

### Post by George-o on 2010-01-12
All that I have open is chrome, and one terminal.

---

### Post by pastalavista on 2010-01-12
> **George-o said:**
> All that I have open is chrome, and one terminal.Perhaps it would help if you explained what you were doing when you got the error?

---

### Post by George-o on 2010-01-12
Trying to install any number of things, from java, to dvd decrypters to any of the add-ons I've been told to get to get there.

---

### Post by pastalavista on 2010-01-12
When "installing things" in Ubuntu, you are using package managers. One process (possibly udates) hasn't finished yet or was interrupted.

---

### Post by George-o on 2010-01-12
Possibly. I've restarted a few times, and keep getting that. I'm sorry, I really am pretty new to this, but I'm trying. What can I do to clear out whatever was happening?

---

### Post by pastalavista on 2010-01-12
Try booting to the recovery console and enter ```
sudo dpkg --configure -a
```and then reboot normally.

---

### Post by ad_267 on 2010-01-12
That's weird, if you've tried a few times and restarted there shouldn't be anything locking the directory. Next time you get the error try running this command and post the output here. This will tell you what application has opened the /var/lib/dpkg/lock file:
```
sudo lsof | grep /var/lib/dpkg/lock
```

---

### Post by George-o on 2010-01-12
Apparently it has gone away since the last reboot. how about this one?
code: george@george-laptop:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for george: 
--2010-01-12 05:28:36--  [http://www.medibuntu.org/sources.list.d/karmic.list](http://www.medibuntu.org/sources.list.d/karmic.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 272 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 272         --.-K/s   in 0s      

2010-01-12 05:28:37 (17.9 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [272/272]

Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [914B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release [9,237B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 3,841B in 0s (4,037B/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 3,448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free medibuntu-keyring 2008.04.20 [3,448B]
Fetched 3,448B in 0s (6,458B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 150893 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up sun-java6-doc (6-15-1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

---

### Post by ceciliaFX on 2010-01-13
Just today my Update Manager gave me a notification to update and when I did up poped a window with the following:> W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783-en_US.bz2  Could not resolve 'repository.cairo-dock.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/intrepid/Release.gpg](http://repository.cairo-dock.org/ubuntu/dists/intrepid/Release.gpg)  Could not resolve 'repository.cairo-dock.org'

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/i18n/Translation](http://repository.cairo-dock.org/ubuntu/dists/intrepid/cairo-dock/i18n/Translation)I've never had an issue updating and I have done all updates since I installed Ubuntu

everything seems to be working alright on my system. 

is there some issue with the repositories?

---

### Post by michy99 on 2010-01-13
Yes, there is a problem with the cairo-dock repository. There is some information in this thread:

[http://ubuntuforums.org/showthread.php?t=1373828](http://ubuntuforums.org/showthread.php?t=1373828)

---

### Post by rnerwein on 2010-01-13
hi 
try as super user: fuser -u /var/lib/dpkg/lock
to see who is locking this file
ciao

---

