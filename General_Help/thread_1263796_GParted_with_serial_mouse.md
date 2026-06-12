---
title: "GParted with serial mouse"
date: 2009-09-11
forum: General Help
---

### Post by gargoyle60 on 2009-09-11
I have burnt a GParted Live CD and ran it on an old PC (PC100, Pentium II 350MHz, 750MB RAM, 4GB disk).
I was able to create two partitions – one for the main Linux distro, one for a Linux-swap.

Unfortunately, the old PC has a serial mouse which just isn’t being detected. 
I have managed to navigate around the main parts of GParted using just the keyboard, but cannot use normal mouse right-click type actions (for obvious reasons), nor can I get up to the menu line [GParted Edit View Device Partition Help].

Can anyone tell me of a way to navigate up to the menu line using just the keyboard?

Thanks

---

### Post by Psycho.mario on 2009-09-11
You don't need the GParted live cd to create partitions for any ubuntu distros. They all (?) do their partitioins for themselves

---

### Post by gargoyle60 on 2009-09-11
Yes, so I thought. But whenever I've tried loading various ubuntu/xubuntu distros they have all failed, so I wanted to manually set up the partitions in advance, hoping it would get me further into the installs by preparaing the disk (even if subsequently re-partitioned) - does that make sense?

I notice that most of the ubuntu/xubuntu installs never prompted me to set the partitions (except xubuntu9.04 which then failed with the dreaded errno 5 at 22%, but that's another issue).

I'm still trying to find a way for the various installs to recognize my serial mouse as I have the same problem as my o.p. regarding navigating using the keyboard only - during one install (I think it was ubuntu 7.10) the live cd desktop appeared but I couldn't navigate to the "install" icon so I was stuck!

---

### Post by P4man on 2009-09-11
sounds like a kernel problem with your PS/2 mouse (im assuming you know for sure the mouse and/or port work ok?).

Try adding one of these kernel parameters:
```
i8042.noloop
noapic
nolapic
```

See this page if you need help setting kernel parameters:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gargoyle60 on 2009-09-11
The serial mouse works on COM1 and it works fine with Damn Small Linux (ttyS0), so yes it is okay.

The link you gave helps, because I wasn't sure how to modify the startup command switches/options. Thanks.

Looking at various sources, I think I need something like:
    **-- mouse/device=/dev/ttyS0**

but I'm still not 100% sure. Need to experiment.

---

### Post by gargoyle60 on 2009-09-13
No good. Nothing seems to work. I give up!

---

