---
title: "Update ERROR"
date: 2011-11-11
forum: General Help
---

### Post by AzharCh on 2011-11-11
Hi guys,

I am receiving following error while updating

E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)

any idea what it is??

---

### Post by matt_symes on 2011-11-11
Hi

Open a terminal and type

```
cat /etc/apt/sources.list
```

Copy and paste the results back here. Copy and paste by selecting the text in the terminal, right clicking and select copy.

You have a malformed line in that file and when we can see it we can tell you how to remove it.

Kind regards

---

### Post by AzharCh on 2011-11-11
hi,
I got following

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release i386 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) maverick partner
deb-src [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) maverick partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner


Regards

---

### Post by matt_symes on 2011-11-11
Hi

> ## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) maverick partner
deb-src [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) maverick partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

A couple of points.

It looks like you are running Oneiric but you have some sources for Maverick and a malformed line for Lucid.

It is not wise to use sources from a different version of Ubuntu. That can cause you no end of problems.

What i would suggest is removing these lines from your sources.list file.

> deb [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) maverick partner
 deb-src [http://archive.cononical.com/ubuntu](http://archive.cononical.com/ubuntu) maverick partner
 deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner
 deb-src [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

Open a terminal and type

```
sudo sed -i '57,60d' /etc/apt/sources.list
```

Enter your password. It will not be echoed to the screen.

Then type

```
sudo apt-get update
```

Kind regards

---

### Post by AzharCh on 2011-11-11
hi,

Thanks for your reply.
what if i correct the url in source.list file, should it work. (i.e [http://archive.canonical.com/dists/lucid/](http://archive.canonical.com/dists/lucid/) instead of [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid))

I appreciate your help

Regards
Azhar

---

### Post by matt_symes on 2011-11-11
Hi

> **AzharCh said:**
> hi,

Thanks for your reply.
what if i correct the url in source.list file, should it work. (i.e [http://archive.canonical.com/dists/lucid/](http://archive.canonical.com/dists/lucid/) instead of [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid))

I appreciate your help

Regards
Azhar

For a start you would still be using Lucid sources and you want to be using Oneirics. 

Why do you want Lucids sources so much ? Is there an application you are trying to install that not available in Oneric ?

> [http://archive.canonical.com/dists/lucid/](http://archive.canonical.com/dists/lucid/)The archive you want is here.

> [http://archive.canonical.com/dists/oneiric/](http://archive.canonical.com/dists/oneiric/)This is still the wrong format for sources.list anyway. You cant just add [http://archive.canonical.com/dists/oneiric/](http://archive.canonical.com/dists/oneiric/) as a source. It will not work.

You would be looking at something like

```
sudo bash -c "echo deb http://archive.canonical.com/ oneiric partner >> /etc/apt/sources.list"
```

```
sudo apt-get update
```

Kind regards

---

### Post by AzharCh on 2011-11-11
thanks matt,
I dont need maverick and lucid. I got it fixed as u suggested

Regards

---

