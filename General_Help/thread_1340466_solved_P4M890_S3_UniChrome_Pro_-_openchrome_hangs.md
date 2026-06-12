---
title: "solved: P4M890 S3 UniChrome Pro - openchrome hangs"
date: 2009-11-28
forum: General Help
---

### Post by nyxerebos on 2009-11-28
I'm posting this here because this here because I couldn't find this information anywhere else.

I just upgraded to 9.10 and was having a bizarre problem with X, I could log in and would get a desktop but the machine would lock up for a few seconds whenever drawing to the screen.  For example, trying to drag an icon on the desktop would cause the processor use to jump to 100% for 10-15 seconds, then the mouse would reappear at the new position and the icon had moved.  Opening windows was as normal, but moving or redrawing them would cause the same problem, X server eating a bunch of CPU.  Could open web pages in firefox but not scroll them, etc, X completely taking over the processor for a little while.  Painful to use.

My default xorg.conf was this:

# xorg.conf (X.Org X Window System server configuration file)
# ... etc ...
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Note that "sudo dpkg-reconfigure -phigh xserver-xorg" didn't work for me, did nothing.

Apparently my video card is supported by openchrome so I specified the driver (installed by default in 9.10)

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "openchrome"
EndSection

The problem was exactly the same, leading me to believe that it had been using the openchrome driver all along.  I never had to specify a driver for 9.04, it just worked.

Anyway, changing the driver to "vesa" solved the problem, here is my current xorg.conf

# xorg.conf (X.Org X Window System server configuration file)
# .. etc ..
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)"
    Driver        "vesa"
    BusID        "PCI:1:0:0"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "VIA Technologies, Inc. P4M890 [S3 UniChrome Pro] (rev 01)"
EndSection

Am not looking for support, just posting so that anyone else with a P4M890 can find it in the search / Google.

---

