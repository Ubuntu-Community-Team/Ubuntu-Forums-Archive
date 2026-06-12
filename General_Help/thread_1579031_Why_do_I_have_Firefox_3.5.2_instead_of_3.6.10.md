---
title: "Why do I have Firefox 3.5.2 instead of 3.6.10?"
date: 2010-09-21
forum: General Help
---

### Post by emakarov on 2010-09-21
Hello,

Synaptic says that I have firefox 3.6.10+build1+nobinonly-0ubuntu0.10.04.1 (lucid-security) package installed. In Settings | Repositories | Other Software, I don't have anything checked. In the Properties | Installed Files for the firefox package, I see /usr/bin/firefox listed. However, when I run "/usr/bin/firefox --version", I get "Mozilla Firefox 3.5.2". When I choose Help | About withing Firefox, I also see version 3.5.2.

How come the actual version does not correspond to what Synaptic says?

---

### Post by Tibuda on 2010-09-21
[s]Because ubuntu repositories does not offer major updates, only security fixes.
See [https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)

All software in 10.04 are from April 2010.[/s]

EDIT: I got it wrong. Lucid got 3.6. Do you have Firefox installed from another source?

---

### Post by BigDope on 2010-09-21
system > administration > update manager > download the update package for firefox there and install

---

### Post by emakarov on 2010-09-21
This is becoming weird. Yes, after doing "ls -l /usr/bin/firefox" I remembered that it was a symbolic link to /opt/firefox/firefox, which is where I installed Forefox 3.5.2 when I still had Hardy. (I upgraded to Lucid recently.) However, I don't understand why this file (i.e., the link) was not overwritten during the reinstallation that I tried several times  (through Synaptic and by downloading the package manually and running GDebi package installer on it). In fact, I deleted the link and attempted to reinstall Firefox again, and this time it complained:

Setting up firefox (3.6.10+build1+nobinonly-0ubuntu0.10.04.1) ...
update-alternatives: error: alternative path /usr/bin/firefox doesn't exist.

I ended up by manually creating the symbolic link firefox -> ../lib/firefox-3.6.10/firefox.sh, just like in the package archive, and now Firefox 3.6.10 seems to work fine.

> system > administration > update manager > download the update package for firefox there and installWhen I ran Update manager (before I did what I described above), it said that my system is up-to-date and I did not see any suggestion to (re)install Firefox. I also don't know how to request the reinstallation of a specific package from the Update Manager.

---

### Post by Tibuda on 2010-09-21
How have you changed the link in /usr/bin to /opt/firefox? If you have not used the debian alternative system (update-alternatives), this is probably the reason why the installer could not mess with the symlink.

---

### Post by emakarov on 2010-09-21
I probably created the link by hand. I did not know about update-alternatives or that the installer does not overwrite some links. In fact, during the upgrade from Hardy I got a bunch of error messages that started with the complaint that /usr/lib/pkgconfig/pygtk-2.0.pc, which is a link, existed and ended with the warning that my system could be unusable. After I removed the link manually and ran apt-get, everything was OK, it seems.

Thanks for your response.

---

