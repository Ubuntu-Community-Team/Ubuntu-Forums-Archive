---
title: "X wont start when a monitor isn't plugged in at boot time"
date: 2010-06-18
forum: General Help
---

### Post by stephanecharette on 2010-06-18
I have a system I use as a file server running Ubuntu 10.04.  I don't have a screen hooked up to this system.  When this system reboots, if there is no screen, X wont start on it.  This then prevents me from using VNC to get to the desktop.

If a monitor is plugged in at the time it boots, then everything works, and I can then remove the monitor.  But moving this monitor between computers and crawling under desks is not enjoyable.

How can I fix this so X starts on boot even when no monitor is plugged in?

The error I get in /var/log/Xorg.log* looks like this:

[INDENT]
grep -EnC2 "EE|WW|fatal|error" /var/log/Xorg.0.log
...
331- (II) Primary Device is: PCI 01@00:00:0
332- (II) [KMS] Kernel modesetting enabled.
333: (WW) Falling back to old probe method for vesa
334: (WW) Falling back to old probe method for fbdev
335- (II) Loading sub module "fbdevhw"
336- (II) LoadModule: "fbdevhw"
--
362- (II) RADEON(0): Output DVI-0 disconnected
363- (II) RADEON(0): Output DVI-1 disconnected
364: (WW) RADEON(0): No outputs definitely connected, trying again...
365- (II) RADEON(0): Output DVI-0 disconnected
366- (II) RADEON(0): Output DVI-1 disconnected
367: (WW) RADEON(0): Unable to find initial modes
368- (II) RADEON(0): mem size init: gart size :1fdff000 vram size: s:10000000 visible:ffc0000
369- (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
--
384- 	compiled for 1.7.6, module version = 2.5.0
385- 	ABI class: X.Org Video Driver, version 6.0
386: (EE) RADEON(0): No modes.
387- (II) UnloadModule: "radeon"
388- (II) UnloadModule: "exa"
-- 
390- (II) UnloadModule: "fb"
391- (II) Unloading /usr/lib/xorg/modules/libfb.so
392: (EE) Screen(s) found, but none have a usable configuration.
393- 
394: Fatal server error:
395- no screens found
[/INDENT]

I assume there is something I can edit in /etc/X11/xorg.conf to force it to come up in 1024x768 or some such standard resolution even if no screen is detected.  At the moment, that file is very bare with a 3-line "Device", and 3-line "Monitor", and a "Screen" that points to the empty Device and Monitor.

---

### Post by stephanecharette on 2010-06-18
I spent way too much time on this problem over the past few days...but I found the solution.  Seems this may be a known issue when working on headless systems.  Here is what I did to solve the problem:

[LIST=1]
[*]edit /boot/grub/menu.lst
[*]find the line that says:
[*]    [FONT="Courier New"]# defoptions=quiet splash[/FONT]
[*]change that line to say:
[*]    [FONT="Courier New"]# defoptions=quiet splash nomodeset[/FONT]
[*]save and exit from the editor
[*]run this command:  [FONT="Courier New"]sudo update-grub[/FONT]
[/LIST]

Then reboot.  Some of this is indirectly mentioned in passing in the Lucid release notes:  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture) though they don't specifically talk about headless systems.  And I don't seem to have a /etc/default/grub file, perhaps because this system is an upgrade and not a fresh install of 10.04?  Regardless, I hope this helps someone else.

---

### Post by stephanecharette on 2010-10-18
As another possible solution:  I converted an old 10.04 desktop to a headless system today, and ran into a similar problem.  Wouldn't boot correctly into X after the screen was removed.  This is what /var/log/Xorg.0.log ended with:

[INDENT](EE) May 16 14:08:01 NVIDIA(0): No display devices found for this X screen.
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.[/INDENT]

The solution to that one was to modify /etc/X11/xorg.conf and add this line:

[INDENT]Option "ConnectedMonitor" "CRT"[/INDENT]

to '[FONT="Fixedsys"]Section "Device"[/FONT]' just below the [FONT="Fixedsys"]Driver "nvidia"[/FONT] line.

Again, logging it here on the forum in case someone finds this through Google and it helps them out.

---

### Post by Jumphog on 2010-12-29
Thanks for these solutions. Ive just done a fresh install that wouldnt work without a monitor, all this autodetect stuff seems a bit of a step backwards. With the nvidia driver installed and both changes made it'll now get to a desktop without a monitor plugged in.

For info the "ConnectedMonitor" option doesnt work with the fbdev driver, so lucky I had nvidia graphics...

---

### Post by audiomick on 2010-12-29
My thanks too. I have a laptop here with a screen problem. I don't know if I can be bothered trying to do anything with it (it's old, and has had a hard life...) but your solutions may be useful.

---

### Post by Chaosratt on 2011-02-02
> **stephanecharette said:**
> I spent way too much time on this problem over the past few days...but I found the solution.  Seems this may be a known issue when working on headless systems.  Here is what I did to solve the problem:

[LIST=1]
[*]edit /boot/grub/menu.lst
[*]find the line that says:
[*]    [FONT="Courier New"]# defoptions=quiet splash[/FONT]
[*]change that line to say:
[*]    [FONT="Courier New"]# defoptions=quiet splash nomodeset[/FONT]
[*]save and exit from the editor
[*]run this command:  [FONT="Courier New"]sudo update-grub[/FONT]
[/LIST]

Then reboot.  Some of this is indirectly mentioned in passing in the Lucid release notes:  [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture) though they don't specifically talk about headless systems.  And I don't seem to have a /etc/default/grub file, perhaps because this system is an upgrade and not a fresh install of 10.04?  Regardless, I hope this helps someone else.

Any idea on how to do this with the new Grub 2 install?

---

