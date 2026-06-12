---
title: "Right Click Issues - Menu Location"
date: 2010-12-23
forum: General Help
---

### Post by TWK1a4 on 2010-12-23
Hey all,

     To start off, I'm a long time CMD line Linux user but fresh to Ubuntu.  I have searched long and hard for a solution to my issue but, my problem persists...

1: I have a (mental) issue with mashing the right-click button to check the laggyness of my computer.  With Windows 7 if you right-click multiple times, the (right-click) options menu just reappears.   In Ubuntu, when you right-click, the cursor is highlighted over the first menu option which is 'back' in a web browser and 'create folder' on the desktop.  This means when I right click in the same location twice, the first menu option is executed which is driving me crazy!  
     So, is there any way to change the location of where the right-click menu pops up relative to the cursor, so I don't have this annoyance? 
     And, is there a way to set the right-click menu to pop up wherever I right-click, as opposed to just toggling it? 


2: (Should be a one liner) I installed Ubuntu 10.04 but I clicked on my System's About tab and I'm somehow running 11.04 Natty Narwhal, which "was(?!) released in April 2011".  (I gotta stop getting black-out-drunk and using my time machine...) Did I install an alpha release inadvertently through updates?

     Thanks for your time,
     TWeeK

---

### Post by djeikyb on 2010-12-24
1. Haha, you want Ubuntu's context menu to be less usable. I recommend developing a different tic.

2. Yes. Confirm with uname -a. But you (leastwise, someone) would've had to add the repositories.

---

### Post by TWK1a4 on 2010-12-24
Grr (djeikyb), and to think someone found a solution to my insanity so quickly...
 
1) I can't get rid of this tic!  Microsoft ruined me with their OS's freezing and lagging 24/7.

2) uname -a does not display Ubuntu version...  I just insatlled 10.04 a week or so ago and have been blindly updating when the OS prompts me.  Probably a bad habit.

---

### Post by djeikyb on 2010-12-24
1. Set xeyes full-screened as the wallpaper (or be boring and add it to the panel). You'll see any lag.

2. It gives you the codename and kernel, which you can check against the documentation. Also, cat /etc/lsb-release

---

### Post by TWK1a4 on 2010-12-24
1) I'm loony.

2) cat /etc/lsb-release:
twk@nicholas-LapTop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
twk@nicholas-LapTop:~$ 

System->About Ubuntu: 
You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.
	
I'm just down right confused now...  I installed 10.04 but I'm running 10.10 and 11.04?

---

### Post by akand074 on 2010-12-24
> **TWK1a4 said:**
> 1) I'm loony.

2) cat /etc/lsb-release:
twk@nicholas-LapTop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"
twk@nicholas-LapTop:~$ 

System->About Ubuntu: 
You are using Ubuntu 11.04 - the Natty Narwhal - released in April 2011 and supported until October 2012.
    
I'm just down right confused now...  I installed 10.04 but I'm running 10.10 and 11.04?

11.04 still uses a lot of 10.10 files/settings. Hence, it sometimes states your running 10.10, when really your running 11.04. This is because 11.04 is still in the Alpha stage of it's release and highly unstable. It's just for testing purposes, so that is a problem. Do a clean install of 10.04 or 10.10, I wouldn't use the upgrade option in the future, it only causes problems.

---

### Post by djeikyb on 2010-12-24
1. Bind your right-click button to something more useful to you than a well-placed context menu. Or maybe you could keep the context menu but add a sound.

Loony? Did you run xeyes?

---

### Post by satish_j on 2010-12-24
Iam also facing this annoying issue in Ubuntu.i managed to shift the menu items down in right-click context menu.Below link may be of some help..
[http://ubuntuforums.org/showthread.php?t=1608564]("http://ubuntuforums.org/showthread.php?t=1608564")

---

### Post by matt_symes on 2010-12-24
Hi


> 2: (Should be a one liner) I installed Ubuntu 10.04 but I clicked on my System's About tab and I'm somehow running 11.04 Natty Narwhal, which "was(?!) released in April 2011". (I gotta stop getting black-out-drunk and using my time machine...) Did I install an alpha release inadvertently through updates?

It sounds like you installed alpha 1 or a daily build. What download link did you use?

This is the link you want

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Kind regards

---

### Post by TWK1a4 on 2010-12-24
@satish_j - That looks like something I can work with.  I'll have to investigate it more tomorrow when I have more time.  It seems like our issue a unique combination of hardware and user (Thanks Microsoft for giving us mental disorders). 

@matt_symes - I have only ever used the "Ubuntu software update manager" or whatever the automatic update manager is called.  I don't know the proper name is but it pops up when there are installed apps/programs that need updating.  When ever you install a new OS there are a ton of updates for the OS and installed programs.  I only ever glance over them considering there were 1200 the day I installed 10.04!  I searched through them and can't find and can't find anything relating to "11.04", "natty", or "narwhal".  I can't figure out when I did this...

     -TWeaK

---

### Post by matt_symes on 2010-12-24
Hi

What kernel release do you have?

```
uname -r
```

can you also post the output of 

```
cat /etc/apt/sources.list
```

Kind regards

---

### Post by JPWhite on 2010-12-30
> **TWK1a4 said:**
> @satish_j - That looks like something I can work with.  I'll have to investigate it more tomorrow when I have more time.  It seems like our issue a unique combination of hardware and user (Thanks Microsoft for giving us mental disorders). 

@matt_symes - I have only ever used the "Ubuntu software update manager" or whatever the automatic update manager is called.  I don't know the proper name is but it pops up when there are installed apps/programs that need updating.  When ever you install a new OS there are a ton of updates for the OS and installed programs.  I only ever glance over them considering there were 1200 the day I installed 10.04!  I searched through them and can't find and can't find anything relating to "11.04", "natty", or "narwhal".  I can't figure out when I did this...

     -TWeaK

Same here. I didn't knowingly upgrade to an alpha release I also use Update Manager, its set to get 'Normal Releases'

---

### Post by mc4man on 2010-12-30
> I didn't knowingly upgrade to an alpha release
The System - About Ubuntu showing 11.04 (natty) in 10.10 (maverick) is a known mistake

---

### Post by JPWhite on 2010-12-30
> **matt_symes said:**
> Hi

What kernel release do you have?

```
uname -r
```

can you also post the output of 

```
cat /etc/apt/sources.list
```

Kind regards

I'm having the same issues with 11.04 reported as my current release in 'System --> About Ubuntu'. I believe I should have 10.10. Here is the output from the commands you suggest.

```

jpwhite@jpwhite-laptop:~$ uname -r
2.6.35-24-generic
jpwhite@jpwhite-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu karmic partner
# deb-src http://archive.canonical.com/ubuntu karmic partner

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse
# deb http://ppa.launchpad.net/arzajac/ppa/ubuntu maverick main # disabled on upgrade to maverick
# deb http://download.virtualbox.org/virtualbox/debian lucid non-free # disabled on upgrade to lucid
deb http://extras.ubuntu.com/ubuntu maverick main #Third party developers repository


```

---

### Post by JPWhite on 2010-12-30
> **mc4man said:**
> The System - About Ubuntu showing 11.04 (natty) in 10.10 (maverick) is a known mistake

OK Thanks for the quick response. I'll ignore it :-)

---

### Post by matt_symes on 2010-12-30
Hi

> **mc4man said:**
> The System - About Ubuntu showing 11.04 (natty) in 10.10 (maverick) is a known mistake

> **JPWhite said:**
> OK Thanks for the quick response. I'll ignore it :-)

Yes. Sorry about that. I was not aware of the bug at that time. 

Here is the link

[https://bugs.launchpad.net/ubuntu/+bug/694558](https://bugs.launchpad.net/ubuntu/+bug/694558)

Kind regards

---

