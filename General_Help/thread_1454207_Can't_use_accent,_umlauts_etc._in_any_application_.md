---
title: "Can't use accent, umlauts etc. in any application anymore"
date: 2010-04-14
forum: General Help
---

### Post by mutvik on 2010-04-14
After updating to Lucid Beta 2, I was unable to place accents, umlauts etc. on letters in KDE apps (as described [here]("https://bugs.launchpad.net/kubuntu-ppa/+bug/520408")). (I've  The solution of the problem, they said, was running "sudo im-switch -s default-xim". I did, but got the following error(s):

No system wide default defined just for locale nb_NO .
Use "all_ALL" quasi-locale and set IM.

After searching for a solution for too long, I tried "sudo im-switch -s default", getting this error:

No system wide default defined just for locale nb_NO .
Use "all_ALL" quasi-locale and set IM.
update-alternatives: using /etc/X11/xinit/xinput.d/default to provide /etc/X11/xinit/xinput.d/all_ALL (xinput-all_ALL) in manual mode.

This, or something I don't know of, caused the problem (I know, stupid!), previously only present in KDE apps, now to apply to what seems like all other apps (in gedit I can't even write æøå). This also applies to the Greek polytonal keyboard mapping.

Obviously, I must have damaged some important configuration files. I anyone could tell me how to make accents etc. work like before, or even in KDE apps, I would be very grateful. I tried "sudo dpkg-reconfigure console-setup", but with no result. I've I have backups of my home folder from before the update, but not much more.

"sudo im-switch -s default" gives:

Your input method setup under nb_NO locale as below.
=======================================================
No private configuration can be defined for root account.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - manual mode
 lenke peker for øyeblikket til default
default - prioritet 10
default-xim - prioritet 0
none - prioritet 0
Nåværende  «beste» versjon er default.
=======================================================
The available input method configuration files are:
default default-xim ibus lo-gtk none th-gtk th-xim 
=======================================================

----

BTW: Running "sudo im-switch -s default-xim" didn't restore the previous settings, as if that would be logical.

---

