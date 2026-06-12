---
title: "Get rid of Upstart"
date: 2009-11-10
forum: General Help
---

### Post by PacShady on 2009-11-10
Hey guys,

Ever since upgrading to Karmic I've had nothing but problems, mostly to do with the booting process, and I think Upstart is to blame.

* my random-key encrypted /tmp directory doesn't mount automatically (had to make a script to manually mount and change ownership)
* keep getting gconf-sanity-check-2 error 256 (think it's linked to the /tmp problem, after the script above it only happens half the time now)
* splash screen only stays on sometimes
* every few boots complains of a mounting problem and drops to a recovery console, which can immediately be skipped pressing Ctrl+D (haven't caught why yet, as whenever it happens I haven't disabled the splash screen)
* can't log boot messages (apparently upstart doesn't use bootlogd, even though the config files to run it are still there)
* typing passwords in for encrypted drives is unreliable (with splash- random key press is ignored; without splash- have to press Enter random number of times before input will be accepted)
* keeps telling me my encrypted drives are unavailable, sometimes several times, before finding that they actually ARE available and moving on with the boot

Coupled with other errors I've read such as GDM loading before fsck is finished scanning drives (already tested the 'bootwait' option for fstab, and it causes my drives to not mount due to a "bad fs option"), and God knows what else, I'm seriously thinking Upstart is way more trouble than it's worth. Because of the number of problems, and the inability to log boot messages, I'm having a hard time trying to get things to work the way they should.

Does anyone know if it's possible to swap back to the older system (which has apparently been Upstart all along but from what I understand still using sysvinit scripts)? At this stage, Karmic is turning out for me like Edgy was, and I'll either have to downgrade back to Jaunty or change to a different distro that doesn't use Upstart the way Karmic does.

'Shady

---

### Post by PacShady on 2009-11-10
Ok, I caught the problem regarding the mounting error throwing me back to a recovery console. The system seems to be trying to mount the /tmp drive before it's had a chance to finish starting the encryption. By the time it's thrown back a recovery console, the encryption has started, so exiting the console works immediately.

Maybe this is why the original init system did things in a linear fashion, instead of trying to save time by running everything at once.

---

### Post by kobayashison on 2009-12-04
> **PacShady said:**
> Hey guys,

* my random-key encrypted /tmp directory doesn't mount automatically (had to make a script to manually mount and change ownership)
* keep getting gconf-sanity-check-2 error 256 (think it's linked to the /tmp problem, after the script above it only happens half the time now)

'Shady

I have the same problems.
The encrypted /tmp bug is probably opened here: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/456274](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/456274)

I think I resolved the "gconf-sanity-check-2 error 256" updating the firmware of my HP DV2000 notebook to F.2A, not the latest because I get other problems.

---

### Post by PacShady on 2009-12-04
I think I did find that bug report when I was trying to fix this, but it seems different. I disabled usplash (xsplash?) and the bug still happened. For me though it doesn't matter any more, after a few days of tearing my hair out trying to dodgy up a hack solution, and having Ubuntu ignore all my attempts, I swapped over to Arch Linux which has worked like a dream ever since (once I managed to set it up), including my randomly encrypted /tmp partition.

I don't know if it would work, but maybe setting up the encryption manually similar to Arch might bypass whatever Ubuntu screws up. Their Wiki page for setting up LUKS encryption is here: [http://wiki.archlinux.org/index.php/LUKS](http://wiki.archlinux.org/index.php/LUKS). I don't know how much might need to be changed to suit Ubuntu (for instance, Ubuntu doesn't have an rc.conf file), and I don't know if it's enough to get past the problems with Upstart, but it might give someone some ideas. Either that, or if you can handle spending some more time in the console than Ubuntu requires, give Arch a try!

'Shady

---

