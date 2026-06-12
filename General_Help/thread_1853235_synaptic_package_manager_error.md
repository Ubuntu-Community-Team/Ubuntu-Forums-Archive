---
title: "synaptic package manager error"
date: 2011-10-01
forum: General Help
---

### Post by mozozo4 on 2011-10-01
Hi, i don't know what happened. My synaptic package manager was working before but know it gives me this error
i try to open synaptic package manager, but it gives me an error and it doesn't let me open it


E: Type '“deb' is not known on line 55 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

can someone please help me

---

### Post by papibe on 2011-10-01
Hi mozozo4,

Could you post the content of that file (/etc/apt/sources.list)?

Regards.

---

### Post by mozozo4 on 2011-10-01
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
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
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) natty main #Third party developers repository
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security multiverse
“deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main”

---

### Post by dFlyer on 2011-10-01
remove the quotation marks around this entry as sudo

“deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main”

than run sudo apt-get update

---

### Post by Enigmapond on 2011-10-01
Yes so do do that, open the terminal and do:

```
gksu gedit /etc/apt/sources.list
```

Scroll to the bottom entry and remove the quotes...save and exit.

Now run the update again,,as advised.

Cheers!

---

### Post by papibe on 2011-10-01
> **mozozo4 said:**
> **[COLOR="Red"]“[/COLOR]**deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free main[COLOR="Red"]**”**[/COLOR]
There's a wrong quotes (") in the last line. You have to remove them. Here's a way to do it:
```
$ gksudo gedit /etc/apt/sources.list
```
Your password will be asked, and then very careful go to the end of the file, and remove the quotes at the beginning and end of the line.

Save the file, close the editor. Before going to synaptic I would update:
```
$ sudo apt-get update
```
I hope it helps,
Regards.

---

### Post by mozozo4 on 2011-10-01
thank you so much for the help

i was wondering since my ubuntu is so slow 

how do i get ubuntu 2d?
and does compiz work with ubuntu 2d?

by the way thank you again

---

### Post by papibe on 2011-10-01
I would recommend marking this thread solved, and opening a new thread to take care of that concern (one that have a title that attract the right people to it).

Regards.

---

### Post by wildmanne39 on 2011-10-01
Hi, to answer your question it will work but it will be flat will be flat in 2d, but you can install unity 2d from from software center or synaptic.
There maybe away to fix your slowness, but you do need to mark this thread solved as suggested and start a new one with a good title so you can get help with that issue.
Thank you

---

