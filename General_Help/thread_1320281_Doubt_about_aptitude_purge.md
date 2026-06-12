---
title: "Doubt about aptitude purge"
date: 2009-11-09
forum: General Help
---

### Post by amrith92 on 2009-11-09
Hi!

I've recently upgraded Ubuntu from 9.04 to 9.10 Karmic Koala. Since the upgrade I noticed that I couldn't use compiz-fusion, and my audio (speakers) stopped working, among other problems, like nautilus crashes etc.

I've tried the 'fixes' for these problems, but they didn't help. This is when I suspected that maybe some packages were broken (My power did go out during the upgrade to Karmic Koala once, in the download stage, but it resumed from the same point when the power came back on). That's when I opened up aptitude from the terminal. I selected the "purge" option from the menu, and I got some 24 odd broken packages.

Among these packages, were some essential packages like tar, util-linux, sed, apt, ncurses-bin, ncurses-base, gzip, grep, findutils, mount, diff, debianutils, coreutils, bsdutils, dash, bash, python-minimal, perl-base, login, hostname, e2fsprogs, dpkg, base-passwd and base-files.

It keeps asking me for confirmation to purge them, asking me to type:
[CENTER]"Yes, I am aware this is a very bad idea"
[LEFT]
My question is this:
What Should I do at this point? Must I go ahead and let aptitude purge these packages, and trust that my system will start up, or do something else?

Thank you,
Amrith

PS: I have no idea if I'm posting this in the right forum or not...
[/LEFT]
[/CENTER]

---

### Post by _khAttAm_ on 2009-11-09
I think purging them and installing them before reboot will do it.

I haven't done this myself though.

---

### Post by amrith92 on 2009-11-09
So if I purge them, would the system crash before I have a chance to reinstall the packages? I'm actually a little worried about performing this purge, as I currently don't have the resources to take a backup of my data...
Thanks again :)

---

### Post by nothingspecial on 2009-11-09
If you remove apt and dpkg your going to struggle to install anything, without some fancy chrooting and what have you. Try to fix them first.

```
sudo apt-get install -f
```

---

