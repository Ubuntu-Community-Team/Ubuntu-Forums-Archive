---
title: "E: Malformed Line 56 in source list"
date: 2010-07-26
forum: General Help
---

### Post by ToxicDoom420 on 2010-07-26
So, i screwed up lol. Go figure. I was back in the synaptic manager, trying to install an ALSA driver. Cause, i came across the repository link one day on google..and, had no problems with it - so, i lost the link to re-add to the repository...and, in the process, i thought i found it. Guess not. This is what i get now...when i tried to mark a few updates.

E: Malformed line 56 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

With me being new to Linux - i haven't really used it since 8.04 - and, even then...i barely used it. So, with it being my main system now....i'm pretty much learning as i go :)

So...the question is....how in the...heck....do i fix the problem i created? lol.

Thanks guys!

---

### Post by dcstar on 2010-07-26
> **ToxicDoom420 said:**
> So, i screwed up lol. Go figure. I was back in the synaptic manager, trying to install an ALSA driver. Cause, i came across the repository link one day on google..and, had no problems with it - so, i lost the link to re-add to the repository...and, in the process, i thought i found it. Guess not. This is what i get now...when i tried to mark a few updates.

E: Malformed line 56 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

With me being new to Linux - i haven't really used it since 8.04 - and, even then...i barely used it. So, with it being my main system now....i'm pretty much learning as i go :)

So...the question is....how in the...heck....do i fix the problem i created? lol.

```
gksudo gedit /etc/apt/sources.list
```

Find line 56 and comment it out or fix it so it looks like the other that still work.

---

### Post by ToxicDoom420 on 2010-07-26
thank you SOOOO Much DCStar! i dunno what i woulda did without that - now i know! xD That's the only thing about linux that confuses me....the command prompt. I mean, if i was using DOS back in the day, maybe i'd be used to it. 

What i did was just remove that line, so that there's 55 lines. Hopefully i come across that thread or something from ubuntu i had the day before i decided to wipe the windows off, and go full blown 10.04 :D

Thanks again for the help! :D

---

### Post by anotherusernametoforget on 2011-09-13
I followed the same advice, but now it's crying about line 57.

---

### Post by oldos2er on 2011-09-13
Could you please run **cat /etc/apt/sources.list** in a terminal and post the output here?

---

### Post by anotherusernametoforget on 2011-09-13
assquack@ubuntu:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release amd64 (20110427.1)]/ natty main restricted
deb-src [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty main restricted #Added by software-properties

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty main restricted
deb-src [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-updates main restricted
deb-src [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty universe
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty multiverse
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-security main restricted
deb-src [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-security restricted main multiverse universe #Added by software-properties
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-security universe
deb [http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
# deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
# deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by oldos2er on 2011-09-13
No obvious errors are jumping out at me. If you want to you can delete the last two lines referencing lucid.

If you're still having problems can you post the complete output of **sudo apt-get update** ?

---

### Post by anotherusernametoforget on 2011-09-13
root@ubuntu:/home/assquack# sudo apt-get update
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty InRelease
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates InRelease
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security InRelease
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty Release.gpg
Get:1 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates Release.gpg [198 B]
Get:2 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security Release.gpg [198 B]
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty Release
Get:3 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates Release [31.4 kB]
Get:4 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security Release [31.4 kB]
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/main Sources       
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/restricted Sources
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/multiverse Sources
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/universe Sources
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/main amd64 Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/restricted amd64 Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/universe amd64 Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/multiverse amd64 Packages
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/main TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/multiverse TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/restricted TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/universe TranslationIndex
Get:5 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/restricted Sources [14 B]
Get:6 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/main Sources [105 kB]
Get:7 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/multiverse Sources [1,890 B]
Get:8 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/universe Sources [25.2 kB]
Get:9 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/main amd64 Packages [316 kB]
Get:10 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/restricted amd64 Packages [14 B]
Get:11 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/universe amd64 Packages [91.0 kB]
Get:12 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/multiverse amd64 Packages [4,170 B]
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/main TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/multiverse TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/restricted TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/universe TranslationIndex
Get:13 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/restricted Sources [14 B]
Get:14 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/main Sources [67.0 kB]
Get:15 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/multiverse Sources [650 B]
Get:16 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/universe Sources [10.6 kB]
Get:17 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/main amd64 Packages [176 kB]
Get:18 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/restricted amd64 Packages [14 B]
Get:19 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/universe amd64 Packages [36.2 kB]
Get:20 [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/multiverse amd64 Packages [1,936 B]
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/main TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/multiverse TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/restricted TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/universe TranslationIndex
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/main Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/multiverse Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/multiverse Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/restricted Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/universe Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty/universe Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/main Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/multiverse Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/multiverse Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/restricted Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/universe Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-updates/universe Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/main Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/multiverse Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/multiverse Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/restricted Translation-en
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/universe Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) natty-security/universe Translation-en
Fetched 899 kB in 2s (378 kB/s)
Reading package lists... Done

---

### Post by oldos2er on 2011-09-14
All fixed?

---

