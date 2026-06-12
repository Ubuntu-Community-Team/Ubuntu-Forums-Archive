---
title: "Ubuntu 10.10 having a problem installing updates or .deb's at all!"
date: 2010-10-25
forum: General Help
---

### Post by r2rX on 2010-10-25
Hey guys,

I've encountered a problem which I have no idea the cause of or what the solution is.

Whether I use Ubuntu Software Center, Update Manager or Synaptic Package Manager, I always get the following error for ANYTHING I try install:

```

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 131223 files and directories currently installed.)

Preparing to replace firefox-gnome-support 3.6.12~hg20101021r34694+nobinonly-0ubuntu1~umd1~maverick (using .../firefox-gnome-support_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb) ...

Unpacking replacement firefox-gnome-support ...

dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'

dpkg-deb: subprocess <decompress> returned error exit status 2

dpkg: error processing /var/cache/apt/archives/firefox-gnome-support_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb (--unpack):

 short read on buffer copy for backend dpkg-deb during `./usr/share/doc/firefox-gnome-support/copyright'

No apport report written because MaxReports is reached already
Preparing to replace firefox-branding 3.6.12~hg20101021r34694+nobinonly-0ubuntu1~umd1~maverick (using .../firefox-branding_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb) ...

Unpacking replacement firefox-branding ...

dpkg: error processing /var/cache/apt/archives/firefox-branding_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb (--unpack):

 corrupted filesystem tarfile - corrupted package archive

No apport report written because MaxReports is reached already
tar: Skipping to next header

tar: Exiting with failure status due to previous errors

dpkg-deb: subprocess tar returned error exit status 2

dpkg: error processing /var/cache/apt/archives/firefox_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb (--unpack):

 subprocess dpkg-deb --control returned error exit status 2

No apport report written because MaxReports is reached already
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'

tar: Unexpected EOF in archive

tar: Unexpected EOF in archive

tar: Error is not recoverable: exiting now

dpkg-deb: subprocess tar returned error exit status 2

dpkg: error processing /var/cache/apt/archives/xulrunner-1.9.2_1.9.2.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb (--unpack):

 subprocess dpkg-deb --control returned error exit status 2

No apport report written because MaxReports is reached already
Errors were encountered while processing:

 /var/cache/apt/archives/firefox-gnome-support_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb

 /var/cache/apt/archives/firefox-branding_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb

 /var/cache/apt/archives/firefox_3.6.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb

 /var/cache/apt/archives/xulrunner-1.9.2_1.9.2.12~hg20101023r34698+nobinonly-0ubuntu1~umd1~maverick_amd64.deb


```

This particular error is refering to Mozilla software, but the same type of error occurs for ANYTHING at all....even if I download my own .deb files, it does the same thing.

I've tried 'sudo apt-get clean' but to no avail.

Anyone have any idea what's going on?

All the help is appreciated!

r2rX  :(

---

### Post by Hippytaff on 2010-10-25
Have you tried
```

sudo apt-get install -f

```
to fix broken packages if thats the problem :-)

---

### Post by r2rX on 2010-10-25
Hey Hippytaf,

No broken packages...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.
```

I'm at a loss...

r2rX

---

### Post by Hippytaff on 2010-10-25
Have you checked that sources list entries are correct?
```
[FONT=monospace]
cat [/FONT]/etc/apt/sources.list

```

---

### Post by r2rX on 2010-10-25
Seems to be. This happened over the past day...it was working fine prior....I don't think i've done anything in particular that would've caused this.

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ke.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ke.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://ke.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick universe
deb http://ke.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ke.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://ke.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ke.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://ke.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

deb http://archive.canonical.com/ubuntu maverick partner
```

r2rX

---

### Post by Hippytaff on 2010-10-25
Can't see anything wrong with that, though I'm no expert...not sure what to suggest

can you succesfully

```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by stoneage on 2010-10-25
I would recommend trying a different download server, particularly if you are using the one in the USA.

It might also be worth going to /var/cache/apt/archives/ and removing or renamimg whatever is there.

---

### Post by r2rX on 2010-10-25
This is so ridiculous....

I discovered the problem....ESET AntiVirus. :)

Once uninstalling it, everything is working fine now. Seems that ESET doesn't play well with Ubuntu 10.10 at the moment.

Thanks for all the help, guys.
r2rX  :D

---

### Post by Hippytaff on 2010-10-25
Excellent...there's not a massive need for anti-virus software on linux anyway...remeber to mark as solved :-)

---

