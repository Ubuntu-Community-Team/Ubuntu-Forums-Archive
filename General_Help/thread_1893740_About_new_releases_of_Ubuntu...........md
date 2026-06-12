---
title: "About new releases of Ubuntu.........."
date: 2011-12-10
forum: General Help
---

### Post by pretty_whistle on 2011-12-10
Suppose I use Lubuntu right now.  How long is the support for it?

Another question:

When the next new LTS release comes out, which will be 12.04, will there be an LTS upgrade available for Lubuntu as well?

I looked here but am still uncertain:
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

At the above link, it says:
"The LTS may not apply to all editions and remixes of Ubuntu."
"The project will decide which editions will be LTS early in the LTS development cycle."

It says "...may not apply to all editions..."  May not?  Maybe, maybe not....So how do I find out for sure.

Does anyone know?

---

### Post by oldtimer7777 on 2011-12-10
Here is how I see it.

If Lubuntu is based on Ubuntu, and it is just a desktop environment.  And ubuntu rolls out an LTS and you install the Lubuntu Desktop Environment on top of LTS Ubuntu from the Lubuntu PPA, in essence you are running an LTS version of Lububu desktop environment. 

Here is the PPA for Lubuntu (for example):

```
sudo add-apt-repository ppa:lubuntu-desktop/ppa 
sudo apt-get update 
sudo apt-get install lubuntu-desktop
```Does that make sense now?

I hate doing upgrades from from version to the next.  It is always better to do a fresh installation and then install whatever desktop environment from the PPA you want to use.  Lubuntu is LXDE a desktop environment. It is using Ubuntu, so whatever Ubuntu updates/upgrades, it will roll along with it. 

> **pretty_whistle said:**
> Suppose I use Lubuntu right now.  How long is the support for it?

Another question:

When the next new LTS release comes out, which will be 12.04, will there be an LTS upgrade available for Lubuntu as well?

I looked here but am still uncertain:
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

At the above link, it says:
"The LTS may not apply to all editions and remixes of Ubuntu."
"The project will decide which editions will be LTS early in the LTS development cycle."

It says "...may not apply to all editions..."  May not?  So how do I find out for sure.

Does anyone know?

---

### Post by pretty_whistle on 2011-12-10
> **oldtimer7777 said:**
> Here is how I see it.

If Lubuntu is based on Ubuntu, and it is just a desktop environment.  And ubuntu rolls out an LTS and you install the Lubuntu Desktop Environment on top of LTS Ubuntu from the Lubuntu PPA, in essence you are running an LTS version of Lububu desktop environment. 

Does that make sense now?

I hate doing upgrades from from version to the next.  It is always better to do a fresh installation and then install whatever desktop environment from the PPA you want to use.
Excuse my noob question, but what is PPA?  I keep running into it while reading.

---

### Post by CryptAck on 2011-12-10
> **pretty_whistle said:**
> Excuse my noob question, but what is PPA?  I keep running into it while reading.
[PPA](https://help.launchpad.net/Packaging/PPA)

---

### Post by claracc on 2011-12-11
Lubuntu 12.04 will not be Long Term Support (LTS) release. Ubuntu 12.04 will be LTS though.

[http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)

> LTS :
Again, it's not a choice which depends on the users, but a decision made by the developers. Of course I would like to be LTS, like I would like to buy an expensive car. The fact is, we can't. And even if we try, it could be so expensive that it will block us to do new cool stuff, because we have to maintain 12.04.

---

### Post by oldtimer7777 on 2011-12-11
> **claracc said:**
> Lubuntu 12.04 will not be Long Term Support (LTS) release. Ubuntu 12.04 will be LTS though.

[http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)


If you install Lubuntu Desktop Environment on top of Ubuntu 12.04 LTS, you have a desktop environment that isn't LTS but the OS is LTS.  The question is slightly fallacious.

---

### Post by pretty_whistle on 2011-12-11
> **claracc said:**
> Lubuntu 12.04 will not be Long Term Support (LTS) release. Ubuntu 12.04 will be LTS though.

[http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)
[SIZE=3]Thanks for that.

Interesting.
[/SIZE]

---

### Post by pretty_whistle on 2011-12-11
> **claracc said:**
> Lubuntu 12.04 will not be Long Term Support (LTS) release. Ubuntu 12.04 will be LTS though.

[http://ubuntuforums.org/showthread.php?t=1870442](http://ubuntuforums.org/showthread.php?t=1870442)
[SIZE=3]Considering the link you gave says what I needed to know, I'll just mark this question as solved.

[/SIZE]

---

