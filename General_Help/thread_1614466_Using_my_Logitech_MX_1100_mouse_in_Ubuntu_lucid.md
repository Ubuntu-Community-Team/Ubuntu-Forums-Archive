---
title: "Using my Logitech MX 1100 mouse in Ubuntu lucid"
date: 2010-11-05
forum: General Help
---

### Post by buddykoerner on 2010-11-05
Hello,

I am trying to get my MX 1100 Logitech mouse to work in ubuntu.

When I plugged in the mouse it worked right away. using the standard mouse configuration app none of the settings change how my mouse works... Sensitivity, buttons etc. 

I installed lomoco (for logitech mice) and cannot get it to recognise the mouse. 

when i run lomoco -i, I get the following error:

003.005: 046d:c714 Unsupported Logitech device: Unknown
003.004: 046d:c713 Unsupported Logitech device: Unknown
003.003: 046d:0b04 Unsupported Logitech device: Unknown
003.002: 046d:c526 Unsupported Logitech device: Unknown

I went into /lib/udev/rules.d/40-lomoco.rules and added the following:

# "C-BUF34",  "Receiver for MX1100 Laser"
ATTRS{idVendor}=="046d", ATTRS{idProduct}=="c526", RUN+="udev.lomoco"
Still when i run lomoco -i, It still says it is unsupported. 

I really want to get this mouse to fully work on my computer because its sooo nice,

please help,
-buddy

---

