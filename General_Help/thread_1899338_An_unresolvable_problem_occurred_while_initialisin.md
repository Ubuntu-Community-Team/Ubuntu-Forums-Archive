---
title: "An unresolvable problem occurred while initialising the package information."
date: 2011-12-23
forum: General Help
---

### Post by benhanby on 2011-12-23
Hi i'm new to ubuntu, update manager keeps giving me the following message :
Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)'

when i enter this into the terminal 
> ~$ cat /etc/apt/sources.listi get this 
> # deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ dists/oneiric/main/binary-i386/

# deb cdrom:[Ubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111012)]/ oneiric main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) oneiric-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) oneiric-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) oneiric main
deb [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
deb-src [http://archive.canonical.com/](http://archive.canonical.com/) oneiric partner
sorry but i don't have the foggyest clue about whats wrong or what i should do!
Thanks for any help :)

---

### Post by valvegrid on 2011-12-23
Try updating your sources list for a start:

> sudo apt-get update

Enter that in a terminal and enter your password.

---

### Post by benhanby on 2011-12-23
Thanks for the advice when i enter 
> sudo apt-get update                      i get 
> E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by oldos2er on 2011-12-23
Line 59 in your sources.list should be ```
deb-src http://archive.canonical.com/ubuntu oneiric partner
```
Open the file with admin privileges so you can edit it: ```
gksu gedit /etc/apt/sources.list
``` You can copy and paste the new line I've posted above over the old one. Save and exit the file, then run ```
sudo apt-get update
``` Hopefully that will fix the error.

---

### Post by benhanby on 2011-12-23
Thankyou very much for the help i did as you said and now the following message come up when i use the final code: 


> 'E:Malformed line 60 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.'> E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.Sorry to keep pestering im hopless at this!
Thankyou for resolving line 59 for me :)

---

### Post by oldos2er on 2011-12-23
I just noticed you have the partner repo mentioned twice (if erroneously), sorry for not seeing that earlier. Open the file in gedit again ```
gksu gedit /etc/apt/sources.list
``` Delete all the lines below ```
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
``` at the bottom of the file. Add the following two lines in their place: ```
deb http://archive.canonical.com/ubuntu oneiric partner
deb-src http://archive.canonical.com/ubuntu oneiric partner
``` Save, and ```
sudo apt-get update
``` again. Let me know how it goes.

---

### Post by benhanby on 2011-12-23
Thank you very much this has resolved all of the issues i was experiencing , your help is very much appreciated!

---

### Post by oldos2er on 2011-12-23
You're welcome. Enjoy Ubuntu!

---

