---
title: "how install extra programs with adept?"
date: 2006-03-13
forum: General Help
---

### Post by mistamcgoo on 2006-03-13
Ive just installed kubuntu 5.10 on my laptop after my Xp gave up (again) I've been using ubuntu for a while on my desktop (with kde installed afterwards) so i'm used to installing software with synaptic or apt. I started up adept because i want to install extra programs like firefox, evolution mail, gaim, kedit, dutch language packs for openoffice,mplayer, vlc,  ... But i cannot find these in adept. with synaptic, i just enabled the extra repositories, and i got all the software i can install from internet. but i don't see any of these programs in the adept list. i checked the repositories and the seem to be all uncommented. btw, when i try apt or sudo apt in console, i get command not found? My wireless connection is set up completely, so i have fast internet access. Is there something i am doing wrong here? I searched on the forum, but no success. sorry if this is a dumb question.

---

### Post by aysiu on 2006-03-13
Can you go to KMenu > System > Konsole and type these commands and copy and paste their output to this thread? ```
cat /etc/apt/sources.list
sudo apt-get update
```

---

### Post by mistamcgoo on 2006-03-13
## Uncomment the following two lines to fetch updated software from the network
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted universe
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy main restricted universe

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

stijn@aspire:~$ sudo apt-get update
Password:
Reading package lists... Done

when i just do sudo apt 
sudo: apt: command not found

---

### Post by aysiu on 2006-03-13
*apt* is not a command.

You have to use *apt-get* or *aptitude*.
You can also use graphical versions of *apt-get* like Synaptic Package Manager or Adept.

Your sources.list is empty.

The # sign basically means "ignore the rest of this line--it doesn't exit."

Go here to get an updated list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by mistamcgoo on 2006-03-13
ah i think i get it now. 
first, i looked at the repositories list in directly in the adept menu ('manage repositories' in the menu in the top ). the single # doesn't show there, 
only the double ##. 
I edited the repo's list with kwrite and the list with programs is a lot bigger now. Feel pretty dumb not having found this myself, thanks very much for the help.

---

