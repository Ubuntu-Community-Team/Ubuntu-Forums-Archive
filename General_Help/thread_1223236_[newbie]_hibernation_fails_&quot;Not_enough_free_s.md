---
title: "[newbie] hibernation fails: &quot;Not enough free swap&quot;"
date: 2009-07-25
forum: General Help
---

### Post by tlroche on 2009-07-25
summary: Linux desktop newbie has ThinkPad Z61t with (wubi-installed) xubuntu-9.04 which fails to hibernate with the error "Not enough free swap". How to fix?

details:

My ThinkPad Z61t (one of the last pre-Lenovo models) came with winxp (currently SP3) to which I recently added xubuntu-9.04 via wubi. Both OS are patched up-to-date. The Z61t will suspend in xubuntu-9.04 without error, and will both suspend and hibernate in winxp-sp3 without error. But attempting to hibernate in xubuntu-9.04 gets the error "Not enough free swap": the error is barely/briefly visible when attempting to hibernate from X, but clear when running

$ sudo pm-hibernate

from tty1. I note

```
tlroche@tlrZ61t:~$ free -m
>              total       used       free     shared    buffers     cached
> Mem:           993        953         40          0        202        353
> -/+ buffers/cache:        396        596
> Swap:          255          7        248
tlroche@tlrZ61t:~$ swapon -sv
> Filename                              Type            Size    Used    Priority
> /host/ubuntu/disks/swap.disk          file          262136    7196    -1
```

Normally I would just suspend, but my battery recently failed, so that's not normally an option. I'm wondering (given that I'm new to running linux on my desktop, though I've shelled into servers for a long time):

0 Is this swap.disk a real file? or some kind of wubi fu?

Presuming it's a real file, and that increasing its size will enable the Z61t to hibernate from xubuntu-9.04,

1 How should I make swap.disk bigger? and exactly how much bigger?

Alternatively, what do I need to do to fix this problem? (Besides buy a new battery :-(

Your assistance is appreciated, Tom Roche <Tom_Roche@pobox.com>

---

### Post by Revolutionary101 on 2009-07-25
This is your problem:

During hibernation your computer writes all the RAM aka Memory to the Swap partition on your Hard Drive. Your computer is telling us that it had 953 MB used on your RAM. The Swap partition is 255 MB in size. Your computer can't fit all of the 953 MB worth of RAM on the 255 MB Swap partition. I suggest resizing your swap partition to make it bigger.

To make the swap space bigger is to buy a flash drive or external hard drive and formatting it so it can be used as swap space or reinstall Ubuntu and let Ubuntu use more space on the Hard Drive.

---

### Post by nmaster on 2009-07-25
wubi can't hibernate. i think its on the faqs page of the wubi site.

---

### Post by Revolutionary101 on 2009-07-25
> **neal.m.master said:**
> wubi can't hibernate. i think its on the faqs page of the wubi site.

Yeah I forgot about that.

---

### Post by tlroche on 2009-07-26
> **neal.m.master said:**
> wubi can't hibernate. i think its on the faqs page of the wubi site.

Yep :-(

```
http://wubi-installer.org/faq.php
> Hibernation is not supported under Wubi,
```

---

