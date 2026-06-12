---
title: "Problems with xorg after upgrade to Dapper"
date: 2006-02-08
forum: General Help
---

### Post by Jefim on 2006-02-08
I recently upgraded from Breezy to Dapper and encountered a problem with xorg.
The thing is that when starting x i get the following output:
failed to load driver 'kbd' (no such file)
failed to load driver 'mouse' (no such file)
no core keyboard found
no core pointer found

and x ends running leaving me in linux terminal (keyboard works here). i haven't changed ANY config files!

And 1 thing more - I'm not quite sure if i did the upgrade correctly. I did it from the update manager (this thingy which shows available updates in tray) after I added dapper repos to my sources.list.

Currently I reinstalled Breezy, but still, I want to use Dapper. Does anyone know where I screwed up?

---

### Post by magnusbb on 2006-02-08
It is not my intention to be harsh, but:

This is the Breezy support forums.

Dapper is not, by any means, considered stable - in fact, it is more unstable than "unstable". X being unusable is a typical behaviour in Dapper, since they're making the transition from 6.8 to 7.0.

I would recommend going back to Breezy for now.

To answer your question regarding the upgrade: No, if you skipped the so-called "apt-get dist-upgrade" command, you've not installed Dapper the correct way.

---

### Post by newuser111 on 2006-02-08
you shouldnt use the update manager to do updates when doing major upgrades (ie from breezy to dapper), in fact its better to exit X altogether

you should type ctrl alt f1 after putting the correct repos in your sources.list, removing all the breezy sources

then type init 1 then type sudo apt-get update and sudo apt-get dist-upgrade

you will also have to run sudo apt dpkg-reconfigure xserver-xorg and select vesa and then reboot, after you will probably have to reinstall your video card drivers from scratch because there are new kernels installed with dapper

---

