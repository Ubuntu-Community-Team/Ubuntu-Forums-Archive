---
title: "Freeze with Caps and Scroll Lock blinking"
date: 2009-09-14
forum: General Help
---

### Post by lospo on 2009-09-14
Hi and good morning,
I've got a trouble on a fresh install of Ubuntu 9.04: sometimes (random) il freeze leaving only caps lock and scroll lock blinking.

I've read something about a WiFi card, but i haven't one...

The system is an Intel Core Duo (6320??) with 1g ram and an integrated lan (cabled) card.

Can someone help me ???

---

### Post by P4man on 2009-09-14
ew, blinking leds is a kernel panic. Its roughly like a windows blue screen of death, and can be very hard to diagnose and fix.

Is this the first time you are trying linux on that machine? Or did you use previous versions without that problem?

anyway, there are many possible causes, but the most frequent cause in my experience is a buggy ACPI BIOS. You could check if there is a bios update for your machine, or you can try a few things that may work around the problem.

Have a look here:
[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

It explains how to set boot options. In the example they set 'vga=775', instead of that, try booting with any of these options:

```
noapic
nolapic
noacpi
```

try them one at a time. The options you set there are only active for 1 boot, so if it freezes, and you have to reboot, it will have forgotten about it, try the next one.

Good luck :s

---

### Post by fh_scott on 2009-09-14
I have a Vostro 1500 that does that when it overheats.

---

### Post by lospo on 2009-09-27
Excuse my delay, i have no flat connection....

No, the pc isn't overheat, windows stay up entire weeks....

But i can see a strange thing: it freeze when i play video or MP3, can it suggest something???

Thanks

---

