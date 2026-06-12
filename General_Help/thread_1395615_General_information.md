---
title: "General information"
date: 2010-02-01
forum: General Help
---

### Post by germandev on 2010-02-01
Hi!

I am using Linux for about 3 years now and so do know the basics. My first distribution was Debian, afterwards I switched to Arch. 

Unfortunately I am not that confident with Arch Linux anymore. There are some hardware issues (regarding the Catalyst driver) and other software issues where just no one helps me. 

Because of the large community and good experiences of friends I am thinking of switching to Ubuntu but have two questions. I really hope there's someone who can answer them ;)

1. 

Few people say Ubuntu is "just for beginners" as it is too "overcrowded with useless packages and services that can't even be removed". Because I don't know Ubuntu I can't estimate what's right, what's over the top and what's completely wrong. 
I am mainly using my system to develop Java web applications on JBoss AS and so need all of the resources the system has. I want to disable all kind of unnecessary services like Bluetooth and update notifications and be able to fine tune the system. Would I be able to do so when using Ubuntu?

2.

Arch Linux provides a repository for user built packages, called AUR. The packages can describe their own dependencies and what they provide. This is not only useful for packages that are not maintained by the distribution at all but also when it is necessary to use "bleeding edge" software because e.g. a bug or a needed function. 

Two examples:

* A package vlc-3gp is provided that compiles vlc with 3gp support. The original player doesn't play that format.
* Latexdraw is a program I sometimes use to create pstricks graphics. 

I could compile these packages by myself but the provided package build does this automatically for me. It does not only save time and configures the distribution specific parameters but also enables the possibility to check for (and install) updates. When using tools like "yaourt" the packagebuild can be edited before installation.

Is there something like the AUR for Ubuntu as well?

Thank you in advance and best regards!

---

### Post by Leppie on 2010-02-01
hi and welcome to the community,

1. you could do a minimal install and then install whatever window manager you prefer. normally if you do a full ubuntu install, you would get the ubuntu-desktop which is a gnome de with some ubuntu stuff. by doing a minimal install and afterwards adding your preferred windows manager you would avoid the "bloated" desktop environment. if you want a complete install which is not as bloated as the ubuntu distro, but still ubuntu based have a look at crunchbang linux.

2. ubuntu provides the proposed (pre-releases) and unsupported (backports/testing) repositories. this is where you would usually find your bleeding edge technology requirements.

---

