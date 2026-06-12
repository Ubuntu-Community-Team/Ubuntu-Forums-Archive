---
title: "How to downgrading server kernel to desktop kernel?"
date: 2011-03-07
forum: General Help
---

### Post by xavierzhao on 2011-03-07
Hi all.

Currently I am looking at the following way to solve my problem that uses more than 3GB RAM on 32-bit Ubuntu.

[http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html](http://www.ubuntugeek.com/how-to-use-more-than-3gb-ram-on-32-bit-ubuntu.html)

For various reasons, I am trying to downgrade server kernel to desktop kernel. Can anyone given me some ideas?

---

### Post by xavierzhao on 2011-03-07
My English is poor, thanks in advance for your reply

---

### Post by oldos2er on 2011-03-07
Which version of Ubuntu are you running? If 10.04 or newer, those directions from 2008 won't apply. You need the PAE kernel: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

---

### Post by xavierzhao on 2011-03-09
> **oldos2er said:**
> Which version of Ubuntu are you running? If 10.04 or newer, those directions from 2008 won't apply. You need the PAE kernel: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Thanks for your reply. Currently I want to downgrade kernel from server to desktop.

If successfully implemented, will use it

---

### Post by xavierzhao on 2011-03-09
> **oldos2er said:**
> Which version of Ubuntu are you running? If 10.04 or newer, those directions from 2008 won't apply. You need the PAE kernel: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I am running Ubuntu 10.10

---

### Post by 3Miro on 2011-03-09
Server and Desktop versions of the kernel are not upgrade/downgrade from each other. They differ in the way they schedule the CPU, but this has more to do with how a server is used as opposed to a desktop.

Go to System -> Admin -> Synaptic Package Manager, find whichever version of the kernel that you want to install, install and reboot. You should see the new version of the kernel in the Grub menu list.

---

