---
title: "language-pack-en failed to upgrade"
date: 2010-01-29
forum: General Help
---

### Post by CrazySat on 2010-01-29
Good morning.

I am using since from last septmber Ubuntu 8.04 LTS which I keep update through Update Manager on daily basis, I am a beginner with Linux systems.

Today Update Manager offered 9 updates but one of them, language-pack-en can't be selected from the list and can't be upgraded.

If I try to install it manually from terminal session
( sudo apt-get install language-pack-en) I get this message :

> fabrizio@fabrizio-desktop:~$ sudo apt-get install language-pack-en
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  language-pack-en: Depends: language-pack-en-base (>= 1:8.04+20100117) but 1:8.04+20090105 is to be installed
E: Broken packages
fabrizio@fabrizio-desktop:~$ I reinstalled with Synaptic language-pack-en-base and it seems to be updated to last version 8.04+20090105

This is the situation in Synaptic
[IMG]http://i45.tinypic.com/fddqix.png[/IMG]

How can I solve the problem ?
Thank you for your help.

---

### Post by CrazySat on 2010-01-29
I do apologize if I maybe posted in wrong section, maybe proper one was "[Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")" ...

---

### Post by raktarok on 2010-01-29
Hi,

You can still install other packages, right?

The problem here seems to be that a newer version of language-pack-en-base(>=1:8.04+20100117) is required to install language-pack-en, but the repo doesn't have such version of language-pack-en-base. Hardy is supposed to be a Long Term Support(LTS) version, but I guess no new package is available for hardy yet. You could try searching for the new version of this package in google, and see if you can find one for hardy.

Of course, if you absolutely need that update, you can use force options and install it, but I would not advise that.

Good luck!

---

### Post by CrazySat on 2010-01-29
Thank you raktarok for your answer.

Yes, I installed all other packs ...

I will wait for an update ... I just had tought it was due to my install and not to a repositories update problem.

---

### Post by muckst3r on 2010-01-29
Yeah - I just got this one as well - mai sabai!
:o

---

### Post by rreese6 on 2010-01-29
I have seen this a couple times before. All we need to do is wait.
They will eventually correct it. It isn't a critical update.
One time, I remember it taking about 4 weeks before the upgrade would install.

---

### Post by CrazySat on 2010-01-30
Hi,

thank you for your confirmation.

Do you think is any way to send a bug report like it is suggested in the log during failed install just to make maybe things easier to developers ?

> Since you only requested a single operation it is extremely likely that
the package is simply not installable [B]and a bug report against
that package should be filed.[/B]

---

### Post by igoddard on 2010-01-30
> **CrazySat said:**
> Hi,

thank you for your confirmation.

Do you think is any way to send a bug report like it is suggested in the log during failed install just to make maybe things easier to developers ?

No need to bother, someone's already done that: [https://bugs.launchpad.net/ubuntu/+source/language-pack-en/+bug/514329](https://bugs.launchpad.net/ubuntu/+source/language-pack-en/+bug/514329)

---

### Post by CrazySat on 2010-01-31
Thank you for pointing me to that. We just need to wait ...

---

### Post by CrazySat on 2010-02-02
The update just came today \\:D/

Thank you !

---

### Post by taur on 2010-03-24
I had the same problem in karmic for a few days, corrected now though

---

