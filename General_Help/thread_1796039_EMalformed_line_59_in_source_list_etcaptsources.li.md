---
title: "E:Malformed line 59 in source list /etc/apt/sources.list (dist parse)"
date: 2011-07-03
forum: General Help
---

### Post by 02.R1 on 2011-07-03
I'm coming up with the error E:Malformed line 59 in source list /etc/apt/sources.list (dist parse) and when I go into terminal and type in gksudo gedit /etc/apt.sources.list and the text editor pops up and after it's finished loading it's just a blank screen with no sources. Is there anything I can do to fix this? Thanks

---

### Post by Rubi1200 on 2011-07-03
Hi and welcome to the forums :-)

What does ```
cat /etc/apt/sources.list
``` show in the terminal?

Post the contents here please.

---

### Post by 02.R1 on 2011-07-03
Heres the full error 

E: Malformed line 59 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by 02.R1 on 2011-07-03
When I type that in the terminal I get 

# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main
deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmicmain
deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmicmain

---

### Post by Rubi1200 on 2011-07-03
The problem I see are 2 lines for Karmic at the end of the list whereas the rest are for Natty.

You should be able to open the file to edit it with:

```
gksudo /etc/apt/sources.list
```

Then comment those last 2 lines out by putting a # at the beginning so it looks like this:

> #deb [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmicmain
#deb-src [http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu](http://ppa.launchpad.net/globalmenu-team/ppa/ubuntu) karmicmain 	

Save and close then run ```
sudo apt-get update
```

---

### Post by CatKiller on 2011-07-03
> **Rubi1200 said:**
> The problem I see are 2 lines for Karmic at the end of the list whereas the rest are for Natty.

Not only that, but he's not got a space between karmic and main...

---

### Post by 02.R1 on 2011-07-03
When I put in gksudo /etc/apt/sources.list in the terminal it just asks for my password and then doesn't do anything to let me edit the sources. It does this 

drew@drew-FK954AA-A2L-a6535c:~$ gksudo /etc/apt/sources.list
drew@drew-FK954AA-A2L-a6535c:~$

---

### Post by oldos2er on 2011-07-03
You left out 'gedit' ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Rubi1200 on 2011-07-03
Oops, my mistake :-(

---

### Post by 02.R1 on 2011-07-03
That worked thanks for your help. I just have one more quick question, I was trying to set it up on my plasma via HDMI and it comes up on the screen it's just too big and I set the resolution to a smaller size and it still doesn't fit is there a fix for this? Thanks

---

### Post by Rubi1200 on 2011-07-03
Great! I am really pleased you got this sorted out and I apologize for the error leaving out gedit in the command. 

Thanks to oldos2er for spotting that!

---

### Post by oldos2er on 2011-07-03
No problem. It's nice to know I'm not the only person who makes the occasional mistake.  :)

---

### Post by CatKiller on 2011-07-03
> **02.R1 said:**
> That worked thanks for your help. I just have one more quick question, I was trying to set it up on my plasma via HDMI and it comes up on the screen it's just too big and I set the resolution to a smaller size and it still doesn't fit is there a fix for this? Thanks

New thread for a different problem. People who know how to fix that kind of thing are unlikely to look at a thread about something completely different.

Don't forget to mark this thread as Solved.

---

