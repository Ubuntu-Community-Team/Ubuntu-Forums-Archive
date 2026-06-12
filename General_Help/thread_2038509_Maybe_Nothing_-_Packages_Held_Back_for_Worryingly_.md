---
title: "Maybe Nothing - Packages Held Back for Worryingly Long Time"
date: 2012-08-06
forum: General Help
---

### Post by Dylan1473 on 2012-08-06
[SIZE=4]EDIT: Disregard, I just went ahead with it anyway. It doesn't seem to have hurt anything. Or helped much of anything for that matter, but at least now I'm fully up to date.[/SIZE]

So, I've noticed that for the past week or two a bunch of packages have been consistently held back and I'm not sure why. Here's the list:

```

The following packages have been kept back:
  hplip hplip-data libhpmud0 libsane-hpaio printer-driver-hpcups
  printer-driver-hpijs wine1.5 wine1.5-amd64 wine1.5-i386:i386

```and here's my sources.list file, though it's worked fine for me for quite some time:

```

#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse

###### Ubuntu Update Repos
deb http://archive.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu precise partner

###### Ubuntu Extras Repo
## deb http://extras.ubuntu.com/ubuntu precise main

##############################################################
##################### UNOFFICIAL  REPOS ######################
##############################################################

###### 3rd Party Binary Repos

#### Wine - https://launchpad.net/~ubuntu-wine/+archive/ppa/
## Run this command:  sudo apt-key adv --keyserver ##keyserver.ubuntu.com --recv-keys F9CB8DB0
##deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu precise main

```I've never had packages held back more than two days that I've noticed, and I *would* like that WINE update for sure, so I'm a bit worried. I'm considering the following options:

1) Forcing the updates with dist-upgrade

I have heard in some places that this is totally safe and in others that it is risky. I had a botched distribution upgrade with Debian in the past that effectively destroyed my operating system, but circumstances were different and I knew full well what I was doing was dangerous then. I don't think that'd happen now (and honestly have used dist-upgrade before) but am a little wary for that reason.

2) Uninstalling WINE and reinstalling it, perhaps directly from the WINE ppa

Even if this worked there'd still be other packages hanging around behind, and I don't really want to reinstall WINE just to update it.

Thoughts?

EDIT: I'd note that when attempting a dist-upgrade I don't see anything particularly worrying in the package changes:

```
The following NEW packages will be installed:
  printer-driver-postscript-hp wine-gecko1.7 wine-gecko1.7:i386 wine-mono0.0.4
The following packages will be upgraded:
  hplip hplip-data libecore1 libelementary libelementary-data libevas1
  libhpmud0 libsane-hpaio printer-driver-hpcups printer-driver-hpijs wine1.5
  wine1.5-amd64 wine1.5-i386:i386

```

---

### Post by bertd2 on 2012-10-16
For posterity's sake (I got here because of a Google search for held back packages): if you want to install just one of the held back packages, just use

```
apt-get install wine
```

It will effectively update just wine, and install its new dependancies (the most likely reason it got held in the first place). If this update requires updating any other held packages, it'll tell you. Selective [FONT="Lucida Console"]apt-get install[/FONT] is the "safe" way to postpone, say, a kernel update, without that update disappearing from your radar altogether.

Invoking [FONT="Lucida Console"]apt-get dist-upgrade[/FONT] allows updates which introduce new dependancies to proceed. On Ubuntu, this can be vital if you want your kernel up-to-date for security reasons.

---

