---
title: "Failed update"
date: 2010-11-25
forum: General Help
---

### Post by person45 on 2010-11-25
I'm unable to update my Ubuntu install (10.04).
When I run sudo apt-get update I get

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.88.45 80]
Reading package lists... Done     

Any ideas on why this is happening? I've tried changing the server in software source.

---

### Post by Hippytaff on 2010-11-25
Can you post your sources list
```

cat /etc/apt/sources.list

```
:-)
 
also maybe try
```

sudo apt-get install -f

```
first

---

### Post by dino99 on 2010-11-25
Try to ping: 91.189.88.45 (have you some ip filtering/backlisting like iplist in use? )

into synaptic repo tab: deselect third parties if any

then:

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

### Post by person45 on 2010-11-25
From the source list

# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse


and running sudo apt-get install -f gets me:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Hippytaff on 2010-11-25
Your sources list looks fine, if just doing sudo apt-get install -f didn't work do this :-)
> **dino99 said:**
> into synaptic repo tab: deselect third parties if any
 
then:
 
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get install -f

---

### Post by person45 on 2010-11-25
I'm afraid that didn't work either:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Hippytaff on 2010-11-25
Just checking, are you using Lucid or did you upgrade to Maverick?

---

### Post by person45 on 2010-11-25
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

---

### Post by Hippytaff on 2010-11-25
Are you running through a proxy?

---

### Post by person45 on 2010-11-25
I am. However, in network proxy preferences I've set it to 'Direct internet connection'

---

### Post by Hippytaff on 2010-11-25
Try not going through the proxy, if it works then, then you know it's somethign to do with your proxy settings and you can investigate further :-)

---

### Post by dino99 on 2010-11-25
Try to ping: 91.189.88.45

[http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html#more-99](http://www.ubuntugeek.com/ubuntu-network-troubleshooting-tips.html#more-99)

---

### Post by tajiknomi on 2010-11-25
> **person45 said:**
> I'm afraid that didn't work either:

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-amd64/Packages.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  Unable to connect to archive.ubuntu.com:http: [IP: 91.189.92.171 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
[SIZE=2]Am not sure , but you can try this....
  
Go to software sources > Ubuntu-Software > Download-from>select the "**main**" and then try.. sudo apt-get update
[/SIZE]

---

### Post by person45 on 2010-11-25
Turned the proxy off, turned it back on, turned my machine off and on. Now it works. Strange. But thanks to everyone ):P

---

### Post by dino99 on 2010-11-25
good to know :) then set your thread to "SOLVED" using the tread tools on top

---

### Post by Hippytaff on 2010-11-25
> **person45 said:**
> Turned the proxy off, turned it back on, turned my machine off and on. Now it works. Strange. But thanks to everyone ):P
 
Excellent, thought it was a proxy thing, don't know how it worked either but it works and thats  all that matters :-)

---

