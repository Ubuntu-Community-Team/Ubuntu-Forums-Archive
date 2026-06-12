---
title: "evolution-alarm-notify error"
date: 2010-03-16
forum: General Help
---

### Post by RasterBurn on 2010-03-16
hello, today my computer froze a couple times while running VBox forcing me to hit the reset button on the computer, anyways, now i am getting this error:

```

An error occurred while loading or saving configuration information for evolution-alarm-notify. Some of your configuration settings may not work properly.

```

```

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-0bZHOOZLeL: Connection refused)

```to be perfectly blunt with you, i dont know what ORBit is or what it is for and the file /tmp/dbus-0bZHOOZLeL doesn't exist on my computer (not even a symlink) the only network sharing apps that are running on the machine are SAMBA and IPP, according to synaptic i don't even have NFS installed on the computer, does anyone know how to fix this problem?

as for evolution-alarm-notify, i don't use use evolution (unless i get a pgp encrypted email) which is highly unlikely that i will get one, i am thinking, if i remove the evolution link from my notification bar will that fix the problem?

---

### Post by dcstar on 2010-03-16
> **RasterBurn said:**
> hello, today my computer froze a couple times while running VBox forcing me to hit the reset button on the computer, anyways, now i am getting this error:
.......

Resetting without proper shutdown will eventually corrupt files.

Boot off a Live CD and do a fsck on the hard disk partition(s) - either manually or using the Partition Editor.

---

### Post by peterx14 on 2010-05-12
FWIW - I've just started getting this myself, and I *never* reset without shutting down properly! Oh, and I also don't use Evolution either.

A quick google pulls up a [bug for this](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/501692) and the comments mention disabling the Evolution Notifier in Startup Applications. And [this page](http://crimm.me/2010/02/ubuntu-9-10-error-popup-evolution-alarm-notify.html) says how to solve the problem by removing the ~/.gconfd/saved_state file.

I've not yet tested either of these myself however.

As for causes... I run Ubuntu 9.10 and have full desktop effects enabled, and I have 3 desktops available. Every now and then -- usually after I've left the computer alone for an amount of time -- I'll notice that desktop effects aren't working and I'm now down to 2 desktops! Everything else otherwise works, there's no data loss, and I can fix it by logging out and logging back in.

However, today this happened immediately after I'd booted and logged in. So I logged straight out again... but it's possible that some of Gnome hadn't completed loading when I logged out, so maybe that's what caused something to get screwed up? And it's when I logged in the second time, when I first got this message.

---

