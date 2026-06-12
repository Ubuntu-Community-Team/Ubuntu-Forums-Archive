---
title: "NEED pc speaker to work again."
date: 2010-08-30
forum: General Help
---

### Post by Ubunthree on 2010-08-30
I need the console beep for audible message alerts when I have the speakers disconnected, or their volume turned down late at night, or when I'm using headphones and set them down to do something else. I was able in the past to get it working after following numerous instructions in other threads, and it worked for a while, but now it has gone silent again and I can't seem to do anything to get it back. It beeps when the computer starts up, so I know the speaker itself is functional. Here is what I had to do originally:

In etc/modprobe.d/blacklist.conf, commented out this line:
[COLOR="Green"]# blacklist pcspkr[/COLOR]

Added to /etc/rc.local script:
[COLOR="#008000"]rmmod pcspkr
modprobe pcspkr[/COLOR]

Added to etc/modules:
[COLOR="Green"]pcspkr[/COLOR]

Added command to startup applications:
[COLOR="#008000"]xset b on[/COLOR]
(After the beep died again, I tried [COLOR="Green"]xset b 100[/COLOR] instead, but no effect.)

Entering this in a terminal:
[COLOR="#008000"]lsmod | grep pcspkr[/COLOR]
...returned this:
[COLOR="#008000"]pcspkr                  1518  0[/COLOR]

Entering this in a terminal:
[COLOR="#008000"]rmmod pcspker[/COLOR]
...returns this:
[COLOR="#008000"]ERROR: Module pcspker does not exist in /proc/modules[/COLOR]
I don't remember whether or not that was the output when the speaker was working. In any case, looking at /proc/modules I see this line in there:
[COLOR="#008000"]pcspkr 1518 0 - Live 0xf9c13000[/COLOR]

Installed "beep" through Synaptic. After a couple of reboots it seemed to work fine. I set Pidgin to call this script whenever a message came in:

[COLOR="#008000"]#!/bin/bash

beep -f 1175 -l 100 -n -f 1480 -l 100 -n -f 1760 -l 100 -n -f 2350 -l 100
[/COLOR]
This sounded a quick D-major arpeggio which was reasonably pleasant and could usually be heard from across the room. A few days ago, though, it stopped working. I've gone over everything that I can remember doing before, and am at a loss. The only change that I can remember making to the system before this came up was that I installed fluxbox out of curiosity, but I don't know whether that could have had anything to do with this. The beep remains broken in GNOME as well.

Thanks!

---

