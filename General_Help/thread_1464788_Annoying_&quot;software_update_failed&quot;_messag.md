---
title: "Annoying &quot;software update failed&quot; message with firefox 3.6"
date: 2010-04-28
forum: General Help
---

### Post by t0p on 2010-04-28
I've been running Firefox 3.6 on my Ubuntu Hardy machine for a while with few problems.  But just recently it told me I needed to install a few updates - which I did, the trusting sould that I am.

Thing is, every time i start FF3.6, I get this message:

> **Software  Update Failed**
The update could not be installed.  Please make sure there are no other copies of Firefox running on your computer, and then Restart Firefox to try again.

Thing is, there are no other instances of Firefox running.  I restart Firefox and the same message pops up again.  But if I don't bother restarting Firefox - if I just click on the **OK** button, the problem goes away and all works as I expect it to.

This is clearly not a major problem - but I intend to upgrade from 8.04LTS to 10.04LTS soon, and I'd like to have this issue recified before that change.  So, anyone out there got any didea what is going on?

**PS:** As I mentioned above, I plan to upgrade from 8.04LTS to 10.04LTS.  If I go the route of clicking on the dist-upgrade thing in the package manager, will this lead tp 8.04 -> 8.10 -> 9.04 -> 9.10 -> 10.04?  Or will there be a much simpler route going straight from 8.04 -> 10.04, with no dilly-dallying on the way?  Should I just bite the bullet and get a Lucide CD?  Or will dist-upgrade do the job for me?

---

### Post by randumnumber on 2010-04-28
I moved to Chrome, it loads so much faster. Firefox was giving me headaches everyday. I am in the process of upgrading to 10.04 right now from 9.04 so far I had had to go the long route...it might be worth getting a disk.

---

### Post by lovinglinux on 2010-04-29
> **t0p said:**
> This is clearly not a major problem - but I intend to upgrade from 8.04LTS to 10.04LTS soon, and I'd like to have this issue recified before that change.  So, anyone out there got any didea what is going on?


Looks like you have Firefox auto-update enabled and it can't install the updates because of permission issues. Go to "Edit >> Preferences >> Advanced  >> Update" and disable the option to update Firefox.

How did you install Firefox 3.6?

> **t0p said:**
> This is clearly not a major problem - but I intend to upgrade from 8.04LTS to 10.04LTS soon, and I'd like to have this issue recified before that change.  So, anyone out there got any didea what is going on?

I would remove non-default Firefox versions before the upgrade and leave just the default installation. Don't forget to disable any ppa repository before the upgrade.

> **t0p said:**
> **PS:** As I mentioned above, I plan to upgrade from 8.04LTS to 10.04LTS.  If I go the route of clicking on the dist-upgrade thing in the package manager, will this lead tp 8.04 -> 8.10 -> 9.04 -> 9.10 -> 10.04?  Or will there be a much simpler route going straight from 8.04 -> 10.04, with no dilly-dallying on the way?  Should I just bite the bullet and get a Lucide CD?  Or will dist-upgrade do the job for me?

You can go straight from a LTS to another LTS version. Nevertheless, if you can afford to do a clean install, then I would do it. This way you will be able to format your file system as ext4, which is the default now. If you don't have a separate partition for home, then is a good time to create one. 

I never did upgrades. I always do clean installs and sometimes I even wipe my home settings, because things can get messed.

---

