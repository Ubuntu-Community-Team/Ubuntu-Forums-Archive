---
title: "Lucid dselect: Available Standard packages won't stay purged"
date: 2010-09-10
forum: General Help
---

### Post by fmyhr on 2010-09-10
Hi,

Yeah, I use dselect. What can I say, I've grown used to it and prefer it to the more modern dpkg front-ends.

Recently did a fresh install of Lucid Server 10.4.1 AMD64. There are some Standard packages that I don't need and I used dselect to purge them:
apparmor
apparmor-utils
friendly-recovery
parted
ufw
update-manager
libapparmor1
libntfs-3g75
libparted0
ubuntu-standard
popularity-contest
pppoeconf
ntfs-3g
libapparmor-perl

dselect removed them as I requested. But now whenever I run dselect "select" screen, all of those Available Standard packages get marked for installation. I can press "C" to make selections revert to what's currently installed, but that's kludgy and sooner or later I'll forget to do that, and it's not always what I want anyway (for example after running "update").

This undead won't-stay-purged behavior of Available Standard packages is a change in how things used to work: I don't have the same problem on an aging Dapper system. Nor have I noticed it on a Karmic notebook.

I've man'ed dpkg, dselect, apt, apt.conf and looked about in
/etc/apt
/etc/dpkg
/usr/share/doc/apt/examples/configure-index.gz

and looked several times for any installed meta-package that would be bringing these Available Standard packages along for the ride every time I run dselect. I've come up empty.

Anybody have ideas?

Thanks for any tips!
-Frank

---

