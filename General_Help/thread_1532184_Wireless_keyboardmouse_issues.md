---
title: "Wireless keyboard/mouse issues"
date: 2010-07-16
forum: General Help
---

### Post by SeanCly10 on 2010-07-16
Here's the leadup: my wife wanted to put a widget manager on my desktop so she could have a particular type of widget. Gdesklets and screenlets either didn't work or didn't have the kind of widget she wanted, so I decided to try Google Gadgets.

I installed it without incident, but when I ran the program for the first time, my wireless keyboard and mouse died instantly; I had to plug in a wired mouse to shut the machine down. The restart didn't bring them back, and I needed to drag a wired keyboard out of the attic to start searching for an answer.

Several different solutions didn't help anything either, and I was about set to pull my hair out when *facepalm* I realized I should try removing Google Gadgets. In doing so, I found that the wireless keyboard had come back, all on its' own...no clue why, since I had done nothing shortly before to bring it back. Removed Gadgets, mouse still gone, and now I'm out of ideas.

I know that it's being detected in some way, although it's hard to say for sure, since my setup is a Logitech EX100 keyboard/mouse combo, and lsusb shows just the receiver:

```
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser[/COLOR]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

Dunno why it's listed as an LX710, but whatever. Trying to reconnect the mouse to the receiver does no good, although it does fine for the keyboard. I'm running both Ubuntu Lucid and Linux Mint Isadora, with the same issue in both. I'm at a loss. Anyone with any ideas?

---

### Post by dcstar on 2010-07-16
> **SeanCly10 said:**
> 
........
Dunno why it's listed as an LX710, but whatever. Trying to reconnect the mouse to the receiver does no good, although it does fine for the keyboard. I'm running both Ubuntu Lucid and Linux Mint Isadora, with the same issue in both. I'm at a loss. Anyone with any ideas?

Boot of a Live CD and if the keyboard and mouse work then something has broken the installed system.

If the mouse still does not work then replace the batteries and re-associate it to the base unit.

---

