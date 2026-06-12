---
title: "update-grub doesn't work"
date: 2010-10-03
forum: General Help
---

### Post by Dustin2128 on 2010-10-03
To start with, this machine has two hard drives, ubuntu is installed to the second one and the first one is blank. I installed slackware 13.1 to sda, and skipped a lilo install as grub was already installed with ubuntu. So I boot into my ubuntu system (jaunty) and run sudo update-grub. When I restart, slackware is not listed, and there are still 6 different and broken options to boot into hardy (previous issue). Recommendations? I'd be happy to swap to LILO, but I've only used it with single boots and it's had a bad reputation for user friendliness (not like grub is much better though honestly...).

---

### Post by drs305 on 2010-10-03
Have you updated Jaunty to Grub 2? G2 is better at picking up other OS's. If you haven't and are interested, here's a blog on how to do it:
[http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html]("http://www.ubuntu-inside.me/2009/06/howto-upgrade-to-grub2-on-ubuntu-jaunty.html")

If you have, we can take a look at least at the broken hardy entries and find out where to remove things so they don't appear. You'll have to post the contents of RESULTS.txt found here:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by Hoopz on 2010-10-03
I think there's a step before running update-grub.  Can't remember right now.  I am still new to linux but this might help you [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Dustin2128 on 2010-10-03
the computer doesn't have a net connection and won't for a while, and I'm almost certain that I haven't upgraded to grub 2. It sounds like the issue as slack 13 was detected just fine by my lucid laptop. Since I can't use the repos, I'm going to have to download grub 2 to my flash drive, does anyone have a link?

EDIT: after I get the link for grub 2, I'm going to download bootinfoscript to my flash drive as well.

---

### Post by Dustin2128 on 2010-10-03
hm, if grub 2 is the default in lucid, would an upgrade of my ubuntu partition solve the problem? I should probably do it anyway to keep up to date. Can you jump straight from jaunty to lucid? I bought a 15 pack of DVDs today but I still prefer not to waste them.

---

### Post by drs305 on 2010-10-03
I don't know about dependencies and such, but here is the grub2 page for Jaunty. Note that it is version 1.96. Grub 2 has made a lot of improvements since then, but 1.96 is the version listed for Jaunty and may be what you need for the transition from grub to grub 2 anyway. 
[http://packages.ubuntu.com/jaunty/grub-pc]("http://packages.ubuntu.com/jaunty/grub-pc")

Added: Yes, an upgrade to Lucid would be the way I'd go. But it would have to be a clean install or multiple upgrades through karmic to lucid. You better hurry though if you want an online upgrade, as you'd want Jaunty to be updated and it reaches End of Life this month.

---

### Post by Dustin2128 on 2010-10-03
> **drs305 said:**
> 
Added: Yes, an upgrade to Lucid would be the way I'd go. But it would have to be a clean install or multiple upgrades through karmic to lucid. You better hurry though if you want an online upgrade, as you'd want Jaunty to be updated and it reaches End of Life this month.
No net connection, but I can't believe jaunty is already at EOL... man I've been at this a while. I have decided to go with a fresh lucid install, meant to give a disc to a friend anyway.

---

