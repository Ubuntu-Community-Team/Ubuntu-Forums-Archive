---
title: "Ubuntu version name messed up."
date: 2009-09-28
forum: General Help
---

### Post by Akira Kurosawa on 2009-09-28
[SIZE=2]**SELF SOLVED (See Below)**[/SIZE]
Hello, I'm fairly new to Ubuntu. I installed Ubuntu Jaunty desktop. 
I recently installed Linux Mint's menu onto Ubuntu, but now when I try to upgrade I get an error, saying
"An upgrade from 'Gloria' to 'Karmic' is not supported with this tool." 
Gloria being the Linux Mint version name.

Can anyone push me in the right direction for restoring Ubuntu Jaunty's version name?
Any help would be much appreciated.

---

### Post by zvacet on 2009-09-28
How did you install Gloria?On top of Ubuntu or some other way?

---

### Post by Topsiho on 2009-09-28
An upgrade to a newer (normal) version of Ubuntu is only possible from the last previous (normal) version, of UBUNTU. Same applies for the LTS-versions (Long Term Support), but that does not apply here.

You say that on top of Jaunty you installed Gloria, so you now have Gloria installed and not Jaunty.

An upgrade to a newer version, in this case Karmic, is therefore not possible.

Also: Karmic is not released yet, only the preliminary test versions, the last one being Alpha6 (which on my test computer is uninstallable, but that's something else). So for this reason an upgrade to Karmic is not possible too.
Fortunately so, because upgrading to a release which is not yet a finished product is really not a wise thing to do :)

Topsiho

---

### Post by Topsiho on 2009-09-28
Rereading your text I read:

"I recently installed Linux Mint's menu onto Ubuntu"

Even if that means that you only changed some part of Jaunty's to something else, you can't upgrade to the next version of Ubuntu.
The upgrade assumes a certain condition of Jaunty, and that is a fully updated Jaunty system, and of course no exceptions to this. If an exeption is detected it's only right that an error is reported and the upgrade not started, leaving you with an unusable system ...

Topsiho

---

### Post by t0p on 2009-09-28
If you really want to upgrade to Karmic (rather than doing a clean install) I advise: 

1. Wait for Karmic to be officially released;

2. Remove the Mint menu if that's possible.

If you can't revert Jaunty to its original state, an upgrade will not be possible.  And an upgrade to Karmic isn't possible at all til it's been released!

---

### Post by Akira Kurosawa on 2009-09-28
No no, I didn't install gloria on top of ubuntu. Just the gnome panel applet (mintmenu)
I used this guide, [http://www.khattam.info/2009/08/01/install-linux-mint-menu-in-ubuntu/](http://www.khattam.info/2009/08/01/install-linux-mint-menu-in-ubuntu/)

[http://lwn.net/images/mint7/mint7_menu.png](http://lwn.net/images/mint7/mint7_menu.png)
I mounted the alternate iso for karmic, and am trying to install from there.
[SIZE=1]*(this isn't my primary OS, so I'm not worried about bugs. I'm just learning)*[/SIZE]

---

### Post by Akira Kurosawa on 2009-09-28
**NEVER MIND - SOLVED**
Thanks for the input guys but I figured it out myself.
/etc/lsb-release
Containted what I was looking for.
I restored the text back to default after cross referencing it with the live cd version.

> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.04
DISTRIB_CODENAME=jaunty
DISTRIB_DESCRIPTION="Ubuntu 9.04" 

After that, upgraded, rebooted and using karmic without a hitch, without having to uninstall anything.

---

