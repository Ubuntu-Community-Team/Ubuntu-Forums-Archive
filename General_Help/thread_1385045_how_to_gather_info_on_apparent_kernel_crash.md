---
title: "how to gather info on apparent kernel crash"
date: 2010-01-19
forum: General Help
---

### Post by spip on 2010-01-19
I've had ubuntu on an older toshiba laptop for some time now.  Every now and then, I encounter a complete lockup of the machine.  Clearly this isn't a userland crash, can only be kernel side.

This just happened now, and I would like to gather some info on what could have possibly happened.

However, when I reboot, there is nothing in /var/log/message.log, /var/log/dmesg, or any of the older /var/log/dmesg.*.gz files.  Most HOWTO's on how to diagnose a kernel oops give an example of what a resulting trace looks like in dmesg, but I don't see any of that.

Could it be that:

1. The kernel is not causing an exception, but is rather locked in an infite lock spin?  (a soft lock, I guess) -- This wouldn't be a crash per se.  And the computer's fan did kick into high gear meaning the machine was executing some code (whereas I believe most exception handlers would then start running NOOPS after having printed the necessary diagnostic message)

2. I am looking in the wrong place?  Although most help resources point to /var/log/dmesg

3. Something else?

Also, just to be sure, when you normally encounter a kernel crash, upon reboot, are you supposed to be able to recover anything from dmesg?  Is there always a rollback of the previous dmesg into dmesg.0.gz ?

thank you,
spip

P.S: If it matters, in this case the crash occured while I was copying data to this laptop via ssh.  The only really active applications would have been sshd.  I had nothing else started (on top of whatever the system runs by default) and was in an empty ubuntu gnome desktop.  Because this has to be kernel-side, sshd doesn't do anything from the point of view of the kernel (other than executing) except for lost of network reads/writes.

---

