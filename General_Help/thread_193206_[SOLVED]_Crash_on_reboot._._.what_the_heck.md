---
title: "[SOLVED] Crash on reboot. . .what the heck?"
date: 2006-06-09
forum: General Help
---

### Post by RavenOfOdin on 2006-06-09
k, well, I upgraded to Dapper a while ago and I've now been experiencing this weird problem when I try to reboot my system. Every couple of reboots, I crash.

Well, not really. I get past the "End Current Session/Turn off Computer" box and all that good stuff. . .but when it should be going through the shutdown operations the computer just sits there and doesn't do anything, after 10 minutes of which I have to turn off the power manually.

Then, when I type:

```

last -aix

```

in console, I get a notice which says I've been up from X time until a crash, then a "reboot" notice directly above it.

Checking kern.log doesn't give me anything other than a tulip_stop_rxtx() failed issue with my Ethernet connection. dmesg doesn't give me anything either.

I've been using KDE, with KDM as my default display manager, and have recently tried to install Guarddog so I can remove a Firestarter which isn't registered as a package.

Someone help, this is getting annoying.

---

