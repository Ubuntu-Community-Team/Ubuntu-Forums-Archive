---
title: "Synaptic Package Manager Problem"
date: 2010-01-30
forum: General Help
---

### Post by Ruskiy Letenant on 2010-01-30
I got this code:

     E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/
     sources.list.d/playonlinux.list
     E: The list of sources could not be read.
     Go to the repository dialog to correct the probem.
     E: _cache->open() failed, please report.

What is the repos system...Need some help here.

---

### Post by Ruskiy Letenant on 2010-01-30
Im trying to follow this link, [http://ubuntuforums.org/showthread.php?t=731293&highlight=Conquer+Online](http://ubuntuforums.org/showthread.php?t=731293&highlight=Conquer+Online)

to install conquer online, and im not sure how to even follow those instructions. Ive been looking everywhere to find a way to make it work. The main problem seems to be the DirectX 9 requirement for the game. I hear that you dont need it, you need POL, well, thats where the problem is.

---

### Post by MelDJ on 2010-01-30
could you post the output of
```
gedit /etc/apt/sources.list
```

---

### Post by stoneage on 2010-01-30
Did you manually edit your sources.list at any time?

Post the result of ```
gksudo gedit /etc/apt/sources.list
```


EDIT - Ooops...... oldos2er is likely correct. (Must read more carefully)

Ruskiy Letenant, you need to use a simple text editor, one that doesn't store formatting information, such as kate or gedit.

---

### Post by oldos2er on 2010-01-30
Can you post the output of **cat /etc/apt/sources.list.d/playonlinux.list** ?

---

### Post by Ruskiy Letenant on 2010-01-30
> **MelDJ said:**
> could you post the output of
```
gedit /etc/apt/sources.list
```
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Ruskiy Letenant on 2010-01-30
> **stoneage said:**
> Did you manually edit your sources.list at any time?

Post the result of ```
gksudo gedit /etc/apt/sources.list
```
EDIT - Ooops...... oldos2er is likely correct. (Must read more carefully)

Ruskiy Letenant, you need to use a simple text editor, one that doesn't store formatting information, such as kate or gedit.

No, didnt touch anything. One thing i installed through terminal was POL.

OUTPUT:
#deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

---

### Post by Ruskiy Letenant on 2010-01-30
> **oldos2er said:**
> Can you post the output of **cat /etc/apt/sources.list.d/playonlinux.list** ?

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<noscript>
<meta http-equiv="refresh" content="0;url=http://finder.cox.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=96e687opkbv4scrood8k84drs6gw5duf&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fplayonlinux.botux.net%2Fplayonlinux_hardy.list&AddInType=4&Version=2.1.1-1.62base&Referer=&Implementation=0"/>
</noscript>
<script type="text/javascript">
window.location.replace("http://finder.cox.net/main?InterceptSource=0&ClientLocation=us&ParticipantID=96e687opkbv4scrood8k84drs6gw5duf&FailureMode=1&SearchQuery=&FailedURI=http%3A%2F%2Fplayonlinux.botux.net%2Fplayonlinux_hardy.list&AddInType=4&Version=2.1.1-1.62base&Referer=&Implementation=0");
</script>
</head>
<body>
</body>
</html>vladimir@VDB:~$

---

### Post by Ruskiy Letenant on 2010-01-30
Im positive its something to do with my failed attempt with POL, I really appreciate the help by the way!

---

### Post by oldos2er on 2010-01-30
That file is fubared. Run these commands one at a time: ```
sudo rm /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
```

Here are some simple instructions to get playonlinux: [http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

---

### Post by Ruskiy Letenant on 2010-01-30
You are a genius, thank you...FIXED

---

### Post by oldos2er on 2010-01-30
No genius, I assure you. You're welcome.  :)

---

### Post by Ruskiy Letenant on 2010-01-30
Well, the package manager is working great, and I've installed POL, but now I need one more pit of advice into deciphering these instructions:

[http://ubuntuforums.org/showthread.php?t=731293&highlight=Conquer+Online](http://ubuntuforums.org/showthread.php?t=731293&highlight=Conquer+Online)

---

### Post by oldos2er on 2010-01-30
I don't use playonlinux, so I don't know much about it. If you post exactly what you tried and where it's going wrong, maybe someone else will jump in to help. Or try the gaming subforum: [http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

---

