---
title: "/etc/apparmor/initramfs:  No such file or directory"
date: 2009-11-12
forum: General Help
---

### Post by 1clue on 2009-11-12
Hi,

I have a partially tatered system.

It all started when I got frustrated with the lack of VMware in 9.10.  I did some research and decided to install Xen.

Something went wrong with the installation.  I just went through, looked for the master packages and installed them, and then started picking some ancillary stuff in the same search that looked interesting.  I installed that, and then rebooted.

I didn't get X at all.  The screen went through the disk scan (it's doing that every boot, for some reason) and then started flashing right when the log says, "Starting apparmor profiles..." and then immediately after that, chroot:  Cannot execute /etc/apparmor/initramfs:  No such file or directory
Failure:  AppArmor profiles failed to load.

The flashing goes on for a few seconds, then I get the login prompt on the console.

I've done a bunch of stuff, including messing around with aptitude which I used to be fairly familiar with but not anymore.  I uninstalled all the Xen stuff, then without thinking about it uninstalled some apparmor stuff because I was still dealing with a broken package.  I was never very familiar with Debian's dependency resolution commands, so I probably got too delete-happy with the Xen packages.

I figured out that /etc/apparmor/initramfs belongs to apparmor.  I re-installed that, and now there's NOTHING inside /etc/apparmor.

I would really like my X to work again, I need to use this thing for my job.  Anyone know how to fix this?

Oh yeah, it's amd64, intel i7 920, Karmic.

Thanks.

Thanks.

---

### Post by 1clue on 2009-11-12
Does anyone have an idea how I can get a working system again?

Thanks.

---

### Post by 1clue on 2009-11-13
Solved by re-installing the system.

Fortunately I had made partitions for most of my data and some of my configuration.  I was back up in a few hours.

---

