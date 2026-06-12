---
title: "apt-get error : E: Couldn't find package"
date: 2011-04-26
forum: General Help
---

### Post by techbrainless on 2011-04-26
Hi All , 
I have ubuntu intrepid installed in one of the amazon servers , when i try to install any software using apt-get i used to get the following error
```
E: Couldn't find package .....
```
here is the source list
```
#cat /etc/apt/sources.list
deb http://ec2-us-east-mirror.rightscale.com/ubuntu intrepid main restricted universe multiverse
deb http://ec2-us-east-mirror.rightscale.com/ubuntu intrepid-updates main restricted universe multiverse

deb http://ec2-us-east-mirror1.rightscale.com/ubuntu intrepid main restricted universe multiverse
deb http://ec2-us-east-mirror1.rightscale.com/ubuntu intrepid-updates main restricted universe multiverse

deb http://ec2-us-east-mirror2.rightscale.com/ubuntu intrepid main restricted universe multiverse
deb http://ec2-us-east-mirror2.rightscale.com/ubuntu intrepid-updates main restricted universe multiverse

deb http://ec2-us-east-mirror3.rightscale.com/ubuntu intrepid main restricted universe multiverse
deb http://ec2-us-east-mirror3.rightscale.com/ubuntu intrepid-updates main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted universe multiverse
```

by the way even so when i try to apt-get update , i got the following
```
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Krytarik on 2011-04-26
Obviously, because Intrepid's support ended almost one year ago:
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.10_.28Intrepid_Ibex.29](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Ubuntu_8.10_.28Intrepid_Ibex.29)

You could try to modify the sources like this:
```
deb http://old-releases.ubuntu.com/ubuntu/ intrepid main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ intrepid-security main restricted universe multiverse
```
Greetings.

---

### Post by plucky on 2011-04-26
> I have ubuntu intrepid installed

Intrepid has reached End of Life and is no longer supported.

> when i try to install any software using apt-get i used to get the following error
Code:

E: Couldn't find package .....


The Intrepid Repositories have been shut down.

See [http://ec2-us-east-mirror.rightscale.com/ubuntu/dists/](http://ec2-us-east-mirror.rightscale.com/ubuntu/dists/)

What package are you trying to install?

See [Ubuntu Releases](https://wiki.ubuntu.com/Releases)

Perhaps it is time to upgrade.

Good Luck

---

### Post by techbrainless on 2011-04-26
Thanks for all the replies

Hi [Krytarik]("http://ubuntuforums.org/member.php?u=1187548")  your answer works for me , thanks alot

---

### Post by Joe of loath on 2011-04-26
I advise against using Intrepid for anything, it's too old to be of use for testing, and has been unsupported for long enough to be too insecure for a production machine.

---

### Post by AllGamer on 2011-04-26
well, i do understand why some people might not want to upgrade.

not all Linuxes are made equal for all hardwares ;)

some hardware only works with some specific versions of distros, because either 
a) the hardware vendor no longer offer updated drivers & no sources are availeble to compile your own drivers
b) the hardware runs too slow in newer linuxes
c) hardware is not supported on newer linux distros


I've been in those shoes several times, and i always ended up doing either of these:
a) upgrade the hardware parts preventing the upgrade
b) find alternative drivers sources
c) stay with that version of linux forever
d) downgrade to a previous version of linux that is compatible with the hardware

:)

---

