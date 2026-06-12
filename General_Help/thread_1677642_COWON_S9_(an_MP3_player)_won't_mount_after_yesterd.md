---
title: "COWON S9 (an MP3 player) won't mount after yesterday's Lucid upgrades"
date: 2011-01-29
forum: General Help
---

### Post by OrangeVixen on 2011-01-29
I have a COWON S9 (an MP3 player that normally mounts like any memory stick) and I noticed that when I connect it, it won't auto mount and does not seem to be recognized by Lucid after yesterday's kernel updates.

This player has always auto-mounted without any problems until yesterday's (2011 Jan 27) kernel updates. I rebooted and made sure I'm on the latest kernel.


Anyone else experiencing things not auto mounting? I can't get it to manually mount either. It doesn't seem to be recognized at all now.

---

### Post by Jahid65 on 2011-01-29
If you have any old karnel, use that to log in.

---

### Post by OrangeVixen on 2011-02-16
I figured out the problem, appearently a package called the Linux firmware was upgraded.

I rebooted but it does not seem to be enough.

You actually have to shutdown, turn off your computer (UNPLUG as needed), plug back in, turn on computer, boot.

Then it works.

For some reason, the restart/reboot does not clear something that causes the USB devices to become funny but only seems to affect USB MP3 players.

---

