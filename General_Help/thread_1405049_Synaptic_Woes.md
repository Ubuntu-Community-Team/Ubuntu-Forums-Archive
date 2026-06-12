---
title: "Synaptic Woes"
date: 2010-02-12
forum: General Help
---

### Post by veefwoar on 2010-02-12
Hi all. I have just intalled Ubuntu 9.10 and i have been having some really strange issues while trying to install adobe flashplugin.

Firstly i tried using the Ubuntu Software centre but when i clicked on the flash installer option, it said my hardware architecture wasn't supported. I'm only using 32 bit and an older dual core so this is a bit strange.

Initially i couldn't connect to the internet at all but i found a forum entry that showed me how to disable ipv6 in grub, mozilla and the network connections manager. So now i have connection.

The disconnect seems to be in the way Ubuntu is accessing the repositories. I have tried the reload button in synaptic but it stalls on the first file and shows nothing under "Show indivdual file information" and then it times out later with a bunch of failed attempts logged in the window.

I have tried a working source.list file from a friend and that didn't help either. I'm not sure what info i need to provide so that you can help me so if you post I'll do my best.

Thanks.

---

### Post by fooman on 2010-02-12
try running the following command in a terminal (applications > accessories > terminal)....type or copy/paste:

```
sudo apt-get update
```enter your password when prompted (you will not see it so type carefully),  then press enter.  post the output back here.

---

### Post by veefwoar on 2010-02-12
Thanks mate but already tried that.

---

### Post by QIII on 2010-02-12
In System | Administration | Software Sources "Download from:", what server are you pointed to?
 
It may be that the server you have chosen is busy.

---

### Post by veefwoar on 2010-02-12
I was originally pointed at the Australian server, but I changed that to Main. Same problem. I got one error come back saying malformed package on a package that had i386 in the name. Sorry i dont have more detailed info right now as I'm not in front of the machine.

---

### Post by QIII on 2010-02-12
No problem.

When you get a chance, copy and paste what happens when you try to update in the terminal.

That might be illuminating.

---

### Post by fooman on 2010-02-13
> **veefwoar said:**
> Thanks mate but already tried that.

if you post the output here,  it may give us a clue as to the problem.

---

### Post by veefwoar on 2010-02-14
I have been told that the problem seems to be connecting to the DNS server. My web browser works fine, ping [www.google.com](www.google.com) works fine as well. When I try to connect to package sources (i.e apt-get update) the resulting line goes to 2% "Trying to connect to au.archive.ubuntu.com", sits there for about 3 mins then spits the following out:

```
Err http://mirror.files.bigpond.com jaunty Release.gpg                         
  Could not connect to mirror.files.bigpond.com:80 (1.0.0.0), connection timed out
Err http://mirror.files.bigpond.com jaunty/main Translation-en_AU              
  Unable to connect to mirror.files.bigpond.com http:
Err http://au.archive.ubuntu.com karmic Release.gpg                            
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://au.archive.ubuntu.com karmic/main Translation-en_AU                 
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic/restricted Translation-en_AU           
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic/universe Translation-en_AU             
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic/multiverse Translation-en_AU           
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-updates Release.gpg                    
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-updates/main Translation-en_AU         
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-updates/restricted Translation-en_AU   
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-updates/universe Translation-en_AU     
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-updates/multiverse Translation-en_AU   
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-security Release.gpg                   
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-security/main Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-security/restricted Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-security/universe Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err http://au.archive.ubuntu.com karmic-security/multiverse Translation-en_AU
  Unable to connect to au.archive.ubuntu.com http:
Err http://archive.canonical.com karmic Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err http://archive.canonical.com karmic/partner Translation-en_AU
  Unable to connect to archive.canonical.com http:
Reading package lists... Done                     
W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/Release.gpg  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_AU.bz2  Unable to connect to archive.canonical.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_AU.bz2  Unable to connect to au.archive.ubuntu.com http:

W: Failed to fetch http://mirror.files.bigpond.com/ubuntu/dists/jaunty/Release.gpg  Could not connect to mirror.files.bigpond.com:80 (1.0.0.0), connection timed out

W: Failed to fetch http://mirror.files.bigpond.com/ubuntu/dists/jaunty/main/i18n/Translation-en_AU.bz2  Unable to connect to mirror.files.bigpond.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by fooman on 2010-02-14
it appears you have some jaunty sources mixed in there....could that be the problem?

post the contents of /etc/apt/sources.list here and we can tell you which ones to delete.

---

### Post by veefwoar on 2010-02-14
Thanks for taking u the challenge fooman. Here's the contents of the list. I can see only one reference to Jaunty that isn't commented out (last line):

```
# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release Candidate amd64 (20090414.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://au.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ karmic universe
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic universe
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates universe
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://au.archive.ubuntu.com/ubuntu/ karmic multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://au.archive.ubuntu.com/ubuntu/ karmic-updates multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://au.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-security main restricted
deb http://au.archive.ubuntu.com/ubuntu/ karmic-security universe
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-security universe
deb http://au.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ karmic-security multiverse
deb http://mirror.files.bigpond.com/ubuntu/ jaunty main
```

---

### Post by fooman on 2010-02-14
open it as root with gedit and comment out that line...then try to update again.

```
gksudo gedit /etc/apt/sources.list
```then try:

```
sudo apt-get update
```post back again with any errors....hope it helps.

---

### Post by veefwoar on 2010-02-14
Turns out I had too many dns addresseses in my resolv.conf file. Originally there were none so i put in every one i could find for my ISP so there were something like 6 in there. I commented out all but the one and it appears to have worked. The update is working as i type this.

The reference I found was here:

[http://ka1fsb.home.att.net/resolve.html](http://ka1fsb.home.att.net/resolve.html)

I got lucky though as there is only one reference to the limit in a comment in one of his sample files.

Thanks for taking the time to help me out though guys, I really appreciate it!

---

### Post by symon1980 on 2010-02-24
im having the same trouble as you, its a fresh install of ubuntu 9.10 and my resolv.conf file is clean....I don't know what the problem is.....

i've tried everything you have tried with no success...

---

