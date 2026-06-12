---
title: "managing mount points"
date: 2010-09-10
forum: General Help
---

### Post by BiaxidentM on 2010-09-10
Hi,

I have a duel-boot of windows 7 and ubuntu 10.04.
I recently had to format my windows partition and reinstall windows. now every time I boot ubuntu he says he cant find the windows drive and I can choose to press S to skip and M to manual recovery which appear to do nothing. It's really annoying.
I tried to set the mount point of the windows partition from ubuntu, the windows drive was added in the media folder (which is not what I want, I want to have a windows folder on root), but it's still asks me to S or M on boot.

is there a way to fix that?

thanks

---

### Post by anglican on 2010-09-10
> **BiaxidentM said:**
> Hi,

I have a duel-boot of windows 7 and ubuntu 10.04.
I recently had to format my windows partition and reinstall windows. now every time I boot ubuntu he says he cant find the windows drive and I can choose to press S to skip and M to manual recovery which appear to do nothing. It's really annoying.
I tried to set the mount point of the windows partition from ubuntu, the windows drive was added in the media folder (which is not what I want, I want to have a windows folder on root), but it's still asks me to S or M on boot.

is there a way to fix that?

thanksThe entry in the file /etc/fstab is what is causing your annoyance. Just delete it... or change it to whatever is appropriate for your system.

H

---

### Post by BiaxidentM on 2010-09-10
> **anglican said:**
> The entry in the file /etc/fstab is what is causing your annoyance. Just delete it... or change it to whatever is appropriate for your system.

H

It worked!
I deleted the old entry and changed "/media/windows" to "/windows" in the mew entry.

Thanks allot!

---

### Post by absolutezero1287 on 2010-09-10
> **BiaxidentM said:**
> It worked!
I deleted the old entry and changed "/media/windows" to "/windows" in the mew entry.

Thanks allot!

Please mark this thread as "SOLVED" since your issue was resolved.

---

