---
title: "System not booting, very broken. gconftool-2 symbol lookup error. Any help appreciate"
date: 2010-10-07
forum: General Help
---

### Post by supergrover1981 on 2010-10-07
Hi folks,

I've asked around a bit on this, but so far no luck. If anyone has any ideas, I'd be very appreciative.

This morning I installed a few synaptic packages without really looking at what they were on my 10.04-64 box, then walked away while they installed. When I came back 20 minutes later the screen was black (mouse cursor still present). I couldn't recover any functionality, so I hard-reset the machine.

From there, upon loading, I was getting an "error on sda7: check forced" message. That ended in a message saying "FSCK must be run manually". 

I couldn't get into recovery console or single-user mode, but managed to run fsck via a LiveCD. From there, machine still wouldn't boot up. It got to "Checking battery status [OK]" before freezing.

I still can't get into the "Failsafe graphics mode", but I have recovery access via console. I have 15 broken packages, all of which return a dpkg failure message.

So, I tried running sudo dpkg --reinstall -a, and got 

```
gconftool-2: symbol lookup error: /usr/lib/libgobject-2.0.so.0: undefined symbol: g_regex_unref
```

And now I'm stumped. If anyone has any ideas I'd be very appreciative - I'd really really love to recover this machine.

Thanks,
          - SuperGrover

Note: The fact that it happened during/after an update may be coincidence. The HD has also been acting a little screwy the past 36 hours: it seemed to lose a few vim configuration files a few hours earlier, gnome-terminal preferences seemed to be reset, etc.

---

### Post by quixote on 2010-10-09
Have you run ```
sudo dpkg --configure -a
```I doubt it'll fix problems this far-reaching, but everything's worth a try.

Did you fix whatever errors fsck found?

Do you know how full that drive is?  If it gets much over 95%, you can get these sorts of huge problems and not a single error message that tells you what the real issue is.  The command to check is```
df -h
```If the disk is too full, delete whatever you can think of.  One dir that gets large that can be safely dumped because it will simply be rebuilt is ~/.thumbnails in your home dir.

---

