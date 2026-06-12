---
title: "Update issues"
date: 2010-03-05
forum: General Help
---

### Post by Rocprof on 2010-03-05
Hi all

Firstly to the guys who helped me with a AMD Ubuntu installation problem many many thanks it all worked out good.

Now then I do regular updated on my laptop but over the last few days it fails to obtain the last file and I am now getting a triangle reminding me that the updates are behind. Any ideas on how to fix this.

This is the error message I am getting



[B]W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg)  Could not connect to archive.getdeb.net:80 (127.0.0.1). - connect (111: Connection refused)

W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/i18n/Translation-en_GB.bz2](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/i18n/Translation-en_GB.bz2)  Could not connect to archive.getdeb.net:80 (127.0.0.1). - connect (111: Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.[/B]



Again I would appreciate any advice and help

Cheers for now

---

### Post by Intrepid Ibex on 2010-03-05
Getdeb is down sometimes but the [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/i18n/Translation-en_GB.bz2](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/i18n/Translation-en_GB.bz2) file doesn't exist ([http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/Release.gpg) I can download).

You can always update with sudo apt-get update/(dist-)upgrade --fix-missing

**E:** I mean just add the --fix-missing flag to the end of your update command.

---

### Post by Rocprof on 2010-03-05
Is that through the symantic package manager or the terminal kinda new to this so need some guidance

---

### Post by dcstar on 2010-03-05
> **Rocprof said:**
> 
........
W: Failed to fetch [http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/i18n/Translation-en_GB.bz2](http://archive.getdeb.net/ubuntu/dists/karmic-getdeb/games/i18n/Translation-en_GB.bz2)  Could not connect to archive.getdeb.net:80 (**127.0.0.1**). - connect (111: Connection refused)


Your system is trying to connect to your localhost address for Internet access, either you have a Proxy Server that is no longer working correctly or you have the Synaptic Proxy settings set wrong.

If your web browser access still works then make the Synaptic network proxy settings the same as the web browser/system Proxy settings.

---

### Post by Rocprof on 2010-03-05
cheers for that davis now all you need to do is tell me..... How exactly do I do that lol

---

### Post by lyall on 2010-03-05
GetDeb site is working now
I just got some downloads from there

it has been down for several days

good luck and have fun learning

---

### Post by jaycee23 on 2010-03-06
Still having exactly same issue as in OP. 

Tried updating via terminal using --fix-missing but same error displayed. All other updates are fine and internet access is good.

Is it a fault with GetDeb or with my system?

Any ideas welcome.

---

### Post by Intrepid Ibex on 2010-03-06
Well if the howto of adding the getdeb repository has changed, maybe it was worthy of a try to try doing it again: [http://www.getdeb.net/updates/Ubuntu/all#how_to_install](http://www.getdeb.net/updates/Ubuntu/all#how_to_install)
Could you also post your /etc/apt/sources.list?

---

### Post by jaycee23 on 2010-03-06
As requested - my /etc/apt/sources list


# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) karmic main
deb [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu](http://ppa.launchpad.net/jonoomph/openshot-edge/ubuntu) karmic main
deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/
deb [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/bisigi/ppa/ubuntu](http://ppa.launchpad.net/bisigi/ppa/ubuntu) karmic main
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) karmic-getdeb apps

---

### Post by sandyd on 2010-03-06
getdeb is still down.

---

### Post by jaycee23 on 2010-03-06
That's the answer I was hoping to hear Carlee

;)

---

### Post by jaycee23 on 2010-03-07
All good now - looks like GetDeb is up and running again!

:popcorn:

---

