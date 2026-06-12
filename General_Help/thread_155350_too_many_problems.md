---
title: "too many problems"
date: 2006-04-04
forum: General Help
---

### Post by wcks48 on 2006-04-04
mu kubuntu not stable as i heard and seen from. firstly is after the download of macromedia flash plug-in for mozilla, can't open it anymore.Second problem is can't let adept or automatix download the driver for my wifi card. third, the worst is kubuntu can't load Adept. 

could someone tell me what's wrong with my system? could i insert the kubuntu CD to reinstall the system to recover it to initial state, or would it destroy all my downloaded packages? Thanks for your help. I am still thinking the stable of linux always better than other OS...

---

### Post by wcks48 on 2006-04-04
when i run commnad apt-get update in terminal, i got the error msg:
E: Malformed line 36 in source list /etc/apt/sources.list (dist parse)

so, what error in line 36 of source list?
could anybody let me copy their working source list? thanks

---

### Post by Ptero-4 on 2006-04-04
Can you post your messed up sources.list? I ask b/c if your sources.list had special repos, copying over someone elses sources.list can screw up apt with missing or invalid repos (specially true for cross architecture situations).

---

### Post by wcks48 on 2006-04-05
well, my line 36 of the source.list is noted with something about "wine".

here's the content.

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
## deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free

deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) etch non-free

deb [http://kubuntu.org/packages/kde351](http://kubuntu.org/packages/kde351) breezy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/
deb-src [http://koti.mbnet.fi/~ots/ubuntu/](http://koti.mbnet.fi/~ots/ubuntu/) breezy/

deb [http://theli.free.fr/packages/breezy/](http://theli.free.fr/packages/breezy/) ./
## created by arnielistenadded


deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) breezy main restricted

deb [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://my.archive.ubuntu.com/ubuntu/](http://my.archive.ubuntu.com/ubuntu/) breezy main restricted


but if i need to change the content, how should i do? coz the changing only allowed for root access. but even i sign in as root, i can't get up the Kdesktop with command "Startx". tha's my another problem since days before. 

any idea for my big problem? or should i try to reinstall the whole kubuntu?

---

### Post by murph2481 on 2006-04-05
Comment out the line:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

to do this open up a console and type:

```
sudo vi /etc/apt/sources.list
```

Scroll down to the line that is the problem, then press i, then add a # infront of the line press escape then type x and press enter.  Then try apt-get update again.

---

### Post by tagg3rx on 2006-04-05
hehe sending somneone into vi without the commands is mean
[http://www.chem.brown.edu/instructions/vi.html](http://www.chem.brown.edu/instructions/vi.html)

sudo kedit /etc/apt/sources.list 

Or just open up synatpic and go to settings repositories
and remove wine

---

### Post by gingermark on 2006-04-05
[QUOTE=tagg3rx]hehe sending somneone into vi without the commands is mean
[http://www.chem.brown.edu/instructions/vi.html](http://www.chem.brown.edu/instructions/vi.html)

sudo kedit /etc/apt/sources.list 

Or just open up synatpic and go to settings repositories
and remove wine[/QUOTE]
Telling a newbie Kubuntu user to use Kedit and Synaptic is also mean! (neither are installed by default).

Do 'kdesu kate /etc/apt/sources.list' or use Adept.

---

### Post by wcks48 on 2006-04-05
Thanks to all comments and suggestions, but due to my actual problem was can't load the Adept, so the resipotories changing via adept is not functionable. however, i had remove the wine (line 36) via nano in console. and finally, eveything runs well. 

But am i lost the update repository of Wine? how would i add it back again with the correct one? 

one more question, any files such as sources.list for mozilla? coz my mozilla & firefox can't load, may it caused by profile setting problems?

---

### Post by gingermark on 2006-04-05
wcks48, please open up konsole and type "firefox" and post the output. It is likely to help others to properly diagnose the problem.

---

### Post by wcks48 on 2006-04-05
the message appeared on the console is:

wcks48@ubuntu:~$ firefox
Bus error
wcks48@ubuntu:~$

Is it a bug or just some error with the installation of flash plug in?

---

### Post by wcks48 on 2006-04-05
i tried kdesu firefox.
no problem to load it. but of coz all of the profile and history inside is what i had going through while using the firefox as root user.

---

