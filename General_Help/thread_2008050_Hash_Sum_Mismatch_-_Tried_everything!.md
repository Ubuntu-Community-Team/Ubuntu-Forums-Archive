---
title: "Hash Sum Mismatch - Tried everything!"
date: 2012-06-21
forum: General Help
---

### Post by ChinaJustin on 2012-06-21
Running Lubuntu 12.04 on an old desktop here at the university in China I teach at.

Everything was working fine till about three days ago, when I started getting the following error while trying to update:

```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Being a noob, but still understanding looking before asking, I searched Google for an answer.

I have tried the following, none of which have worked:

```
sudo rm -rf /var/lib/apt/lists/*
```

```
sudo rm -rf /var/lib/apt/lists/partial/*
```

```
sudo apt-get clean
sudo apt-get update
```

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

```
sudo apt-get update -o Acquire::BrokenProxy=true
```

```
sudo rm -vf /var/lib/apt/lists/*
```

I tried manually changing my mirror to an ftp site rather than an http site based on [http://ubuntuforums.org/showthread.php?t=1959704](http://ubuntuforums.org/showthread.php?t=1959704), but again, the same two repositories won't download.

And here is what I get from the sources.list file:
```
# 

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423.1)]/ precise main multiverse restricted universe

# deb cdrom:[Lubuntu 12.04 _Precise Pangolin_ - Release i386 (20120423.1)]/ precise main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb ftp://kr.archive.ubuntu.com/ubuntu/ precise universe main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb ftp://kr.archive.ubuntu.com/ubuntu/ precise-updates universe main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb ftp://kr.archive.ubuntu.com/ubuntu/ precise-security universe main restricted multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
# deb-src http://extras.ubuntu.com/ubuntu precise main
```

Going directly to [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) in Chrome works fine; I can browse anything and everything. When I uncheck the two repositories in Update Manager, everything works fine.

I'm having this same problem with Linux Mint 13 on my laptop in my apartment. The only solution that's worked for me there has been using my VPN.

And another thing: while I don't have a proxy set up on my computer (and I use OpenDNS's DNS servers), it appears that there is a server side proxy through China Unicom (or at least I think there is). Sometimes when I try going to a web page, I get an IP address along the lines of 221.179.92.2/proxy?e= followed by a bunch of letters and numbers (note that the address there isn't the EXACT address, but I looked the IP up last night and it was for the ISP the university here uses). The only way to get to the web page, then, is to either go back to the previous page (if it was a link) or type the address in again.

Help?

---

### Post by ChinaJustin on 2012-06-24
*bump*

Still having the problem... was hoping a few days time would fix it, but no joy.

---

### Post by ChinaJustin on 2012-06-27
*bump again*

SOMEbody has to have an idea on this.

---

### Post by jmfal on 2012-06-27
Open up  the"Udate Manager" press the settings button >> click on the other sources tab and uncheck the  "CD" at the top and try 
 
```
  sudo apt-get update  
```


and 
```
 sudo apt-get upgrade  
```

---

### Post by ChinaJustin on 2012-06-27
@jmfal - Yeah, the two CD options were already unchecked, so not an option. Thanks, though.

I **did** uninstall the Oracle Java 7 updater from Webupd8, so I could at least get rid of that repository... but still getting the hash sum mismatch with the extras.ubuntu.com one.

---

### Post by ekot on 2012-07-02
I have the same issue, this happens to me when I try to install additional driver for my graphics card. I also tried Linux Mint and it has the same problem

---

### Post by ChinaJustin on 2012-07-02
Weird. And you're in Russia. My biggest question is why is it a different server from one Linux distribution to another? Lubuntu had the problem with extras.ubuntu.com, Mint is having it with archive.ubuntu.com... I've tried looking on the Chinese Ubuntu forums, but the only suggestion there is to change mirrors. Not very helpful.

---

### Post by ekot on 2012-07-28
In my case problem seems to be in router, when I connected internet directly it works fine.

---

### Post by atenz on 2012-07-28
@ ChinaJustin - You should try changing your mirrors by selecting the fastest or or by selecting the Main Server. 

Then try 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ChinaJustin on 2012-08-26
@atenz - Sorry for the late reply. Summer vacation, been working and traveling.

But yeah, done that, too. I'm currently on a server in America via the "fastest" mirror option while connected through my VPN. When I disconnect my VPN, I still get the error message. Tried a few different mirrors around the world, no luck.

---

