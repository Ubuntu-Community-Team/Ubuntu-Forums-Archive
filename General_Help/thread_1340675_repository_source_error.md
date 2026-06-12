---
title: "repository source error"
date: 2009-11-28
forum: General Help
---

### Post by nikhilvasista on 2009-11-28
hi, i very much new to linux(jaunty 9.04). i have been getting this error lately when click on add/remove programs
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
also 
E: Type 'wget' is not known on line 53 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

i am also unable to update.so i request u all to help me in this regard.thanks in advance.
nikhil

---

### Post by audiomick on 2009-11-28
the first thing is to do what it says.
open a terminal, applications> accessories> terminal

and type

```
sudo apt-get update
```

it will ask you for a password. This is the one you use to log on.
Let it do that, then, in the terminal, type

```
sudo apt-get install -f
```

That might have fixed your problem.

---

### Post by bluestar14 on 2009-11-28
i had a similar problem, and since i just installed it, i just reinstalled ubuntu

---

### Post by nikhilvasista on 2009-11-28
i did.but then i get the following 
nikhilvasista@ubuntu:~$ sudo apt-get update
[sudo] password for nikhilvasista: 
E: Type 'wget' is not known on line 53 in source list /etc/apt/sources.list
nikhilvasista@ubuntu:~$ sudo apt-get install -f
E: Type 'wget' is not known on line 53 in source list /etc/apt/sources.list
E: The list of sources could not be read.
nikhilvasista@ubuntu:~$
i am unable to update also

---

### Post by plucky on 2009-11-29
> E: Type 'wget' is not known on line 53 in source list /etc/apt/sources.list
E: The list of sources could not be read.

You have to fix line 53 in your sources list.

Open a terminal and ```
gksudo gedit /etc/apt/sources.list
```

and look for the line that begins with **wget** and put a # in front of it.It should be line 53.

Or 

Post the output of ```
cat /etc/apt/sources.list
``` to the forums so we can tell you what is wrong with your sources list. 


Good Luck

---

### Post by vinaypvk on 2010-12-03
im getting the error "**E: _cache->open() failed, please report."**
this is the output of  " gksudo gedit /etc/apt/sources.list"
can u tell me what the problem is????? THANKS in ADVANCE..............

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# deb cdrom:[APTonCD for ubuntu maverick - amd64 (2010-11-15 21:09) CD1]/ /
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by sikander3786 on 2010-12-03
> **vinaypvk said:**
> im getting the error "**E: _cache->open() failed, please report."**
this is the output of  " gksudo gedit /etc/apt/sources.list"
can u tell me what the problem is????? THANKS in ADVANCE..............

(This might be thread-hijacking but the I am sure the OP's problem is solved after following **plucky's** instructions so no harm in replying to another issue :-) )

Welcome to the forums :-)

Please try these commands from the terminal and post their complete outputs.

```
sudo apt-get clean
```

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

```
sudo apt-get update
```

While posting the output from Terminal, generate code tags by pressing # from the post menu and paste your text in between the generated tags. [/code] at the end and [code] at the beginning. It would be nice if you also edit your above post and type the codes as suggested here.

Thanks.

---

