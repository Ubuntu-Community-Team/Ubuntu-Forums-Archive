---
title: "Questions about rolling releases"
date: 2010-09-13
forum: General Help
---

### Post by kellyapproved on 2010-09-13
I read a short article on Wikipedia about rolling releases and am not really sure what to think.

Is Ubuntu a rolling release distro and is there an advantage of going with a distro that is a rolling release vs one that isn't?

I'm not looking for cutting edge software, but I am really after quick security updates...eg if Firefox releases a new version to address an exploit, I'd like to get it right away.

---

### Post by Rocket2DMn on 2010-09-13
Ubuntu is *not* a rolling release distro, it comes out with a new release every 6 months (which is actually pretty often).  The big advantage to a rolling release is that you can always get the latest and greatest software, but it also comes with a higher risk of breaking packages and stuff not working b/c not everything is compatible with everything else.

Ubuntu does a process called [Stable Release Updates]("https://wiki.ubuntu.com/StableReleaseUpdates") which includes security patches for software.  This means you won't necessarily get the newest version of a program in a stable release of Ubuntu, but some fixes are applied (like Firefox exploits).  Firefox is upgraded pretty regularly in stable releases with bug fixes.  In Long Term Support (LTS) release like Ubuntu 10.04 Lucid Lynx, major programs like Firefox may receive a full version update down the road in order to help stay relevant.

---

### Post by srs5694 on 2010-09-13
Ubuntu is *not* a rolling release distribution. The term, as I understand it, refers to distributions that have no version numbers. Instead, software is updated on an item-by-item basis whenever it's possible or convenient. For instance, in a rolling release distribution (like Gentoo), there might be a major version update (not just a bug fix) to KDE on November 1, a major version update to Firefox on November 7, a major version update to OpenOffice.org on December, and so on. Additional bug fix and minor updates to other software, and even to packages that have recently had major updates, occur in-between those dates. In Ubuntu, the bug fix, security, and perhaps some minor updates will get released within a version, but the major version updates of individual packages get held and then rolled into a particular version update (say, version 11.04).

For your purposes, I'm not sure there's much, if any, advantage to a rolling release distribution. Ubuntu, like most Linux distributions, offers updates to packages between releases in order to fix bugs and security problems, so it's unclear whether you'd really see much difference in the speed with which such updates are made available.

I've used both types of distributions. In fact, my main desktop system currently runs Gentoo, which uses the rolling release model. I prefer the rolling release approach because it means that there's never a need to deal with a full distribution upgrade. Such upgrades often cause multiple problems because so many things can change at once. With the rolling release model, these problems tend to come at you one at a time rather than in big overwhelming masses. OTOH, there is something to be said for having a more stable system and then dealing with everything all at once when you've got the time. Take your pick.

---

