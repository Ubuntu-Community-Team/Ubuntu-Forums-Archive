---
title: "Failed to download repository information."
date: 2011-05-07
forum: General Help
---

### Post by leon.vitanos on 2011-05-07
```
W:Failed to fetch http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/natty/main/source/Sources  404  Not Found
, W:Failed to fetch http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/natty/main/binary-i386/Packages  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```I just have this message everytime i try to update and also at the systray every hour or something.. What can i do?

---

### Post by matt_symes on 2011-05-07
Hi

Have a look at this link

[http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/](http://ppa.launchpad.net/fredp/ppa/ubuntu/dists/)

As you will see, there is no natty distribution there hence your error.

To remove the error please post the output of

```
cat /etc/apt/sources.list
```

Please post the output between code tags.

Kind regards

---

### Post by leon.vitanos on 2011-05-07
```
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ natty main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gr.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gr.archive.ubuntu.com/ubuntu/ natty universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty universe
deb http://gr.archive.ubuntu.com/ubuntu/ natty-updates universe
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gr.archive.ubuntu.com/ubuntu/ natty multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty multiverse
deb http://gr.archive.ubuntu.com/ubuntu/ natty-updates multiverse
deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://gr.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb-src http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://security.ubuntu.com/ubuntu natty-security universe
deb-src http://security.ubuntu.com/ubuntu natty-security universe
deb http://security.ubuntu.com/ubuntu natty-security multiverse
deb-src http://security.ubuntu.com/ubuntu natty-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu natty main
deb-src http://extras.ubuntu.com/ubuntu natty main


```

I didn't catch what point you want from the output so here it is all of it.. :-k

---

### Post by matt_symes on 2011-05-07
Hi

The offending lines are not in your sources.list file. This means they will be in one of the sub files. Please of the output of

```
ls -l /etc/apt/sources.list.d/
```

That is a small L after ls above.

Also please post the output of

```
grep "ppa.launchpad.net/fredp" /etc/apt/sources.list.d/*
```

Kind regards

---

### Post by leon.vitanos on 2011-05-07
Ok.. So outpout of ```
ls -l /etc/apt/sources.list.d/
``````
total 28
-rw-r--r-- 1 root root 146 2011-04-29 23:53 caffeine-developers-ppa-natty.list
-rw-r--r-- 1 root root 146 2011-04-29 23:53 caffeine-developers-ppa-natty.list.save
-rw-r--r-- 1 root root 118 2011-04-29 23:53 fredp-ppa-natty.list
-rw-r--r-- 1 root root 118 2011-04-29 23:53 fredp-ppa-natty.list.save
-rw-r--r-- 1 root root 120 2011-04-29 23:53 lookit-ppa-natty.list
-rw-r--r-- 1 root root 120 2011-04-29 23:53 lookit-ppa-natty.list.save
-rw-r--r-- 1 root root 156 2011-04-29 23:53 the-board-team-dev-snapshots-natty.list

```And from 
```
grep "ppa.launchpad.net/fredp" /etc/apt/sources.list.d/*
``````
/etc/apt/sources.list.d/fredp-ppa-natty.list:deb http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
/etc/apt/sources.list.d/fredp-ppa-natty.list:deb-src http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
/etc/apt/sources.list.d/fredp-ppa-natty.list.save:deb http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
/etc/apt/sources.list.d/fredp-ppa-natty.list.save:deb-src http://ppa.launchpad.net/fredp/ppa/ubuntu natty main
```

---

### Post by matt_symes on 2011-05-07
Hi

Open a terminal and type

```
sudo rm /etc/apt/sources.list.d/fredp-ppa*
```

Enter your password. It will not be echoed to the screen. This is normal.

Then run

```
sudo apt-get update
```

Kind regards

---

### Post by leon.vitanos on 2011-05-07
Yes i know about sudo xD

Ok no errors now.. Thanks a lot..

---

### Post by denvella on 2011-05-10
I have the same problem here but with a slight difference when I tried out all of the above steps and arrived at 

ls -l /etc/apt/sources.list.d/
The results are 

total 0
[FONT=monospace]
When I tried this code 

[/FONT]grep "ppa.launchpad.net/fredp" /etc/apt/sources.list.d/*
[FONT=monospace]The result was this

grep: /etc/apt/sources.list.d/*: No such file or directory


Any help of what can I do please?

Thanks
[/FONT]

---

### Post by matt_symes on 2011-05-10
Hi

> **denvella said:**
> I have the same problem here but with a slight difference when I tried out all of the above steps and arrived at 

ls -l /etc/apt/sources.list.d/
The results are 

total 0
[FONT=monospace]
When I tried this code 

[/FONT]grep "ppa.launchpad.net/fredp" /etc/apt/sources.list.d/*
[FONT=monospace]The result was this

grep: /etc/apt/sources.list.d/*: No such file or directory


Any help of what can I do please?

Thanks
[/FONT]

So i can see the exact error message, can you post the error for the last couple of lines from

```
sudo apt-get update
```Also, what version of Ubuntu are you using ?

Can you also post the output of

```
ls /etc/apt
```

Kind regards

---

