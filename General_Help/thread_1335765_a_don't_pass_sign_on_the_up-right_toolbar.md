---
title: "a don't pass sign on the up-right toolbar"
date: 2009-11-23
forum: General Help
---

### Post by aray_rio on 2009-11-23
Hi there

im very newbi using GNU/Linux and UBUNTU, previously i've always use windows as my OS
but now i've got my laptop with Ubuntu 9.10 and Vista dual boot.

Ubuntu 9.10 really fascinating me because it's user friendly, but i'm having trouble right now, on the top-right of my desktop there's a don't pass sign that said :

[I][COLOR=Blue]""an error occured, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was:'Error : Opening the cache (E:Malformed line 56 in source list/etc/apt/sources.list(dist parse),E:the list of source  could not be read.)'This usually means that your installed packages have unmet dependencies."[/COLOR]

[/I]and every time i wanted to use the update manager there's a error note said :

[I][COLOR=Blue]"SystemError: E:Malformed line 56 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read."

[/COLOR][/I][COLOR=Blue][COLOR=Black]
i don't know what've i'd encountered and i don't know how to solve it
[/COLOR][/COLOR][COLOR=Blue][COLOR=Black]could anyone help me to solve this problem?

tku,
[/COLOR][/COLOR]

---

### Post by wojox on 2009-11-23
Sure open a terminal and run:

```
cat /etc/apt/sources.list
```

Copy & paste the contents back in code tags #

---

### Post by chaanakya_chiraag on 2009-11-23
btw, if you don't know how to open up a terminal, go to Applications->Accessories->Terminal :)

---

### Post by aray_rio on 2009-11-24
Tku for the response,
after i've run the command at the terminal,then the following was shown,

[COLOR=Blue][I]root@ario-ubuntu:/home/ario# cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

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
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main
deb [http://kambing.ui.ac.id/ubuntu/karmic](http://kambing.ui.ac.id/ubuntu/karmic) main
root@ario-ubuntu:/home/ario# 


[/I][COLOR=Black]But the dont pass sing still there and i still can't use my update manager.
are there anything i should do next?
[/COLOR][/COLOR]

---

### Post by polki@mac.com on 2009-11-24
The last line in your sources.list:

deb [http://kambing.ui.ac.id/ubuntu/karmic](http://kambing.ui.ac.id/ubuntu/karmic) main

should read:

deb [http://kambing.ui.ac.id/ubuntu/](http://kambing.ui.ac.id/ubuntu/) karmic main

(notice the space before "karmic")

Just open a terminal and run:

gksu gedit /etc/apt/sources.list

Put in the space where it should be, save and quit.

Happy installing!

---

