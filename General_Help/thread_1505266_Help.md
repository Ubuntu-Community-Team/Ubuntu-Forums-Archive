---
title: "Help"
date: 2010-06-08
forum: General Help
---

### Post by oceano10000 on 2010-06-08
I have an old pentium 4 dell computer that I would use ubuntu on and hadn't used it in a while as my sister took my monitor. Now that I got it back i tried to boot into ubuntu, and the computer loads up to grub, and as soon as i try to boot into ubuntu it restarts. It does this reboot cycle no matter what I select. I tried booting from live cd's several of them. And resetting the bios, and nothing works. It even goes through a boot cycle when trying to boot from a live cd. Any ideas as to what may have caused this? It was running fine last time I ran it, which was around 4 months ago. Help fix? It was 9.04 by the way.

---

### Post by BoneKracker on 2010-06-08
If you are unable to boot from a CD, that doesn't sound like a software problem to me.

Try other bootable CDs.  If you've got a bootable floppy and a floppy drive, try that too.

---

### Post by pizza-is-good on 2010-06-08
You could disable boot from HDD in the bios and see if it still does the same.

---

### Post by oceano10000 on 2010-06-11
Yeah It doesn't boot from any bootable cd's usb's or floppys, and i did disable boot from HD and it still does the same.

---

### Post by BoneKracker on 2010-06-11
So let me get this straight... it actually loads grub, starts to boot the selected option, and then the machine abruptly restarts?

And this is the same behavior you see when you boot from the Ubuntu CD?

And you see some similar behavior when trying to boot from a Windows CD?

And you can't boot from a floppy either (which I assume would be a DOS or Win98 floppy)?

Have you tried booting into single-user mode?

Doesn't make sense to me.  Seems like something wrong on the motherboard.  Have you tried resetting the bios?  Can you run memtest?  Have you opened it up and checked to make sure everything is properly seated?  Could the CMOS battery be dying?

---

### Post by oceano10000 on 2010-06-11
Yes you have it right, it lets me select the option, the screen goes black. Then the computer just restarts abruptly. Does the same with a ubuntu live cd. And a windows cd as well. Okay and now its just getting to the boot screen and then just reboots randomly. It did that twice without even letting me select something and now it did actually go to the boot screen. I'm assuming its power supply now...

---

### Post by new_tolinux on 2010-06-11
> **BoneKracker said:**
> So let me get this straight... it actually loads grub, starts to boot the selected option, and then the machine abruptly restarts?

And this is the same behavior you see when you boot from the Ubuntu CD?

And you see some similar behavior when trying to boot from a Windows CD?
Seems to me that the boot-order in BIOS is giving HD priority as a boot-device, probably booting from CD/Floppy/Removable media is even set disabled.

I know however that if GRUB is on the harddisk that it's possible Grub forces itself to load, even when CD has boot-priority in the BIOS. The only way I found to get around that is to temporarily disable the harddisk as boot-device or using Fxx during boot to enter the boot-menu.

---

### Post by BoneKracker on 2010-06-11
> **oceano10000 said:**
> Yes you have it right, it lets me select the option, the screen goes black. Then the computer just restarts abruptly. Does the same with a ubuntu live cd. And a windows cd as well. Okay and now its just getting to the boot screen and then just reboots randomly. It did that twice without even letting me select something and now it did actually go to the boot screen. I'm assuming its power supply now...

I'm no hardware expert by any means.  Maybe one will jump in and help.  But you might want to try some of the other things I added to my post above:

reset bios (from bios menu)

reset bios (from motherboard jumper or by removing cmos battery for a minute)

memtest (if you can get it to run)

reseat ram, add-inboards, and cable connectors

try a known-good cmos battery (if machine is 5 years + old maybe buy one $15 or so)

> **new_tolinux said:**
> The only way I found to get around that is to temporarily disable the harddisk as boot-device or using Fxx during boot to enter the boot-menu.
I think he said he already tried that, unless I'm mixing up threads.

---

### Post by oceano10000 on 2010-06-11
I reset the bios from the menu already. I took out the cmos battery when I completely removed everything. Memtest checked out fine. I did a ide drive diagnostic and was fine. reseated the ram and even tried the individual sticks by themselves, i don't know what else to do. What do you think...power supply? I did disable hd boot. Still didn't work. But now its getting inconsistent boots sometimes it will make it to the boot menu sometimes it wont, sometimes it gets a little bit past to where the kernel is loading.

---

### Post by pricetech on 2010-06-11
It's a Dell, so remove the CMOS battery, disconnect the HDD and ODD, both power and ribbon cable, try booting to a floppy.  Yes it will complain, just press F1 to continue.  If it boots to a floppy, then we go on to the next step.

Let us know.

---

### Post by oceano10000 on 2010-06-11
WELL now it booted into the ubuntu live cd completely! 
I said it was getting inconsistent boots. Now it booted completely through. Don't know what changed. It hasn't rebooted yet

---

### Post by BoneKracker on 2010-06-11
This is over my head.  At this point, I would guess something on the southbridge is loose or cooked, or you need a new cmos battery.  I'll let pricetech help you.

---

### Post by oceano10000 on 2010-06-11
Crap i was in the live cd for a good 5 minutes and then it just rebooted.

Sorry all I had was a dos startup disk and now can't find it.

---

### Post by pricetech on 2010-06-11
Well, let's go from where we are.  You did manage to boot the live CD, but it only stayed up about 5 minutes and rebooted, correct ??

Have you disconnected the HDD yet ??

Go ahead and disconnect the floppy as well, leaving only the ODD connected.

Leave the CMOS battery out for now.  Yes it will complain, but it will work without it, it just won't "remember" anything.

By the way, what model Dell is it ???  What BIOS version ??

---

### Post by mr clark25 on 2010-06-11
it sounds a lot like the cpu is overheating. i think that would explain it booting into memtest (doesnt put a lot of load on the cpu) and not ubuntu (may put a load on the cpu when booting).

it could be that the thermal paste on the cpu dried up when the computer was left in storage.

what model dell is it? do you know what cpu does it have in it?

some computers will shut down / restart when the cpu gets to hot.

---

### Post by pricetech on 2010-06-11
I'll be leaving here shortly and probably won't be on the forums again until next week so here's a couple of other things.

If you're not running the latest BIOS, upgrade.  The new BIOS version will be downloadable from Dell.  Use your service tag to get the right BIOS.

See how long it runs with nothing but the ODD connected, running off the live CD.  If it stays up and running you probably have a bad HDD, though it could be just a corrupt OS.  You may have already, but if not, run the Hard Drive Diags available in the boot menu.

If it continues to reboot after a few minutes, you got hardware issues.  The first thing I would suspect is the CPU or the Motherboard.  Look for swollen or leaking capacitors on the Mobo.  Dell may replace it even if it is out of warranty.  It costs nothing to ask.

I doubt the thermal paste is the problem.  It turns chalky after a while, but it doesn't usually fail unless disturbed.  If you decide to remove the heat sink from the proc, be sure you clean both surfaces thoroughly.  I like to use alcohol to clean off any residual heat sink compound.  When you go to put the heat sink back, use just a dab of compound, about the size of a small grain of rice.

The power supply is another possibility.  Reboots usually point to the PSU.  Dell's PSUs are proprietary, so a generic replacement won't work.

Retesting the RAM wouldn't hurt, but I doubt that's the problem at this point.

Good luck with it and I'll check the thread when I return to the forum next week.

---

