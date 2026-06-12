---
title: "sources.list HELP!!"
date: 2010-01-11
forum: General Help
---

### Post by emoguitarist06 on 2010-01-11
Everytime I run apt-get update I get this error:

**W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3135CD5C26C2E075**

Here is my /etc/apt/sources.list

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

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

# Added by perfectbuntu - [www.category5.tv](www.category5.tv)
deb [http://le-web.org/repository](http://le-web.org/repository) stable main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

---

### Post by Johnny B on 2010-01-11
run:
```
sudo gpg --keyserver subkeys.pgp.net --recv 3135CD5C26C2E075 && sudo gpg --export --armor 3135CD5C26C2E075 | sudo apt-key add -
```

---

### Post by emoguitarist06 on 2010-01-11
> **Johnny B said:**
> run:
```
sudo gpg --keyserver subkeys.pgp.net --recv 3135CD5C26C2E075 && sudo gpg --export --armor 3135CD5C26C2E075 | sudo apt-key add -
```

**Thanks for the quick reply! I ran the code and this is what came back**

> ~$ sudo gpg --keyserver subkeys.pgp.net --recv 3135CD5C26C2E075 && sudo gpg --export --armor 3135CD5C26C2E075 | sudo apt-key add -
gpg: WARNING: unsafe ownership on configuration file `/home/pumpkinfeet/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
~$

BTW how did you make that scrolling box in your reply?

---

### Post by michy99 on 2010-01-11
What is the output of this command?```
ls -l ~/.gnupg/gpg.conf
```

---

### Post by emoguitarist06 on 2010-01-11
> **michy99 said:**
> What is the output of this command?```
ls -l ~/.gnupg/gpg.conf
```

[B]~$ ls -l ~/.gnupg/gpg.conf
-rw------- 1 pumpkinfeet pumpkinfeet 9364 2010-01-06 19:40 /home/pumpkinfeet/.gnupg/gpg.conf
~$[/B]

---

### Post by michy99 on 2010-01-11
Somehow the permissions got messed up. To fix it:```
chmod 755 ~/.gnupg/gpg.conf
```Then try this again:```
sudo gpg --keyserver subkeys.pgp.net --recv 3135CD5C26C2E075 && sudo gpg --export --armor 3135CD5C26C2E075 | sudo apt-key add -
```Then try updating.

---

### Post by emoguitarist06 on 2010-01-11
:(

Wah!!

nothing's changed :(

---

### Post by emoguitarist06 on 2010-01-11
I've tried
chmod 555, 755, 775, & 777 and no luck :(

---

### Post by plucky on 2010-01-12
open a terminal and try ```
gpg --keyserver keyserver.ubuntu.com --recv EF4186FE247510BE
```

and ```
gpg --export --armor EF4186FE247510BE | sudo apt-key add -
```

Then ```
sudo apt-get update
``` and see if the warning message goes  away.


Good Luck

---

### Post by audiomick on 2010-01-12
> **emoguitarist06 said:**
> BTW how did you make that scrolling box in your reply?

use the "code" tabs instead of "quote". That is the # symbol.

---

### Post by Slim Odds on 2010-01-12
> **emoguitarist06 said:**
> I've tried
chmod 555, 755, 775, & 777 and no luck :(

~/.gnupg should be 700

```
chmod 700 ~/.gnupg
```

Should not be readable by anyone but you....!!

---

### Post by emoguitarist06 on 2010-01-12
> **plucky said:**
> open a terminal and try ```
gpg --keyserver keyserver.ubuntu.com --recv EF4186FE247510BE
```

and ```
gpg --export --armor EF4186FE247510BE | sudo apt-key add -
```

Then ```
sudo apt-get update
``` and see if the warning message goes  away.


Good Luck

ERUKA!! IT WORKED!! Thanks for all your hard work and dedication to the ubuntu community :)

---

### Post by Slim Odds on 2010-01-12
> **emoguitarist06 said:**
> ERUKA!! IT WORKED!! Thanks for all your hard work and dedication to the ubuntu community :)

For the community, can you tell what you did that actually made it work?

---

### Post by emoguitarist06 on 2010-01-12
> **Slim Odds said:**
> For the community, can you tell what you did that actually made it work?

I did exactly what raymondh told me to

> gpg --keyserver keyserver.ubuntu.com --recv EF4186FE247510BE
gpg --export --armor EF4186FE247510BE | sudo apt-key add -
sudo apt-get update

His previous advice of using:
```
sudo gpg --keyserver subkeys.pgp.net --recv 3135CD5C26C2E075 && sudo gpg --export --armor 3135CD5C26C2E075 | sudo apt-key add -
```
didn't work.

---

