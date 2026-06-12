---
title: "apt not working"
date: 2010-06-09
forum: General Help
---

### Post by wednesday allfather on 2010-06-09
My updates and synaptic have not been working for a while.  I can manually download packages and install them, so dpkg seems to be working.  Here is my /etc/apt/sources.list is

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://mirror.anl.gov/pub/ubuntu/ lucid main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid universe
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid multiverse
deb http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.anl.gov/pub/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://mirror.anl.gov/pub/ubuntu/ lucid-security main restricted
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security main restricted
deb http://mirror.anl.gov/pub/ubuntu/ lucid-security universe
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security universe
deb http://mirror.anl.gov/pub/ubuntu/ lucid-security multiverse
deb-src http://mirror.anl.gov/pub/ubuntu/ lucid-security multiverse
deb http://packages.dfreer.org gutsy main
```

I'll be happy to provide any additional info.  

Thanks for the help and the great community :)

---

### Post by arrange on 2010-06-09
Can you explain in a little more detail what you mean by "updates and synaptic have not been working"? Do you see an error message etc?

Why do you think that *apt* is to blame? Can you for example run ```
sudo apt-get update
```without problems?

---

### Post by plucky on 2010-06-09
And remove ```
deb http://packages.dfreer.org gutsy main
``` from your sources.list

Good luck

---

### Post by wednesday allfather on 2010-06-09
Sorry, I forgot to include this

when running sudo apt-get update here is a snippet of what I get.

```
Err http://mirror.anl.gov/pub/ubuntu/ lucid-backports/restricted Translation-en_US
  Connection failed
Err http://mirror.anl.gov/pub/ubuntu/ lucid-backports/universe Translation-en_US
  Connection failed
Err http://mirror.anl.gov/pub/ubuntu/ lucid-backports/multiverse Translation-en_US
  Connection failed
Err http://mirror.anl.gov lucid-security Release.gpg
  Connection failed
Err http://mirror.anl.gov/pub/ubuntu/ lucid-security/main Translation-en_US
  Connection failed
Err http://mirror.anl.gov/pub/ubuntu/ lucid-security/restricted Translation-en_US
  Connection failed
Err http://mirror.anl.gov/pub/ubuntu/ lucid-security/universe Translation-en_US
  Connection failed
Err http://mirror.anl.gov/pub/ubuntu/ lucid-security/multiverse Translation-en_US
  Connection failed
Ign http://mirror.anl.gov lucid Release
Ign http://mirror.anl.gov lucid-updates Release
Ign http://mirror.anl.gov lucid-backports Release
Ign http://mirror.anl.gov lucid-security Release
Ign http://mirror.anl.gov lucid/main Packages
Ign http://mirror.anl.gov lucid/restricted Packages
Ign http://mirror.anl.gov lucid/main Sources
Ign http://mirror.anl.gov lucid/restricted Sources
Ign http://mirror.anl.gov lucid/universe Packages
Ign http://mirror.anl.gov lucid/universe Sources
Ign http://mirror.anl.gov lucid/multiverse Packages
Ign http://mirror.anl.gov lucid/multiverse Sources
Ign http://mirror.anl.gov lucid-updates/main Packages
Ign http://mirror.anl.gov lucid-updates/restricted Packages
Ign http://mirror.anl.gov lucid-updates/main Sources
Ign http://mirror.anl.gov lucid-updates/restricted Sources
Ign http://mirror.anl.gov lucid-updates/universe Packages
Ign http://mirror.anl.gov lucid-updates/universe Sources
Ign http://mirror.anl.gov lucid-updates/multiverse Packages
Ign http://mirror.anl.gov lucid-updates/multiverse Sources
Ign http://mirror.anl.gov lucid-backports/main Packages
Ign http://mirror.anl.gov lucid-backports/restricted Packages
Ign http://mirror.anl.gov lucid-backports/universe Packages
Ign http://mirror.anl.gov lucid-backports/multiverse Packages
Ign http://mirror.anl.gov lucid-backports/main Sources
Ign http://mirror.anl.gov lucid-backports/restricted Sources
Ign http://mirror.anl.gov lucid-backports/universe Sources
Ign http://mirror.anl.gov lucid-backports/multiverse Sources
Ign http://mirror.anl.gov lucid-security/main Packages
Ign http://mirror.anl.gov lucid-security/restricted Packages
Ign http://mirror.anl.gov lucid-security/main Sources
Ign http://mirror.anl.gov lucid-security/restricted Sources
Ign http://mirror.anl.gov lucid-security/universe Packages
Ign http://mirror.anl.gov lucid-security/universe Sources
Ign http://mirror.anl.gov lucid-security/multiverse Packages
Ign http://mirror.anl.gov lucid-security/multiverse Sources
Ign http://mirror.anl.gov lucid/main Packages
Ign http://mirror.anl.gov lucid/restricted Packages
Ign http://mirror.anl.gov lucid/main Sources
Ign http://mirror.anl.gov lucid/restricted Sources
Ign http://mirror.anl.gov lucid/universe Packages
Ign http://mirror.anl.gov lucid/universe Sources
Ign http://mirror.anl.gov lucid/multiverse Packages
Ign http://mirror.anl.gov lucid/multiverse Sources
Ign http://mirror.anl.gov lucid-updates/main Packages
Ign http://mirror.anl.gov lucid-updates/restricted Packages
Ign http://mirror.anl.gov lucid-updates/main Sources
Ign http://mirror.anl.gov lucid-updates/restricted Sources
Ign http://mirror.anl.gov lucid-updates/universe Packages
Ign http://mirror.anl.gov lucid-updates/universe Sources
Ign http://mirror.anl.gov lucid-updates/multiverse Packages
Ign http://mirror.anl.gov lucid-updates/multiverse Sources
Ign http://mirror.anl.gov lucid-backports/main Packages
Ign http://mirror.anl.gov lucid-backports/restricted Packages
Ign http://mirror.anl.gov lucid-backports/universe Packages
Ign http://mirror.anl.gov lucid-backports/multiverse Packages
Ign http://mirror.anl.gov lucid-backports/main Sources
Ign http://mirror.anl.gov lucid-backports/restricted Sources
Ign http://mirror.anl.gov lucid-backports/universe Sources
Ign http://mirror.anl.gov lucid-backports/multiverse Sources
Ign http://mirror.anl.gov lucid-security/main Packages
Ign http://mirror.anl.gov lucid-security/restricted Packages
Ign http://mirror.anl.gov lucid-security/main Sources
Ign http://mirror.anl.gov lucid-security/restricted Sources
Ign http://mirror.anl.gov lucid-security/universe Packages
Ign http://mirror.anl.gov lucid-security/universe Sources
Ign http://mirror.anl.gov lucid-security/multiverse Packages
Ign http://mirror.anl.gov lucid-security/multiverse Sources
Err http://mirror.anl.gov lucid/main Packages
  Connection failed
Err http://mirror.anl.gov lucid/restricted Packages
  Connection failed
Err http://mirror.anl.gov lucid/main Sources
  Connection failed
Err http://mirror.anl.gov lucid/restricted Sources
  Connection failed
Err http://mirror.anl.gov lucid/universe Packages
  Connection failed
Err http://mirror.anl.gov lucid/universe Sources
  Connection failed
Err http://mirror.anl.gov lucid/multiverse Packages
  Connection failed
Err http://mirror.anl.gov lucid/multiverse Sources
  Connection failed
Err http://mirror.anl.gov lucid-updates/main Packages
  Connection failed
Err http://mirror.anl.gov lucid-updates/restricted Packages
  Connection failed
Err http://mirror.anl.gov lucid-updates/main Sources
  Connection failed
Err http://mirror.anl.gov lucid-updates/restricted Sources
  Connection failed
Err http://mirror.anl.gov lucid-updates/universe Packages
  Connection failed
Err http://mirror.anl.gov lucid-updates/universe Sources
  Connection failed
Err http://mirror.anl.gov lucid-updates/multiverse Packages
  Connection failed
Err http://mirror.anl.gov lucid-updates/multiverse Sources
  Connection failed
Err http://mirror.anl.gov lucid-backports/main Packages
  Connection failed
Err http://mirror.anl.gov lucid-backports/restricted Packages
  Connection failed
Err http://mirror.anl.gov lucid-backports/universe Packages
  Connection failed
Err http://mirror.anl.gov lucid-backports/multiverse Packages
  Connection failed
Err http://mirror.anl.gov lucid-backports/main Sources
  Connection failed
Err http://mirror.anl.gov lucid-backports/restricted Sources
  Connection failed
Err http://mirror.anl.gov lucid-backports/universe Sources
  Connection failed
Err http://mirror.anl.gov lucid-backports/multiverse Sources
  Connection failed
Err http://mirror.anl.gov lucid-security/main Packages

```

And I forgot I added that gutsy deb also.  Duh :) not really sure what I was thinking there.

It seems like I cannot find the servers for some reason, but I do, in fact, have a working internet connection.

---

### Post by arrange on 2010-06-09
Have you tried choosing a different mirror in *Software sources*?

---

### Post by wednesday allfather on 2010-06-09
Yes, I have.  I tried several mirrors and also 'Select Best Server' or from administration -> software sources

---

### Post by wednesday allfather on 2010-06-10
I've seen this kind of post a couple places and it doesn't seem to get solved.  My dear ubuntu-linux geeks... i_need_your_help :)

---

### Post by emarkay on 2010-06-10
Strange - What happens when you do "System - Update Manager" (the GUI) and enter your password - do you get any error messages?

---

### Post by wednesday allfather on 2010-06-11
Not at that stage.  The only errors I get are from requesting package data (updates) or trying to install packages from the repos.

---

### Post by oaxacamatt1 on 2010-06-11
Hi Wednesdcay and all,
I have actually experienced this same problem and was going to write about it soon (after I gathered my info), but I have seen the same on two systems.
Very disturbing!!
M

---

### Post by wednesday allfather on 2010-06-14
Greetings all.

I am updating now as I type this reply.  Everything seems fine.  I was using a SOCKS5 proxy (just thought i'd try it out) which seems to have been the cause for my requests for files being ignored.  Anyway, here is my fix.  

```
sudo nano /etc/apt/apt.conf
```

If you see

```
Acquire::http::proxy "http://125.64.96.21:1080/";
```

or any IP, you can just remove the lines and leave an empty file behind.  

A free proxy listed on the web is most certainly going to be used to do bad stuff.  This one was flagged on stopforumspam.com or something like that.  

Anyway, I hope this helps and thank you all very much for the replies.

---

