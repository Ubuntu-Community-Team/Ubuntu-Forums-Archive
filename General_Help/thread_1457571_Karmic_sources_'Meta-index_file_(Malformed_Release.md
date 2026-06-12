---
title: "Karmic sources: 'Meta-index file (Malformed Release file?)' error"
date: 2010-04-18
forum: General Help
---

### Post by Helkaluin on 2010-04-18
Hi,

I've tried Google in general and on this forum, so far what I got were wrong 'Components' fields (e.g. adding 'web' whereas there're only 'free' and 'non-free' available for the repository) for the source line in question. But I can't quite get my head around this one:

Error when doing apt-get update:
```
W: Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release  Unable to find expected entry  free/binary-i386/Packages in Meta-index file (malformed Release file?)
```My source list:
```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner


deb http://ppa.launchpad.net/gezakovacs/ppa/ubuntu karmic main
# deb-src http://ppa.launchpad.net/gezakovacs/ppa/ubuntu karmic main
deb http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/flam3/ppa/ubuntu intrepid main
# deb http://debian.anonymous-proxy-servers.net karmic main
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
# deb http://getswiftfox.com/builds/debian unstable non-free
deb http://mirror.netcologne.de/torproject.org karmic main
deb http://security.ubuntu.com/ubuntu/ karmic-security universe restricted main multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe restricted main multiverse
```As you can see the system somehow believes there's a [FONT=Courier New]</ubuntu/dist/karmic/free>[/FONT] whereas clearly there isn't. But I can't quite get that from sources.list

Does anyone have any idea?

Thank you for your attention.

---

### Post by drs305 on 2010-04-18
You may be able to clear the list by opening Synaptic or Software Sources. Go to Settings, Repositories. In the Ubuntu software tab change your source (Download from [noparse]:)[/noparse] to another server.

Reload and see if the error persists. You can even go right back to the gb. server to see if it was a one-time problem that may already be corrected.

---

### Post by Helkaluin on 2010-04-19
drs305: I've tried changing the repos server before posting and after you've suggested it. Still no luck. Clearing apt cache has no effect on the problem.

After reading into the apt-related man pages and digging around the [FONT=Courier New]/etc/apt [/FONT]directory, I've found that the [FONT=Courier New]/etc/apt/sources.list.d[/FONT] also contributes towards the sources list.

Apparently the Medibuntu file somehow reads a duplicate entry of [FONT=Courier New]http://gb.archive.ubuntu.com/ubuntu[/FONT] and the Software Sources frontend doesn't like to show that kind of entry in its GUI (it thinks it's part of the official repos, and so is only changeable in the form of checkboxes in the tab 'Ubuntu Software' and not in list form in the tab 'Other Software'). Obviously, the entry has[FONT=Courier New] free[/FONT] and[FONT=Courier New] non-free[/FONT] in it, thus the meta-index error.

So the GUI does have short comings, given a stupid enough user who can't remember how did he mess up the [FONT=Courier New]/etc/apt/sources.list.d[/FONT] contents!

(On retrospect, though, try changing one of your 'Other Software' sources into one of the official repos - the effect is simply that the line will disappear in 'Other Software', and you have to change it back by going into[FONT=Courier New] /etc/apt/sources.list.d[/FONT]) (Which is very probably what I have done, given the recent Medibuntu repos server downtime, changing the mirror by copy and pasting apparently got me the wrong URL.) (Shouldn't there be some dummy-proof restriction on this?)

---

