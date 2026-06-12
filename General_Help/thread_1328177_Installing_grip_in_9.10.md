---
title: "Installing grip in 9.10"
date: 2009-11-16
forum: General Help
---

### Post by Arndt on 2009-11-16
I recently upgraded to Karmic Koala (9.10) and one thing that happened was that certain repositories are no longer enabled, and the program 'grip' was removed. I'd like to install it again, but I don't quite succeed. I have found threads about the subjects in this forum, but trying to follow what they say doesn't work for me. For example, I added this line to sources.list:

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) jaunty main universe

but grip is still not found.

---

### Post by blazemore on 2009-11-16
Could you please post the output of
```
cat /etc/apt/sources.list
```

---

### Post by Arndt on 2009-11-16
> **blazemore said:**
> Could you please post the output of
```
cat /etc/apt/sources.list
```

# 
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://se.archive.ubuntu.com/ubuntu/](http://se.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) jaunty main universe

---

### Post by t0p on 2009-11-16
I see you have some Jaunty repos set, even though you say you're using Karmic.  Might that be your problem?

In your OP, you said you've tried to install grip but "don't quite succeed".  What do you mean?  Can you please tell us exactly *how* you've tried to install grip, and how exactly the install fails?

It would be useful if you attempted to install the package via the command-line and posted the output.  Enter in a terminal the command

```
sudo apt-get install grip
```

and post here the output.

---

### Post by P4man on 2009-11-16
> **Arndt said:**
> . For example, I added this line to sources.list:

deb [http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) **jaunty** main universe



Try replacing that jaunty with **karmic**. Do it with other sources as well, unless you know for sure there is no karmic repo for that particular ppa and you know the jaunty one will work. (oh and remove any duplicates while you're at it)

---

### Post by Arndt on 2009-11-16
> **t0p said:**
> I see you have some Jaunty repos set, even though you say you're using Karmic.  Might that be your problem?

In your OP, you said you've tried to install grip but "don't quite succeed".  What do you mean?  Can you please tell us exactly *how* you've tried to install grip, and how exactly the install fails?

It would be useful if you attempted to install the package via the command-line and posted the output.  Enter in a terminal the command

```
sudo apt-get install grip
```

and post here the output.

```
# sudo apt-get install grip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grip is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package grip has no installation candidate
```

I also replaced "jaunty" with "karmic" in sources.list (except in jaunty-backports), but this makes no difference.

I could say "I don't succeed at all", but at first I thought it might have been made obsolete, and then I found a page where it could be downloaded, and it recommended that I add that last line instead of downloading. I also did try downloading, and then there was an error message about libkr5 or something similar missing. As far as I can see, that's Kerberos, and I don't see what Kerberos has to do with grip. This is the page: [http://packages.ubunut.com/jaunty/grip](http://packages.ubunut.com/jaunty/grip).

As for the "jaunty" lines, I don't know why the file looks like it does. I assumed the upgrade process to 9.10 would set everything up correctly.

---

### Post by mc4man on 2009-11-16
> I don't see what Kerberos has to do with grip

Well the grip source has a libcurl dependency which in jaunty resulted in Kerberos becoming one of the dependencies.

Karmic has a newer version with a different name, that's why it can't be installed.
Also the debian maintainer for grip (Daniel Baumann), abandoned it last spring, so the odds of it reappearing are slim.

The only way you're installing the jaunty version is to install the jaunty Kerberos package, the advisability of doing that is unknown to me, ie. having 2 versions of Kerberos installed at once.

I'd be inclined not to, though one could do as they please, or seek info from someone who knows Internet security well.

Other options include 

Using a better, current ripper like rubyripper or abcde

Building your own grip from source ( the jaunty source without the debian diff applied would build fine and seems to work ok.

Build the jaunty source with diff applied to a grip package, with the libcurl dependency satisfied with current karmic packages * either libcurl4-gnutls-dev or libcurl4-openssl-dev, don't know the difference myself the former seems more likely

Did build as package so as to test, though have no inclination to use, prefer above mentioned rippers by far

These would be your basic build depends for karmic  (but not all if doing a debian package

> +Build-Depends: debhelper (>= 7), dpatch, autotools-dev, autoconf, libcdparanoia0-dev, libcurl4-gnutls-dev, libglib2.0-dev, libgnome2-dev, libgnomeui-dev, libgtk2.0-dev, libid3-3.8.3-dev, libvte-dev

---

### Post by oldos2er on 2009-11-16
Grip v3.3.1 is working fine here on 9.10. I compiled it from source code found here: [http://nostatic.org/grip/grip-download.shtml](http://nostatic.org/grip/grip-download.shtml)

---

### Post by Arndt on 2009-11-16
Thanks for all the answers. I think I'll just use some other program, like sound-juicer.

---

### Post by rapido on 2010-02-01
I compiled grip from sources, which seemed to work just fine.  

Following is a link to the post on that topic, complete with a shell script to automate the work - [http://ubuntuforums.org/showpost.php?p=8759491&postcount=25]("http://ubuntuforums.org/showpost.php?p=8759491&postcount=25")

---

### Post by dentament on 2010-04-30
Here is a ppa with pre-packaged grip
[https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)

---

### Post by oldos2er on 2010-04-30
> **dentament said:**
> Here is a ppa with pre-packaged grip
[https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)

Thanks for that. I compiled grip on Lucid a couple weeks ago though; even tho' it's getting a little long in the tooth I haven't found another ripper app with similar features.

---

