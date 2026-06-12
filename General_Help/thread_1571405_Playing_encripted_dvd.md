---
title: "Playing encripted dvd"
date: 2010-09-09
forum: General Help
---

### Post by Leshinsky on 2010-09-09
Following instructions on [http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html](http://www.ubuntugeek.com/playing-encrypted-dvds-in-ubuntu.html) i try the instructions and get this

matthew@ubuntu:~$ sudo apt-get install libdvdread3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdread3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdread3 has no installation candidate

---

### Post by dirty_harry on 2010-09-09
Well, I'm running Jaunty with libdvdread4 installed! works fine! ;)

maybe the site at ubuntugeek is out of date.

I find this userguide always useful:
[http://ubuntuguide.org/wiki/Ubuntu:Jaunty#CDs_and_DVDs](http://ubuntuguide.org/wiki/Ubuntu:Jaunty#CDs_and_DVDs)

---

### Post by Leshinsky on 2010-09-09
I wish mine would run fine.  Does anyone have a idea on how to get the computer to run dvds so i can watch them on my computer?  This is a feature i would like to have and i dont want to go back to windows.

---

### Post by gandaran on 2010-09-09
> **Leshinsky said:**
> I wish mine would run fine.  Does anyone have a idea on how to get the computer to run dvds so i can watch them on my computer?  This is a feature i would like to have and i dont want to go back to windows.
add the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository and install libdvdcss2

---

### Post by dirty_harry on 2010-09-09
Have you tried to install  libdvdread4 instead of "3"?

---

### Post by Leshinsky on 2010-09-09
I believe the version i was attempting to install was version 4.  

I just attempted to install Medibuntu as per a previous post to this topic and got this
matthew@ubuntu:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
[sudo] password for matthew: 
--2010-09-09 14:04:51--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-09-09 14:04:52 (43.5 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages [3,277B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages [8,241B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 18.6kB in 1s (13.7kB/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 41 not upgraded.
Need to get 3,448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Err [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free medibuntu-keyring 2008.04.20
  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb](http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?


That was cut and pasted from Terminal.  Can someone help with this?

Thanks.

---

### Post by gandaran on 2010-09-09
run the command again in terminal, (copy and paste to terminal) if you still get the same error again then open synaptic package manager and install the medibuntu keyring there then update the package list.

---

### Post by Leshinsky on 2010-09-09
I ran the command again in termainal using cut and paste to verify that it was the right one.  I got the same error message and when i try to use the software center to find the program it does not exist.

---

### Post by gandaran on 2010-09-09
> **Leshinsky said:**
> I ran the command again in termainal using cut and paste to verify that it was the right one.  I got the same error message and when i try to use the software center to find the program it does not exist.
not software center! use synaptic package manager, the medibuntu keyring package will be there, mark for install and click the apply button.

---

### Post by Leshinsky on 2010-09-09
Ok is the next step re running that command in terminal.  
If so i get this

matthew@ubuntu:~$ sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2010-09-09 14:29:23--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-09-09 14:29:24 (43.2 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Fetched 7,051B in 1s (6,247B/s)
Reading package lists...
Reading package lists...
Building dependency tree...
Reading state information...
medibuntu-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Fetched 7,051B in 1s (6,245B/s)
Reading package lists...
matthew@ubuntu:~$

---

### Post by gandaran on 2010-09-09
then all is okay now, just install libdvdcss2 and don't worry about installing libdvdread, installing libdvdcss2 pulls all the dependencies needed including libdvdread.
you mite need to the install the w32codecs packages too.

---

### Post by Leshinsky on 2010-09-09
This does not make sense.  

I reinstall the thingie like you said.  I fun both lines and it still is searching for a plug in.  is this not everything i needed to do?  

here is the cut and paste from terminal.

matthew@ubuntu:~$  sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
matthew@ubuntu:~$  sudo /usr/share/doc/libdvdread4/install-css.sh
--2010-09-09 14:38:11--  [http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8080 (7.9K) [application/octet-stream]
Saving to: `/tmp/dvdcss-yvPbhy/Packages'

100%[======================================>] 8,080       51.4K/s   in 0.2s    

2010-09-09 14:38:12 (51.4 KB/s) - `/tmp/dvdcss-yvPbhy/Packages' saved [8080/8080]

--2010-09-09 14:38:12--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-yvPbhy/libdvdcss.deb'

100%[======================================>] 38,080      79.3K/s   in 0.5s    

2010-09-09 14:38:13 (79.3 KB/s) - `/tmp/dvdcss-yvPbhy/libdvdcss.deb' saved [38080/38080]

(Reading database ... 145306 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-yvPbhy/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
matthew@ubuntu:~$

---

### Post by gandaran on 2010-09-09
> **Leshinsky said:**
> This does not make sense.  

I reinstall the thingie like you said.  I fun both lines and it still is searching for a plug in.  is this not everything i needed to do?  

here is the cut and paste from terminal.

matthew@ubuntu:~$  sudo apt-get install libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdvdread4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 41 not upgraded.
matthew@ubuntu:~$  sudo /usr/share/doc/libdvdread4/install-css.sh
--2010-09-09 14:38:11--  [http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/lucid/free/binary-amd64/Packages)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8080 (7.9K) [application/octet-stream]
Saving to: `/tmp/dvdcss-yvPbhy/Packages'

100%[======================================>] 8,080       51.4K/s   in 0.2s    

2010-09-09 14:38:12 (51.4 KB/s) - `/tmp/dvdcss-yvPbhy/Packages' saved [8080/8080]

--2010-09-09 14:38:12--  [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.10-0.3medibuntu1_amd64.deb)
Resolving packages.medibuntu.org... 88.191.82.11
Connecting to packages.medibuntu.org|88.191.82.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 38080 (37K) [application/octet-stream]
Saving to: `/tmp/dvdcss-yvPbhy/libdvdcss.deb'

100%[======================================>] 38,080      79.3K/s   in 0.5s    

2010-09-09 14:38:13 (79.3 KB/s) - `/tmp/dvdcss-yvPbhy/libdvdcss.deb' saved [38080/38080]

(Reading database ... 145306 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.10-0.3medibuntu1 (using .../dvdcss-yvPbhy/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.10-0.3medibuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
matthew@ubuntu:~$
well the libdvdcss and libdvdread are installed! have you tried playing the dvd now? what player are you using?

---

### Post by Leshinsky on 2010-09-09
I have VLC which wont even open up, and the generic "movie player" and xine.  VLC wont even open up when i try and movie player and xine are trying to find plug ins that just are not there.

---

### Post by gandaran on 2010-09-09
> **Leshinsky said:**
> I have VLC which wont even open up, and the generic "movie player" and xine.  VLC wont even open up when i try and movie player and xine are trying to find plug ins that just are not there.
have you installed codecs? for the movie player install the ubuntu-restricted-extras package, and try mplayer, for mplayer you need to install the w32codecs.

---

### Post by Leshinsky on 2010-09-09
How do i do that.  I am new to this version of Ubuntu.  I had 9.04 over a year ago so im kindof lost now.

---

### Post by gandaran on 2010-09-09
> **Leshinsky said:**
> How do i do that.  I am new to this version of Ubuntu.  I had 9.04 over a year ago so im kindof lost now.
```
sudo apt-get install ubuntu-restricted-extras
```
or look up the package in software center or synaptic package manager

---

### Post by Leshinsky on 2010-09-09
I get this error message.

matthew@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apport-hooks-medibuntu ca-certificates-java cabextract freepats
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea6-plugin java-common libaccess-bridge-java
  libaccess-bridge-java-jni libavcodec-extra-52 libavutil-extra-49 libcdaudio1
  libcelt0-0 libdirac-encoder0 libfaac0 libfftw3-3 libflite1 libgme0
  libiptcdata0 libkate1 libmms0 libmp4v2-0 libofa0 libopenjpeg2 liborc-0.4-0
  libsoundtouch1c2 libwildmidi0 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib ttf-mscorefonts-installer tzdata tzdata-java unrar
Suggested packages:
  default-jre equivs libfaad0 libfftw3-dev sun-java6-fonts ttf-sazanami-gothic
  ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho ttf-telugu-fonts
  ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following packages will be REMOVED:
  libavcodec52 libavutil49
The following NEW packages will be installed:
  apport-hooks-medibuntu ca-certificates-java cabextract freepats
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea6-plugin java-common libaccess-bridge-java
  libaccess-bridge-java-jni libavcodec-extra-52 libavutil-extra-49 libcdaudio1
  libcelt0-0 libdirac-encoder0 libfaac0 libfftw3-3 libflite1 libgme0
  libiptcdata0 libkate1 libmms0 libmp4v2-0 libofa0 libopenjpeg2 liborc-0.4-0
  libsoundtouch1c2 libwildmidi0 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib ttf-mscorefonts-installer tzdata-java
  ubuntu-restricted-extras unrar
The following packages will be upgraded:
  tzdata
1 upgraded, 38 newly installed, 2 to remove and 40 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
matthew@ubuntu:~$

---

### Post by Leshinsky on 2010-09-09
is anyone have a idea how to get past this error message 
matthew@ubuntu:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apport-hooks-medibuntu ca-certificates-java cabextract freepats
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea6-plugin java-common libaccess-bridge-java
  libaccess-bridge-java-jni libavcodec-extra-52 libavutil-extra-49 libcdaudio1
  libcelt0-0 libdirac-encoder0 libfaac0 libfftw3-3 libflite1 libgme0
  libiptcdata0 libkate1 libmms0 libmp4v2-0 libofa0 libopenjpeg2 liborc-0.4-0
  libsoundtouch1c2 libwildmidi0 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib ttf-mscorefonts-installer tzdata tzdata-java unrar
Suggested packages:
  default-jre equivs libfaad0 libfftw3-dev sun-java6-fonts ttf-sazanami-gothic
  ttf-kochi-gothic ttf-sazanami-mincho ttf-kochi-mincho ttf-telugu-fonts
  ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
The following packages will be REMOVED:
  libavcodec52 libavutil49
The following NEW packages will be installed:
  apport-hooks-medibuntu ca-certificates-java cabextract freepats
  gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly-multiverse
  icedtea-6-jre-cacao icedtea6-plugin java-common libaccess-bridge-java
  libaccess-bridge-java-jni libavcodec-extra-52 libavutil-extra-49 libcdaudio1
  libcelt0-0 libdirac-encoder0 libfaac0 libfftw3-3 libflite1 libgme0
  libiptcdata0 libkate1 libmms0 libmp4v2-0 libofa0 libopenjpeg2 liborc-0.4-0
  libsoundtouch1c2 libwildmidi0 openjdk-6-jre openjdk-6-jre-headless
  openjdk-6-jre-lib ttf-mscorefonts-installer tzdata-java
  ubuntu-restricted-extras unrar
The following packages will be upgraded:
  tzdata
1 upgraded, 38 newly installed, 2 to remove and 40 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
matthew@ubuntu:~$

---

### Post by Leshinsky on 2010-09-09
Does anyone have any ideas why i am having such a problem getting where i can watch dvds on my computer.  Noone seems to have a solution to this problem.

---

### Post by dirty_harry on 2010-09-09
did you try to restart your system, installed the updates etc?

and I have to admit that I'm not sure what causes your problem.but with a little help, some reading and the very famous trial'n'error method I always got (almost) everything working. ;)

---

### Post by Leshinsky on 2010-09-09
well i am trying to trail and error part.  i am using another page [https://help.ubuntu.com/7.04/musicvideophotos/C/video.html](https://help.ubuntu.com/7.04/musicvideophotos/C/video.html) and i can redo a few of them in synaptic package manager but their not all there.  and the ones that are are getting stuck on the down load and somehow my computer is not getting the information it needs.

---

### Post by FinalShot on 2010-09-09
Learn to help yourself. **[Do Not Click This]("http://www.google.com/search?client=ubuntu&channel=fs&q=E%3A+Could+not+get+lock+%2Fvar%2Fcache%2Fapt%2Farchives%2Flock+-+open+%2811%3A+Resource+temporarily+unavailable%29&ie=utf-8&oe=utf-8")**.

---

