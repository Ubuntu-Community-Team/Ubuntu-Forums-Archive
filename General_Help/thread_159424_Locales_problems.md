---
title: "Locales problems"
date: 2006-04-12
forum: General Help
---

### Post by tokez on 2006-04-12
My locales do not seem to be working atm. When I use synaptic (and terminal) to install the locales package it returns:
```

andrew@andrew:/usr/src/linux$ sudo apt-get install locales
Password:
Reading package lists... Done
Building dependency tree... Done
locales is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up locales (2.3.5-1ubuntu12.5.10.1) ...
Generating locales...
  en.ISO-8859-1...cannot open locale definition file `en': No such file or directory
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.2.ds1-20ubuntu3) | belocs-locales-data (>= 2.3.4-16ubuntu1); however:
  Package locales is not configured yet.
  Package belocs-locales-data is not installed.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of localeconf:
 localeconf depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing localeconf (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
 language-pack-en-base
 localeconf
 language-pack-en
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Tried internet and forum searches and not able to find anything on it. As a matter of fact, I cant even find the term 'locales' on superindex.apress.com ...

This is stopping me from activating my Direct Rendering and is becoming a problem. Please help...

Thanks in advance.

---

### Post by tokez on 2006-04-12
I figured this might be a bit more to the point for those who just skim :P

```

andrew@andrew:~$ sudo dpkg-reconfigure locales
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/sbin/dpkg-reconfigure: locales is broken or not fully installed
andrew@andrew:~$

```

Have tried everything I know how to do to no avail. Please assist.

---

### Post by tokez on 2006-04-12
Ok, I see what the problem is.

/usr/lib/locales/ is coming up blank. Even after running the 'sudo apt-get install locales' . For some reason it doesnt seem to be installing it completely, possibly because of missing locales ....

Does anyone know where I can get a hold of the en_US.UTF8 locale without running thru Synaptic or apt-get to try and troubleshoot?

Or if you have an idea of why my installation is faulty that would help as well.

---

### Post by tokez on 2006-04-13
Bumping incase someone who knows missed the post.

My locales still arent working and I have tried everything, including downloading what I believed to be a locales .tar.gz and manually unpacking it into my /usr/lib/locale directory. This does not solve the problem.

locales -a  returns that 3 folders for the locales are non-existant. I am new to ubuntu and am completely dumbfounded by this problem.

As said above, this is stopping me from completely installing/removing certain apps/packages and is really causing a problem.

If i cannot fix it by the end of this week, I will be installing OpenSUSE and see if the problem follows.

Thanks.

---

### Post by tokez on 2006-04-13
```

andrew@andrew:/usr/lib/locale$ sudo apt-get install language-pack-gnome-en
Reading package lists... Done
Building dependency tree... Done
language-pack-gnome-en is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up locales (2.3.5-1ubuntu12.5.10.1) ...
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Generating locales...
  en.ISO-8859-1...cannot open locale definition file `en': No such file or directory
dpkg: error processing locales (--configure):
 subprocess post-installation script returned error exit status 4
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.2.ds1-20ubuntu3) | belocs-locales-data (>= 2.3.4-16ubuntu1); however:
  Package locales is not configured yet.
  Package belocs-locales-data is not installed.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.2.ds1-20ubuntu3) | belocs-locales-data (>= 2.3.4-16ubuntu1); however:
  Package locales is not configured yet.
  Package belocs-locales-data is not installed.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 locales
 language-pack-en-base
 language-pack-gnome-en-base
 language-pack-en
 language-pack-gnome-en
E: Sub-process /usr/bin/dpkg returned an error code (1)
andrew@andrew:/usr/lib/locale$

```

---

### Post by tokez on 2006-04-13
```

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
deb-src http://archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

deb http://archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse


deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

deb http://deb.opera.com/opera/ etch non-free

deb http://kubuntu.org/packages/kde351 breezy main

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://koti.mbnet.fi/~ots/ubuntu/ breezy/
deb-src http://koti.mbnet.fi/~ots/ubuntu/ breezy/

deb http://people.ubuntu.com/~doko/OOo2 ./
deb http://theli.free.fr/packages/breezy/ ./
## created by arnielistenadded

deb http://wine.sourceforge.net/apt/ binary/

```

---

### Post by tokez on 2006-04-14
The problem was identified and corrected.

To fix it I ran
sudo dpkg-reconfigure --force locales
and deselected every locale that did not begin with en_US.
In my case this left me with just 2 locales, en_US.ISO and en_US.UTF .
Only allowing these and then continuing on corrected my locale issue and therefore allowed me to flawlessy install my ati drivers and enable 3d hardware support.

Complicated problem -- elementary fix :P

ALL THANKS TO WOEDEND :P

***NOTE:
In my case I selected en_US.UTF-8 as my default locale. Not sure if this matters, but it was my used setting that worked.

---

### Post by jimoupas on 2006-04-27
Man .. thanks a lot!!!!
im trying to find a fix for that few days now with much help from gnomefreak and jobezone (irc) and we couldnt fix it with everything we tried.... 

anyway i did what u said and everything is fixed as i see !! really thanks man

---

### Post by werem00se on 2006-05-06
Yes, thanks a TON.  My hoary=>breezy upgrade failed miseably, leaving me with no X and errors running apt.  This was a huge clue to the problem.

---

