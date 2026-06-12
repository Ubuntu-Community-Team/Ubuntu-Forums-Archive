---
title: "adding medibuntu key"
date: 2011-03-20
forum: General Help
---

### Post by jon zendatta on 2011-03-20
Attempting to add the Medbuntu key, so I can install ubuntu-restricted-extras.
 ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

```
So after this command
```
sudo apt-get install ubuntu-restricted-extras
```
```
Err http://nz.archive.ubuntu.com/ubuntu/ maverick/universe libopenjpeg2 i386 1.3+dfsg-4
  403  Forbidden
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_i386.deb  403  Forbidden
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
Here is my source list
```
#deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nz.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nz.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick universe
deb http://nz.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nz.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://nz.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://nz.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://nz.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
deb http://packages.medibuntu.org/ maverick free non-free
```


So how to I apply the --fix command please?:KS

---

### Post by jon zendatta on 2011-03-20
And I tried adding the key this way
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
--2011-03-21 10:35:36--  http://www.medibuntu.org/sources.list.d/maverick.list
Resolving www.medibuntu.org... 1.0.0.0
Connecting to www.medibuntu.org|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--2011-03-21 10:35:42--  (try: 2)  http://www.medibuntu.org/sources.list.d/maverick.list
Connecting to www.medibuntu.org|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.

--2011-03-21 10:35:49--  (try: 3)  http://www.medibuntu.org/sources.list.d/maverick.list
Connecting to www.medibuntu.org|1.0.0.0|:80... connected.
HTTP request sent, awaiting response... Read error (Connection reset by peer) in headers.
Retrying.
```
No connection?

---

### Post by andrewthomas on 2011-03-20
Try changing your mirror. 

I just tried 
```
http://nz.archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_i386.deb
```403 Forbidden
```
http://archive.ubuntu.com/ubuntu/pool/universe/o/openjpeg/libopenjpeg2_1.3+dfsg-4_i386.deb
```good

Is this what you did for medibuntu?

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

---

