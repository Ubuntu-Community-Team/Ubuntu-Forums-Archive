---
title: "How to get unchecked updates"
date: 2009-07-13
forum: General Help
---

### Post by Oldhacker on 2009-07-13
This morning, there were a number of updates available, but four did not give me the opportunity to check them to accept for download and installation:
Avidemux; devede; K9 copy; transcode

How does one get updates that cannot be manually checked in the update manager? This has happened in the past, and I assume that they are in a different repository.

Thanks

---

### Post by j7%&lt;RmUg on 2009-07-13
If you are looking at the updates in Update Manager and those 4 updates are greyed out, it usually means that you have the ubuntu-proposed repository checked in software sources.

To uncheck this repository got to System > Administration > Software Sources

Click on the updates tab and uncheck "prereleased updates" click close and if it asks you, reload the software sources.

Hope this helps.

---

### Post by philinux on 2009-07-13
> **Oldhacker said:**
> This morning, there were a number of updates available, but four did not give me the opportunity to check them to accept for download and installation:
Avidemux; devede; K9 copy; transcode

How does one get updates that cannot be manually checked in the update manager? This has happened in the past, and I assume that they are in a different repository.

Thanks

Which version of ubuntu are you running?

---

### Post by Oldhacker on 2009-07-13
I am using Ubuntu 8.10 for AMD64

When I tried what you suggested about unchecking pre-release updates, it popped up the following message:

W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

---

### Post by philinux on 2009-07-13
Post your sources list.

```
cat /etc/apt/sources.list
```

Dont forget the code tags. Makes it easier to read.

---

### Post by Oldhacker on 2009-07-13
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) intrepid-security multiverse
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) jaunty main
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid multiverse

---

### Post by philinux on 2009-07-13
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid mai

I'm not sure these are repositories. How/why did you add them?

---

### Post by Oldhacker on 2009-07-13
Some application that I was going to try had me add them, but I don't recall which one it was now.

---

### Post by philinux on 2009-07-13
> **Oldhacker said:**
> Some application that I was going to try had me add them, but I don't recall which one it was now.

I would remove them then.

---

### Post by Oldhacker on 2009-07-13
The two unremembered sources are now deleted.
What remains is to see if that changes the inability to check and download updates that were greyed out before.

Thanks to everyone for their input.

---

### Post by philinux on 2009-07-13
> **Oldhacker said:**
> The two unremembered sources are now deleted.
What remains is to see if that changes the inability to check and download updates that were greyed out before.

Thanks to everyone for their input.

Ok so now in a terminal so you can see any errors:-

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Oldhacker on 2009-07-13
Running that gave me two duplicate sources, whereupon it suggested that I run apt-get update to correct. Remembering to add "sudo" before apt-get update,
I ran that and it reported no errors. :-)

Now, all I have to do is get future updates???

Thanks again for your help

---

