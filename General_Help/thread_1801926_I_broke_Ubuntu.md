---
title: "I broke Ubuntu"
date: 2011-07-11
forum: General Help
---

### Post by DaveGiant on 2011-07-11
Hi,

I press alt+F5 or something and Ubuntu crashed. I held the power button down to turn the computer off then restarted it.

I now see the following.

BosyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands

I can type commands.

When I use exit I get a bunch of codes then 'panic occurred, switching back to text console'

Any ideas how I restore the GUI?

---

### Post by WorMzy on 2011-07-11
If you pressed Ctrl+Alt+F5, you just switched to a virtual terminal. Pressing Alt+F7 should get you back to the graphical interface from there; no need to hard reset.

For now though, you'll need to run fsck on your root partition. Get a LiveCD/USB (the one you used to install Ubuntu will do fine), boot into the "Try" mode, and then run

```
sudo e2fsck /dev/sd[COLOR="Red"]##[/COLOR]
```

replace [COLOR="Red"]##[/COLOR] with the actual device ID -- you can find that out by running

```
sudo blkid
```

---

### Post by DaveGiant on 2011-07-11
OK I tried what you said.

When I tried it on the first device it said:

> Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

I then ran it on the second

> /dev/sda5 is mounted

WARNING!!! The filesystem is mounted. If you continue you ***WILL*** cause ***SEVERE*** filesystem damage.

y/n

I don't know what you think but I think the second command may cause damage :).

Any other ideas?

---

### Post by WorMzy on 2011-07-11
Did you boot to the liveCD? Running those commands when you're booted into your installation is not advisable, as the warning says.

---

