---
title: "Strange apt-get behaviour"
date: 2009-07-06
forum: General Help
---

### Post by Cheesemill on 2009-07-06
Edit - Posted in wrong section. Can a mod move this to General Help please.

Hi guys, I'm having a bit of a problem with using aptitude on a new install of Jaunty 64-bit.

Whenever I try a 'sudo aptitude update' I get the following errors.
```
Err http://gb.archive.ubuntu.com jaunty Release.gpg
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty/main Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty/restricted Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty/universe Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty/multiverse Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-updates Release.gpg
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-updates/main Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-updates/restricted Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-updates/universe Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-updates/multiverse Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-backports Release.gpg
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-backports/main Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-backports/restricted Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-backports/universe Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://gb.archive.ubuntu.com jaunty-backports/multiverse Translation-en_GB
  Could not resolve &#8216;http&#8217;
0% [Connecting to http]
Err http://security.ubuntu.com jaunty-security Release.gpg
  Could not resolve &#8216;http&#8217;
Err http://security.ubuntu.com jaunty-security/main Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://security.ubuntu.com jaunty-security/restricted Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://security.ubuntu.com jaunty-security/universe Translation-en_GB
  Could not resolve &#8216;http&#8217;
Err http://security.ubuntu.com jaunty-security/multiverse Translation-en_GB
  Could not resolve &#8216;http&#8217;
Reading package lists... Done
```I know what you're thinking, it's probably an error with my sources.list, however, updating works fine through Synaptic. Any suggestions?

Here's my sources.list
```
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty main restricted

deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe
deb http://security.ubuntu.com/ubuntu jaunty-security multiverse
deb-src http://security.ubuntu.com/ubuntu jaunty-security multiverse
```

---

### Post by tripolitan on 2009-07-06
Does apt-get update work? if so, using synaptic, check aptitude's dependencies, if all checks out, completely remove aptitude then re-install using apt-get install aptitude. If not, file a bug report, your version is still in "testing" phase.

---

### Post by Cheesemill on 2009-07-06
I'm actually running Jaunty, this is my work machine (I only run Karmic at home).

apt-get update isn't working at all (neither is apt-get install) but both Synaptic and Add/Remove programs are OK.

---

### Post by wojox on 2009-07-06
It looks like a problem with their server. Not you. :p

---

### Post by Cheesemill on 2009-07-06
> **wojox said:**
> It looks like a problem with their server. Not you. :p
It's not a server problem, I can be using wget on the sources in one terminal with apt-get failing in another simultaneously, also Synaptic works fine with the same sources.

---

### Post by tripolitan on 2009-07-07
Apt is working, you won't be able to run Synaptic without apt (synaptic is a GTK front end for apt). I don't know about aptitude but apt will not run while synaptic is running, only one package manager at a time

---

