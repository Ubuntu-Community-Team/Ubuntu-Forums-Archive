---
title: "Weird Youtube page rendering"
date: 2009-07-17
forum: General Help
---

### Post by VRXJudge on 2009-07-17
I'm not quite sure why Youtube renders like this (see attached screenshots). Similar sites like Liveleak do not exhibit this problem.

I haven't done anything weird; just using Firefox metapackage + ubuntu-restricted-extras. Abrowser 3.5 (branded Firefox won't move to 3.5 for some reason) and Midori exhibited the same problem when I later installed them for testing.

---

### Post by SledgeHammer_999 on 2009-08-11
I experience the exact same problem. I haven't solved it yet and I don't know what causes it.

Maybe it is an issue with graphics card driver.

My specs are: ubuntu 9.04 64bit and gpu:ati 1800xl(uses the default open-source driver provided by ubuntu).

---

### Post by SledgeHammer_999 on 2009-08-12
My suspicions were correct.

Edit your xorg.conf file and in the Device section put:
> Option	"AccelMethod"	"XAA"

There is even a bug report:
[X.Org](https://bugs.freedesktop.org/show_bug.cgi?id=20469)
[Launchpad](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/335460)

---

