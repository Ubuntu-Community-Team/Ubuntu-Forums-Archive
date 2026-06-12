---
title: "can't access synaptic package manager"
date: 2010-10-23
forum: General Help
---

### Post by poker2 on 2010-10-23
hi,
i don't know if someone can help me, i am unable to open package manager or install any software, each time i try it brings up this message


E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

don't know what else to do. would really appreciate any help I can get.

thanks.

---

### Post by Jebtrix on 2010-10-23
If your using 10.10 here is a working sources.list

Just do:

gksudo gedit /etc/apt/sources.list

And replace the contents with this and save

```
# 

deb http://archive.ubuntu.com/ubuntu maverick main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu maverick-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick universe
deb-src http://archive.ubuntu.com/ubuntu maverick universe
deb http://archive.ubuntu.com/ubuntu maverick-updates universe
deb-src http://archive.ubuntu.com/ubuntu maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu maverick multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick multiverse
deb http://archive.ubuntu.com/ubuntu maverick-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu maverick-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://archive.ubuntu.com/ubuntu maverick-security main restricted
deb http://archive.ubuntu.com/ubuntu maverick-security universe
deb-src http://archive.ubuntu.com/ubuntu maverick-security universe
deb http://archive.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://archive.ubuntu.com/ubuntu maverick-security multiverse

```

---

### Post by poker2 on 2010-10-23
I think am running a 10.04 will that still work with it

---

### Post by sikander3786 on 2010-10-23
If you have added some custom repositories/PPAs, it would be better to post the output of

```
cat /etc/apt/sources.list
```

So we can find the malformed lines.

If it is the default one, you can replace with the one provided in above post.

---

### Post by sikander3786 on 2010-10-23
> **poker2 said:**
> I think am running a 10.04 will that still work with it
No it wouldn't. Post the output of

```
cat /etc/apt/sources.list
```

---

### Post by poker2 on 2010-10-23
it gives me something like this.

poker@Pokers-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu-Netbook 10.04 _Lucid Lynx_ - Release i386 (20100429.4)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb United Kingdom lucid main restricted
deb-src United Kingdom lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb United Kingdom lucid-updates main restricted
deb-src United Kingdom lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb United Kingdom lucid universe
deb-src United Kingdom lucid universe
deb United Kingdom lucid-updates universe
deb-src United Kingdom lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb United Kingdom lucid multiverse
deb-src United Kingdom lucid multiverse
deb United Kingdom lucid-updates multiverse
deb-src United Kingdom lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb United Kingdom lucid-security main restricted
deb-src United Kingdom lucid-security main restricted
deb United Kingdom lucid-security universe
deb-src United Kingdom lucid-security universe
deb United Kingdom lucid-security multiverse
deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main multiverse universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security main multiverse restricted universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main multiverse restricted universe
deb-src United Kingdom lucid-security multiverse
poker@Pokers-laptop:~$

---

### Post by sikander3786 on 2010-10-23
Your sources.list is all messed up. Instead of working hard on it, I'll recommend it the way **Jebtrix** mentioned above.

Backup your messed up sources.list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bad
```

Edit it

```
gksudo gedit /etc/apt/sources.list
```

Delete everything and pop this in. It is a default one for Lucid.

```
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)]/ lucid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://pk.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://pk.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner

deb http://archive.ubuntu.com/ubuntu lucid main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ lucid-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu lucid-updates universe main multiverse restricted
```

Save and close.

Now try,

```
sudo apt-get update
```

Is it sorted now?

---

### Post by poker2 on 2010-10-23
when i try it gives me this message.

[sudo] password for poker:

if i try to put in a password it says sorry try again

---

### Post by Jebtrix on 2010-10-23
In case you need to reset password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by SavageWolf on 2010-10-23
Make sure it's your password.

---

### Post by poker2 on 2010-10-23
yes its done now that was really helpful 
thanks a lot for your assitance

---

### Post by sikander3786 on 2010-10-23
> **poker2 said:**
> yes its done now that was really helpful 
thanks a lot for your assitance
What was wrong with the password?

Were you confused with nothing showing up (asterisks) in the terminal when you typed it?

If it gets messed up again for any reasons, you can use this link to generate a new one for any release.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by poker2 on 2010-10-23
yeah I was confused when nothing was showing, so I tried to change the password through the link you supplied and it said nothing would show. so I went back and used the old password and it worked fine

---

