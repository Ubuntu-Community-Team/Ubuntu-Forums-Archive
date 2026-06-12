---
title: "Monitor Frequency out of Range, 10.04 *URGENT*"
date: 2010-10-16
forum: General Help
---

### Post by Little Blue on 2010-10-16
Hi,

I've recently reinstalled a computer with 10.04 for my parents to use, and it worked fine at mine, but after transporting it to theirs and hooking it up to their existing monitor it doesn't seem to work anymore!

Well, it boots and I hear it login but I don't get a splash screen and at some point between the bios and the login sound it comes up with Frequency out of Range. On the warning message it displays a frequency of "72.9 kHz / 90.2 Hz" but in the monitor settings its reporting that its operating at horizontal 64,0 kHz and vertical 60.0 Hz. I also don't get any splash screen when starting up, just a flashing _ before the monitor stops things

What I can do however is drop into a tty shell (alt+ctrl+2) and login to the shell but don't really know how to change things from there.

Having googled things a bit I've found references to xorg.conf but there's no such thing on my system so I can't edit that to fix this. Likewise I also have found references to fiddling with grup to get into the recovery, but grub doesn't even appear when I boot and I don't know what to press to get it to drop into its menu...

This is really urgent as I need to go home tomorrow at the latest and I want to get my parents system working before then. I also have no spare monitors here and I didn't think to bring with me a liveCD to fiddle with things (only a UNR netbook which I'm posting this from), so the tty is the only access I have to the machine.

Some specs: Ubuntu 10.04. ATi Radeon 9100 IGP, no proprietary drivers are installed, I also don't think (or at least I'm not sure) that any even exist in the repositories either... The monitor is an old CRT that still works beautifully and whose replacement is not an option.

Any help would be massively appreciated!

Cheers.

---

### Post by Little Blue on 2010-10-16
Ah, ok, this is kind of embarrassing now. An hour after posting this I've managed to fix this, kinda.

For reference, this is what I did:

After looking up how to get the grub menu to appear I discovered where the grub configuration is kept. In the console edited the /etc/default/grub file and replaced "quiet splash" with "nomodeset". After that I ran update-grub and rebooted.

This managed to let me login and manually set my monitor refresh rate down a few notches (its now at 60kHz), for the two accounts on the machine (mine and my parents). I then reversed my changes to the grub config reconfigured and rebooted and it works fine now.

Except, well, my parents autologin, so when I logout of that to get into my account, the login screen is still out of the frequency range (fortunately I can guess the keystrokes to login :p). I have to fiddle with gdm somehow to fix that and I haven't the foggiest how to do that!

I'll figure it out, and my initial problem is solved so I'm marking this thread solved.

---

