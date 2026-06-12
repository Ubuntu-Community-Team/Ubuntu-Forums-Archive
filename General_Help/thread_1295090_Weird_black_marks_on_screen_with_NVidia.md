---
title: "Weird black marks on screen with NVidia"
date: 2009-10-19
forum: General Help
---

### Post by x-na on 2009-10-19
Hi!


My problem seems to be a very uncommon one, I haven't found a any help from anywhere and boy I have searched before posting this.

I'm using 64-bit Jaunty, AMD 64 X2 5600+, Asustek M2N68 motherboard, NVidia GeForce 6200 LE PCI-E, NVidia driver version is 185.18.36 from PPA. Same problem occurs with the 180-driver Ubuntu ships with. I haven't tried the 190-beta yet.

Usually this happens in Firefox, but for wife Evolution is affected too. Sometimes almost a half of a webpage might be black, sometimes there's just little lines when scrolling down. Doesn't happen all the time, but moving the cursor might trigger this too.

Screenshot below, as those marks disappear when taking a screenshot or switching windows

This problem was solved after upgrading to Karmic. Maybe x.org bug, nvidia driver version is still the same.

---

### Post by x-na on 2009-10-22
> **x-na said:**
> Hi!


My problem seems to be a very uncommon one, I haven't found a any help from anywhere and boy I have searched before posting this.


Anyone?

---

### Post by P4man on 2009-10-22
Are you using compiz ? If so, does it help to turn it off?
I found this bug which looks similar but is really old. Which ubuntu version are you using?

[http://humani.st/ubuntu-nvidia-compiz-black-window-bug-fix/](http://humani.st/ubuntu-nvidia-compiz-black-window-bug-fix/)
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96473](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/96473)

---

### Post by x-na on 2009-10-23
> **P4man said:**
> Are you using compiz ? If so, does it help to turn it off?
I found this bug which looks similar but is really old. Which ubuntu version are you using?


No, no compiz. Turning it on or off doesn't resolve this issue. And as I said in my first post, 64-bit Jaunty. Soon 64-bit Karmic.

I'm planning to do a fresh install, in hopes it'd solve this issue.

---

