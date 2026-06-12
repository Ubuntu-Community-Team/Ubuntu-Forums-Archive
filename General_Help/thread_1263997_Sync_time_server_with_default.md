---
title: "Sync time server with default?"
date: 2009-09-11
forum: General Help
---

### Post by ChaosChris2009 on 2009-09-11
I've got a problem with my BIOS time setting, after I tried Slax Linux, it changed from the default, and it's off by a few hours

How do I confront on fixing this w/o replacing the battery watch or manually fixing the time by typing it out, that'll just leave it traced back again

I've already found the [site ]("http://www.timeanddate.com/worldclock/city.html?n=876")that I want to sync the time with my OS

I'm in Slax, any tips on how to fix this via Linux?

---

### Post by tgalati4 on 2009-09-11
I'm not familiar with Slax.  Is it related to slackware?  Ubuntu stores time in the BIOS at shutdown as GMT or UTC.  Windows and some other distros store local time to the BIOS.  When switching between them, chaos ensues because you can't be at the same place at two different times.

Oh, wait, you can't be at two places at the same time.  Well, can you configure slax to store time as UTC?  You can also install ntp (a server that runs all the time) or ntpdate (a command that allows you to sync once at boot or whenever).

sudo apt-get install ntpdate

or sudo apt-get install ntp

To run it, put the following in /etc/rc.local   (before the exit 0 line)

ntpdate time.apple.com

Their clocks are shinier.

---

