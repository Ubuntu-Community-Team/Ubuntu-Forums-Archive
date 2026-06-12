---
title: "are the repositories down?"
date: 2010-08-09
forum: General Help
---

### Post by kiridude on 2010-08-09
I cannot update (apt-get update) my system, upgrade, or install new programs through apt or synaptic. I am told that I may have a wrong repository address. Did something happen to my system, or is it on the other end?

Thanks.

---

### Post by inameiname on 2010-08-09
Checking mine just now, they all work just fine, both the official repos and all of my PPAs. 

Did you happen to change your sources.list any? What is it's readout?:

gksudo gedit /etc/apt/sources.list

---

### Post by -kg- on 2010-08-09
> **kiridude said:**
> I cannot update (apt-get update) my system, upgrade, or install new programs through apt or synaptic. I am told that I may have a wrong repository address. Did something happen to my system, or is it on the other end?

Thanks.

> Join Date: Mar 2009
Location: E.U.
Beans: 250
[COLOR="Red"]Ubuntu 9.04 Jaunty Jackalope[/COLOR] 

Are you still running Jaunty, or have you just not updated your CP Panel setting yet?  Support for Jaunty runs out some time this month, and if it already has, the repos will be archived.  I don't know if it has been officially "unsupported" yet, but if it has, that might be your problem.

---

### Post by inameiname on 2010-08-09
Good catch -kg-, I completely missed the fact that he might be still with Jaunty. ;)

---

### Post by Bachstelze on 2010-08-09
> **-kg- said:**
> Support for Jaunty runs out some time this month

No. Suport for Jaunty ends in October with the release of Maverick.

---

### Post by soldier1st on 2010-08-09
9.04 is still supported until October of this year(2 and a half months left) did you try to change servers?perhaps the server that your using is having problems.

---

### Post by kiridude on 2010-08-09
thanks guys for the replies. No I updated to lucid when it came out and everything was working normally up until about a week ago.

Here is my sources.list:

```
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gr.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid universe
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://security.ubuntu.com/ubuntu lucid-security main restricted
deb-src http://security.ubuntu.com/ubuntu lucid-security main restricted
deb http://security.ubuntu.com/ubuntu lucid-security universe
deb-src http://security.ubuntu.com/ubuntu lucid-security universe
deb http://security.ubuntu.com/ubuntu lucid-security multiverse
deb-src http://security.ubuntu.com/ubuntu lucid-security multiverse

deb http://deb.torproject.org/torproject.org lucid main


```

sorry, forgot to update what version I'm running.

Thanks

---

### Post by Bachstelze on 2010-08-09
What's the exact error message that appears when you try to [font=monospace]apt-get update[/font]?

---

### Post by kiridude on 2010-08-09
I was gettting 404 not found errors, but I figured out the problem. The server I was using has either been changed or has a problem. I pointed synaptic to another server and now everything works normally.

Thanks.

---

### Post by ccc2007chaos on 2010-08-09
same problem here. looks like the greek servers are down..

---

### Post by -kg- on 2010-08-09
> **Bachstelze said:**
> No. Suport for Jaunty ends in October with the release of Maverick.

Sorry all...a mule must have kicked me in the math side of my brain!:D

I've had similar problems here in the U.S.  Certain of the servers don't have some of the Lucid repos and I couldn't use the (closer) ones that I used before.  Seems like someone is asleep at the switch.

---

### Post by ccc2007chaos on 2010-08-09
> **ccc2007chaos said:**
> same problem here. looks like the greek servers are down..


sorry for saying nothing...


what i get from Software Update error message:

Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)  Could not connect to gr.archive.ubuntu.com:80 (147.102.222.211). - connect (110: Connection timed out)
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/i18n/Translation-en_US.bz2)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://gr.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Unable to connect to gr.archive.ubuntu.com:http:
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by ccc2007chaos on 2010-08-09
Do the following and it will work again!

System>Administration>Software Sources

click Download from:

select Other>Greece>Ubuntu.otenet.gr

the server of NTUA (Natinoal Technical University of Athens=&#917;&#952;&#957;&#953;&#954;&#959; &#924;&#949;&#964;&#963;&#959;&#946;&#949;&#953;&#959; &#928;&#959;&#955;&#965;&#964;&#949;&#967;&#957;&#949;&#953;&#959;) maybe went on vacations :D

found on:

[http://forum.ubuntu-gr.org/viewtopic.php?f=4&t=13582](http://forum.ubuntu-gr.org/viewtopic.php?f=4&t=13582)

---

### Post by NeverHide on 2010-08-10
> **ccc2007chaos said:**
> Do the following and it will work again!

System>Administration>Software Sources

click Download from:

select Other>Greece>Ubuntu.otenet.gr

the server of NTUA (Natinoal Technical University of Athens=&#917;&#952;&#957;&#953;&#954;&#959; &#924;&#949;&#964;&#963;&#959;&#946;&#949;&#953;&#959; &#928;&#959;&#955;&#965;&#964;&#949;&#967;&#957;&#949;&#953;&#959;) maybe went on vacations :D

found on:

[http://forum.ubuntu-gr.org/viewtopic.php?f=4&t=13582](http://forum.ubuntu-gr.org/viewtopic.php?f=4&t=13582)


Just to make this a little more general,at the System>Administration>Software Sources>Download from select the "other..." option and then "Select Best Server" and it'll do the work for you ;)

---

