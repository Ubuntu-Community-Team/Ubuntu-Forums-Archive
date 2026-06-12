---
title: "E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)"
date: 2010-06-25
forum: General Help
---

### Post by Tam077 on 2010-06-25
Hi, I realise this sort of problem has been posted before but I cannot find anything that helps me resolve it.

I get this error message
E: Malformed line 57 in source list /etc/apt/sources.list (dist parse)

I am pretty new to Ubuntu and dont really understand computer talk can anyone help me fix this please??  here is the sources list (??) as well  :confused:

Thanks heaps!!

tammy@tammy-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

---

### Post by 3rdalbum on 2010-06-25
Count down to Line 57 of the /etc/apt/sources.list file. Take a look at it. It's malformed/misformed/incorrect.

This is line 57: 
deb [http://archive.canonical.com/lucid](http://archive.canonical.com/lucid) partner

Just delete it from the file. The correct entry for it is already in the file (several times, in fact; you should delete the duplicates too).

In order to modify the file, remember you'll need to open it as root with the following command:

```
gksudo gedit /etc/apt/sources.list
```

After bringing this file back to normal, run:

```
sudo apt-get update
```

And in future don't edit the file directly. Use System > Administration > Software Sources instead, because it prevents these sorts of problems from occurring (it will not allow you to add a line to the file that is malformed).

---

### Post by Tam077 on 2010-06-25
Thank you, I did that and I think it has worked, how can I tell?? Please forgive my ignorance as I said before I'm new to Ubuntu and Im worried about making a mistake.

Also should this have fixed the following error I get with package installer??

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

---

### Post by plucky on 2010-06-25
```
deb http://archive.canonical.com/  lucid partner
deb http://archive.canonical.com/ lucid partner
deb http://archive.canonical.com/ lucid partner
deb http://archive.canonical.com/lucid partner 
```

Remove all 4 of those lines as they are incorrect.

And if you need the partner repository, remove the # from this line ```
# deb http://archive.canonical.com/ubuntu  lucid partner
```

Then run ```
sudo apt-get update
``` and if there are no errors you will be good to go.

Good Luck

---

### Post by devias on 2011-10-18
i only count 51 lines

---

