---
title: "Flash 10 will not Install!"
date: 2009-11-01
forum: General Help
---

### Post by OldTimeyJunk on 2009-11-01
I downloaded Flash 10 off Adobe's website (I used the .deb file) and when I open it up the GDebi package manager comes up but there is red text saying - "Error: Dependency is not satisfiable: libnspr4-dev" What Happened? PLEASE HELP!!
Oh, and I have Ubuntu 9.10 (Official Release, not Alpha/Beta)

Josh Robertson :D

---

### Post by ghostier on 2009-11-01
Try getting flash through the software manager. Or try going to a website with flash and then click on install when it prompts you that there are missing plugins.

---

### Post by OldTimeyJunk on 2009-11-01
When I'm on the Software Manager it says "Not Available for your Hardware Architecture" I don't get this cuz it worked on Ubuntu 9.04 & 8.10 and I have 32-Bit PC :(. Infact I think it might be a problem with it- beacause nearly every program I try says "Not Available in the Current Data" - BTW - I used Ubuntu Software Center

---

### Post by barthel on 2009-11-01
Which repositories have you enabled?

Also, after enabling repositories, you need to reload (in Synaptic) or `aptitude update` in a terminal.

---

### Post by liquidbee on 2009-11-01
```
sudo apt-get install libnspr4-dev
```

Try installing Flash again - it shouldn't fail. Also, can you show us your sources.list ?

---

### Post by OldTimeyJunk on 2009-11-01
It came up with this...
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libnspr4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnspr4-0d
E: Package libnspr4-dev has no installation candidate

```

This is my "sources.list"
```

# added by the release upgrader
deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/ karmic main restricted
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ karmic main restricted #Added by software-properties
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ karmic main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic universe
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ karmic multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu karmic-security main restricted
deb-src http://security.ubuntu.com/ubuntu karmic-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu karmic-security universe
deb http://security.ubuntu.com/ubuntu karmic-security multiverse

# deb http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main # disabled on upgrade to karmic
# deb-src http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu karmic main # disabled on upgrade to karmic

# deb http://ppa.launchpad.net/awn-testing/ubuntu karmic main # disabled on upgrade to karmic
# deb-src http://ppa.launchpad.net/awn-testing/ubuntu karmic main # disabled on upgrade to karmic
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.04 "Jaunty Jackalope" disabled on upgrade to karmic

```

---

### Post by barthel on 2009-11-04
Granted that I'm using the US archive and running 64-bit, but libnspr4-dev is in Ubuntu main.

If you use Synaptic (System -> Administration -> Synaptic Package Manager) and type "libnspr" in the "Quick Search" box, you should see libnspr4-0d, libnspr4-0d-debug, and libnspr4-dev. (This assumes you're in category "All", which I believe is default when you first open Synaptic.)

It's definitely not an archive issue. I just checked [http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nspr/](http://gb.archive.ubuntu.com/ubuntu/pool/main/n/nspr/) and the packages are there.

I also took a quick look at the early levels of the dependency tree and libnspr4-dev is *NOT* a dependency of flashplguin-installer.

To me, this suggests that something is wrong in your apt hierarchy.

Did you do an upgrade or a clean install of Karmic?

---

### Post by sm1thson on 2009-11-04
Hi, I had the same issue. I had to click the link in this thread [http://ubuntuforums.org/showthread.php?t=1301008&highlight=Dependency+flash]("http://ubuntuforums.org/showthread.php?t=1301008&highlight=Dependency+flash")which then (in my case) said something about there been a broken version (as i had tried to install and failed) so i had to go to add remove programs (or the synoptic manger?) search for broken, remove it then the link in hte above thread worked and installed it all no problems.

I think i read it is an error in the download from adobe.

---

### Post by HiImTye on 2009-11-04
> **OldTimeyJunk said:**
> It came up with this...
```
Package libnspr4-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnspr4-0d

```
try
```
sudo apt-get install libnspr4-0d
```

first remove your original flash from synaptic (administrator>synaptic package manager)

what I would do is remove flash and try installing flash from synaptic itself:
search for flash within synaptic (load synaptic, type in flash in the search box, select the ones with a green box on the left. choose 'purge' or 'completely uninstall' or whatever the option is)
install 'flashplugin-nonfree' (search for flash again, look for it)

---

