---
title: "Oneiric Ocelot will not boot."
date: 2011-10-15
forum: General Help
---

### Post by quequotion on 2011-10-15
I have to say I'm not surprised.
This is the 5th version of Ubuntu in succession to fail immediately after install.
I am tired of this.
I want, just once, to not have a headache after every minor or major upgrade.

This time, boot failed with a garbled Plymouth, so I tried to add "nosplash" in GRUB (thanks for changing the access key to grub by the way... why?).
I expected "nosplash" to give me a wall of text explaining everything happening at boot, but instead I have a blinking cursor that never stops blinking.

I tried f2, Alt+f2 and even Ctrl+Alt+f2 but the screen will not change.

What should I do to at least find out what the problem is?

---

### Post by effenberg0x0 on 2011-10-15
When you hold shift at the PC boot (too see Grub) and choose recovery mode or the old Kernel, does the PC boot normally? 

If it does, we can fix things from there.

Regards,
Effenberg

---

### Post by quequotion on 2011-10-16
> **effenberg0x0 said:**
> When you hold shift at the PC boot (too see Grub) and choose recovery mode or the old Kernel, does the PC boot normally? 

If it does, we can fix things from there.

Regards,
Effenberg

Thank you for the reply!

It was there, but it didn't work any better than the 3.0 kernel.

Luckily, I found I could get into text mode if i removed the "set linux-gfx-payload" line and kernel options "quiet splash vt.handoff=7" (note, i just typed those from memory and they may not be exact). X would not start as it was trying to load nouveau and nvidia simultaneously (although nouveau was not installed...)

I ended up using aptitude to discover a lengthy chain of broken dependencies (which neither apt nor ubuntu's upgrading program noticed..) and removed nearly half the packages on my system. After reinstalling them, I was able to get Ubuntu to boot.

For the first time in ages I have a proper boot splash and I can use the proprietary drivers.

Unfortunately, now the desktop is in a horrible state as compiz will not redraw the screen without some user action (like draging a window or rotating the cube). Menus and panels are inoperable in this state and work is very slow in any window.

Unity 2D will have to suffice for the moment.

---

### Post by quequotion on 2011-10-16
Marked as solved because I no longer have this issue.

Unfortunately I don't know exactly what resolved it.

If anyone has the same problem after upgrade, try aptitude and see if there are numerous broken dependencies and unnecessary i386 packages.

---

