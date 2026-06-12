---
title: "confused"
date: 2009-08-29
forum: General Help
---

### Post by xdweaver on 2009-08-29
Okay i have installed ubuntu studio 9.04. i have tried to run the update manager and i get this error,

 E:Type '[...]' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read

I don't know what i did wrong. and have not a clue to fix it. It also says that even when i try to add the [Medibuntu repository]("http://www.medibuntu.org/"). 

I have ran the sudo gedit /etc/apt/sources.list. This is what i get:


...]
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[...]# 
# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main sudo gedit /etc/apt/sources.list


Not sure what is wrong. PLEASE HELP!!!!!! PLEASE

---

### Post by overdrank on 2009-08-29
> **xdweaver said:**
> Okay i have installed ubuntu studio 9.04. i have tried to run the update manager and i get this error,

 E:Type '[...]' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read

I don't know what i did wrong. and have not a clue to fix it. It also says that even when i try to add the [Medibuntu repository]("http://www.medibuntu.org/"). 

I have ran the sudo gedit /etc/apt/sources.list. This is what i get:

[COLOR="Red"]
...][/COLOR]
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[...]# 
# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main sudo gedit /etc/apt/sources.list


Not sure what is wrong. PLEASE HELP!!!!!! PLEASE

Hi and delete what I have highlighted in red and save. Then update and try again.

---

### Post by xdweaver on 2009-08-29
Okay i did delete what you highlighted in red. And tried to update and now get this:

'E:Type '[...]' is not known on line 8 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

So i did the sources.list and this is what i get:

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[...]# 
# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main sudo gedit /etc/apt/sources.list

---

### Post by overdrank on 2009-08-29
> **xdweaver said:**
> Okay i did delete what you highlighted in red. And tried to update and now get this:

'E:Type '[...]' is not known on line 8 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

So i did the sources.list and this is what i get:

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
[COLOR="Red"][...]# [/COLOR]
# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main sudo gedit /etc/apt/sources.list

What I have highlighted now is causing the issues. Is this the whole list?
Post the output of the command ```
cat /etc/apt/sources.list

```
In your other [thread ]("http://ubuntuforums.org/showthread.php?t=1252926") I see you were having issues with adding a repo, did you delete any of your list while doing so?

---

### Post by xdweaver on 2009-08-29
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

# deb cdrom:[Ubuntu-Studio 9.04 _Jaunty Jackalope_ - Release i386 (20090421.4)]/ jaunty main sudo gedit /etc/apt/sources.list

---

### Post by xdweaver on 2009-08-29
that was it.. thank you so much

---

### Post by overdrank on 2009-08-29
> **xdweaver said:**
> that was it.. thank you so much

Yes but you are missing several repos in your list. 
```

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted

# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release amd64 (20090420.1)]/ jaunty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

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
# deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu jaunty partner

deb http://security.ubuntu.com/ubuntu jaunty-security main restricted
deb-src http://security.ubuntu.com/ubuntu jaunty-security main
deb http://security.ubuntu.com/ubuntu jaunty-security universe
deb-src http://security.ubuntu.com/ubuntu jaunty-security universe


```As you can see this is my list, I do believe it will work with your system as I am using 64bit and was looking for the standard Jaunty repository list and have not located it. :)

---

