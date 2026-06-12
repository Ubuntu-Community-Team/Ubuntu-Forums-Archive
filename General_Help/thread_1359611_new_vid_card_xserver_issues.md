---
title: "new vid card xserver issues"
date: 2009-12-19
forum: General Help
---

### Post by fleury29 on 2009-12-19
So I have been reading just about every xserver issue thread on the forums and havent found anything so I am just going to tell you guys my exact problem.

I am running ubuntu 9.10 on a machine that I use as a file server.  I came home from school with my personal desktop to find a blown cap on my mobo.  While I wait for a replacement cap I decided to pop my Nivida GeForce 8800 GTS into my file server to beef up the graphics so I can game while on break.  After installing the card I booted up the PC and it started to load and I saw the panels begin to load.  Instead of jumping to the desktop everything went white.  I was able to CTRL-ALT-F1 into a console to try to run "sudo dkpg-reconfigure xserver-xorg" but it did nothing and just asked for my next command.  I tried renaming xorg.conf.failsafe to xorg.conf, but that made things worse lol.  I even booted into the repair console and repaired broken packages.  I switched back to the old xorg.conf file and am back where I started...any ideas?

PS I'm going to try to find a way to install the restricted drivers for my Nvidia drivers via the command line.

Thanks

---

