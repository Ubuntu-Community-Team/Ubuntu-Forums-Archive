---
title: "Karmic Upgrade: Disabling screen auto-brightness on Asus M50VC"
date: 2009-11-03
forum: General Help
---

### Post by supergrover1981 on 2009-11-03
Hi gang,

Been using Ubuntu on my Asus M50-VC since Gutsy. I've always had a problem with auto-brightness going crazy.

The easiest way to get around it was to add a bash script such as:

```

echo 0 > /sys/devices/platform/asus-laptop/ls_switch

```

But under karmic, that script fails due to insufficient permissions.

I've tried chmodding ls_switch, but each time the computer restarts, it goes back to its original permissions.

Just to clarify: I can chmod ls_switch, run the echo command & it works fine....but I need to do it manually every time I restart. Any suggestions?

Cheers,
       - Supergrover

---

### Post by TruePhase on 2009-11-03
I just ran in to a similar issue on my Asus M50v after upgrading to Karmic. Previously I disabled auto-brightness with the following in my /etc/rc.local:

```

echo 0 > /sys/devices/platform/asus-laptop/ls_switch
```

This stopped working after upgrading. I noticed that the hyphen between "asus" and "laptop" changed to an underscore in Karmic. Replacing the above in rc.local with this:

```

echo 0 > /sys/devices/platform/asus_laptop/ls_switch

```

automatically disables auto-brightness on each boot.

hope this helps!

---

