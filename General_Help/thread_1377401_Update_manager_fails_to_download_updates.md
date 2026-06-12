---
title: "Update manager fails to download updates"
date: 2010-01-10
forum: General Help
---

### Post by Eyeyseeh39 on 2010-01-10
I recently installed Ubuntu 9.10 on an old computer I had lying around and have been pleasantly surprised by it.
I had a small problem with firefox not connecting to the internet but I managed to fix this by disabling ipv6 in about:config.
The problem I now have is that update manager fails to download updates and gives a message saying failed to fetch several files.
I'm connected to the internet via a wired router.
I'm a complete novice to Ubuntu so be gentle with me when answering as it will have to be simple for me to understand! :-) 

Cheers

Iain

---

### Post by zvacet on 2010-01-10
Type in terminal

```
sudo apt-get update && sudo apt-get upgrade
```

If that doesn´t help go to the system<admin<software sources and check all under ubuntu software and first two under updates tab.Reload.In system>admin>software sources you can also change server and try another one if all above fail.

---

### Post by Eyeyseeh39 on 2010-01-10
OK thanks for the advice but it hasnt sorted the problem, I still get almost 100 messages similar to this one

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101: Network is unreachable)

Hope someone can help!

Cheers

Iain

---

### Post by stoneage on 2010-01-10
I think the problem is that file doesn't exist in the archive:-
[http://archive.ubuntu.com/ubuntu/pool/main/p/python2.6/](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.6/)

The nearest equivalent is libpython2.6_2.6.4-0ubuntu3_i386.deb

I guess it has been superseded. What are you updating, and can you post the results of > gksudo gedit /etc/apt/sources.list ?

---

### Post by Eyeyseeh39 on 2010-01-10
Hi Stoneage

When I open update manager it gives me a list of 87 recommended updates, these are the files I'm attempting to download.

Here is the output you asked for,

# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security restricted main multiverse universe #Added by software-properties
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse


Hope this helps

Cheers

Iain.

---

### Post by stoneage on 2010-01-10
I was hoping it would, but those are all karmic sources, so it isn't that.


I'm afraid I don't know what it might be, that file seems to be from the  Karmic Proposed Repository:-
[https://launchpad.net/ubuntu/karmic/i386/libpython2.6/2.6.4-0ubuntu2](https://launchpad.net/ubuntu/karmic/i386/libpython2.6/2.6.4-0ubuntu2)

Have you installed anything manually, or did you have the proposed repo enabled earlier(on the Updates tab on System -> Admin -> Software Sources)?

It might help if you list some of the other not-found files.... I'm confused :)

---

### Post by Soweto on 2010-01-21
> **Eyeyseeh39 said:**
> OK thanks for the advice but it hasnt sorted the problem, I still get almost 100 messages similar to this one

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu2_i386.deb)
  Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (101: Network is unreachable)

Hope someone can help!

Cheers

Iain

I'm also new to Linux. I got this message while trying to update my software. After trying several things I realized that my firewall was blocking me. The updates are going thru after "fixing" the firewall. You might need to check this as well... hope it helps

---

### Post by smossbarger on 2010-01-30
Please see:  [http://www.linuxforums.org/forum/ubuntu-help/157482-solved-cannot-update-install-programs-through-synaptic-2.html](http://www.linuxforums.org/forum/ubuntu-help/157482-solved-cannot-update-install-programs-through-synaptic-2.html)

---

