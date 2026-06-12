---
title: "gnucash dependency hell"
date: 2006-04-18
forum: General Help
---

### Post by owlcroft on 2006-04-18
I have updated my Synaptic repositories list, and it seems to conform to several different sets of popular recommendations.

I select gnucash and ask it to install.  It replies that it cannot, and lists three required files that would not be loaded:

#1 = **libgal23** (v. >= 0.24)

#2 = **libgdk-pixbuf-gnome2** (v. >= 0.22.0-8)

#3 = **libgtkhtml.1-3** (v. >= 1.1.10)

If I try to get those by themselves, #3 tells me it can't work because it requires #1 and #2.  If I try # 1, it can't work because it requires #2.  OK, clearly #2 is the linchpin.

But if I try to get #2, I'm told that it cannot work because it in turn requires **libgdk-pixbuf2** of version *0.22.0-8ubuntu0.1*, whereas version *0.22.0-8.1* is what is scheduled for installation.  BZZZZZT!

Curiouser and curioser: I find that in **/var/cache/apt/archives/** I already have deb packages for *both* versions.  Do I uninstall the unwanted one?  Or, were I to try that, would I break my desktop in some way before I could even get the other installed?  Or, if I drop back to a command-line interface after a reboot and make the change that way, will the one work as well as the other in my system as it stands?  (That is, ignoring the yet-uninstalled gnucash.)

I thought, as a Linux newcomer, that the APT system was supposed to avoid thiese kinds of nightmares. . . .

---

### Post by Sutekh on 2006-04-19
[QUOTE=owlcroft]I have updated my Synaptic repositories list, and it seems to conform to several different sets of popular recommendations.[/quote]
This may be the problem.  I would stick to the default repositories where possible, rather than using many different ones.

What does you current sources.list look like?

[quote=owlcroft]
Curiouser and curioser: I find that in **/var/cache/apt/archives/** I already have deb packages for *both* versions.  Do I uninstall the unwanted one?  Or, were I to try that, would I break my desktop in some way before I could even get the other installed?[/QUOTE]
The packages in that folder are **archives** of the package files, they are not the installed files.  If you have installed the packages, then you can delete those .deb files at any time.

---

### Post by owlcroft on 2006-04-19
[QUOTE=Sutekh]This may be the problem.  I would stick to the default repositories where possible, rather than using many different ones.

What does your current sources.list look like?[/QUOTE]Nothing too *outre*, I think:

```
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

## Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy-security universe multiverse

## Uncomment the following two lines to add software from the official 'backports' repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

## Uncomment this if you ever want WINE:
## deb http://wine.sourceforge.net/apt/ binary/

## plf primary repo
## http 100mbit/s mirror provided thanks to OVH http://ovh.com
## deb http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free
## deb-src http://packages.freecontrib.org/ubuntu/plf/ breezy free non-free

## plf mirror. use if primary repo is offline
## FTP mirror from http://free.fr (french ISP)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

## Uncomment this if you ever want the Opera browser:
#deb http://deb.opera.com/opera/ etch non-free

## Get KDE packages (?):
deb http://kubuntu.org/packages/kde351 breezy main

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
deb http://people.ubuntu.com/~doko/OOo2 ./

deb http://theli.free.fr/packages/breezy/ ./
## created by arnielistenadded

## Uncomment to access main Debian 'testing' branch:
#deb http://http.us.debian.org/debian testing main contrib non-free

```


> The packages in that folder are **archives** of the package files, they are not the installed files.  If you have installed the packages, then you can delete those .deb files at any time.Yes, I realize that; but I don't know, in this case, just which of the two really is or was installed.  I am guessing that the *0.22.0-8.1* one is the installed one, else I would think that Synaptic would not be complaining that it pines for the *0.22.0-8ubuntu0.1* version.  But I am unsure of those things.

I simply don't know what to do now to get gnucash--which I have a strong need for--installed.  Nor do I understand how this circumstance arose in the first place.

I came to Linux, and Ubuntu in particular, full of high hopes.  I have it installed as a clean, new single-boot system on my lady's computer; this is as a learning exercise in preparation for a *possible* eventual changeover of my own "enterprise" (ha) system from OS/2, which I still very much like but for which support, especially hardware drivers, is dwindling rapidly.

So far, while Ubuntu seems like a pretty neat idea when it runs, I have been appalled at the number of what should have been simple, straightforward things that have in the fact required intervention well beyond the little-old-lady-user stage to merely get the system up and running.  (Video, audio, dhcp, scsi, and several items of common software like gnucash.)

At any rate, all help wil be welcome.

---

### Post by Sutekh on 2006-04-19
> ## plf mirror. use if primary repo is offline
## FTP mirror from [http://free.fr](http://free.fr) (french ISP)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

## Get KDE packages (?):
deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

## Oo2 final - you can optionally use this one until OOo2 final arrives in backports
deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arnielistenadded

Try commenting these out and running
```
sudo apt-get update
sudo apt-get install gnucash
```

---

### Post by owlcroft on 2006-04-20
[QUOTE=Sutekh]Try commenting these out and running
```
sudo apt-get update
sudo apt-get install gnucash
```[/QUOTE]Nope.

Mind, I used Synaptic: I de-checked those repositories, then tried getting gnucash, which failed as before.  I then tried getting just the problem package, 
**libgdk-pixbuf2**, but that, too, was as before: wrong version.

Still in hell . . . .

---

