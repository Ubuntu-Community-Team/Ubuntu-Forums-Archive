---
title: "Acer Aspire Video/Mouse/Who knows what else..."
date: 2011-11-25
forum: General Help
---

### Post by cwwilson721 on 2011-11-25
Had 11.04 64bit installed, just did a 'clean' 11.10 install.
Main display on Laptop does not work, but external was working.
External display works fine using Live CD

After install and first reboot (all working okay-ish), I installed proprietary Nvidia drivers, then rebooted.

When Ubuntu comes up, the display switches from the external (which can/does show BIOS, etc), to the laptop display (which does not work).

So, I'm stuck.

How do I convince the *installed* Nvidia Setiings program to use the external monitor while booting the system from a Live CD?

 Is there a setting in xorg.conf I can edit (or add) to fire up the external when x starts, and not default to the internal monitor?

Thanks in advance

---

### Post by fooman on 2011-11-25
hi,  not sure of any nvidia or xorg.conf settings to do what you want....but i know that a few of the laptops that i have owned,  had an "f" key (very top row of keyboard) that doubled as a switch for the external/laptop display.

does your laptop have one of these?  ...it may have to be pressed in sync with the "fn" key in order to work.

---

### Post by cwwilson721 on 2011-11-25
On the Acer 4350 it's the fn+f5 key...that didn't work. (In the first post, I do say the display 'works' in BIOS, etc, up to when the Xsever starts. So that eliminates the hardware switch)

I ended up copying a xorg.conf file from another computer that had dual-display Nvidia graphics, with the following added to the original xorg.conf in the "Screen" subsection:

```
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: NULL"
```

All working now, at least on video front.

Now to get the touchpad working... And the builtin wireless..

But those are for another thread, and another day, after searching first

---

