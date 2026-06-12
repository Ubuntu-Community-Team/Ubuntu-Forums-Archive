---
title: "Suspend/hibernate instantly reboots computer"
date: 2010-10-25
forum: General Help
---

### Post by Shinoda on 2010-10-25
Hey, all.

A weird problem arose a few months ago in my box and has plagued me ever since: the PC immediately reboots whenever I try to suspend or hibernate Ubuntu. It's actually instantaneous, as if I pushed the reset button.

Way more days into googling than I wished I had to, I have tried just about every solution related to suspension/hibernation problems, but none really applies to the exact situation I'm experiencing, since most are about being unable to resume after suspending/hibernating, and in my case it seems the system is instantly killed and therefore doesn't even start said operation.

After rebooting, applications behave exactly as when the PC is hard-reset, which I think is an indication that running processes aren't being properly terminated and the system is just going down abruptly (if the less-than-a-second it takes to go down and restart the boot sequence isn't obvious enough).

Before you ask:

[LIST=1]
[*]everything was working fine before;
[*]upgraded to Maverick but the problem remained;
[*]every suspend/hibernate method that I know of (GUI, CLI) does the same;
[*]can't easily test in another OS since I only have Ubuntu installed (no dual-boot or the like);
[*]swap partition is larger than RAM;
[*][FONT=Courier New]/etc/initramfs-tools/conf.d/resume[/FONT] is pointing to the correct swap UUID;
[*]tried several [FONT=Courier New]SUSPEND_METHODS[/FONT] and video-related options in [FONT=Courier New]/etc/default/acpi-support[/FONT];
[*]enabling/disabling the [FONT=Courier New]acpid[/FONT] and [FONT=Courier New]acpi_support[/FONT] services in BUM (Boot-Up Manager) has no effect;
[*]enabling/disabling BIOS STR (Suspend-To-RAM)-related options has no effect;
[*]unsetting [FONT=Courier New]NvAGP[/FONT] or setting it to [FONT=Courier New]1[/FONT] in [FONT=Courier New]/etc/X11/xorg.conf[/FONT] has no effect;
[*]adding/removing the [FONT=Courier New]agpgart[/FONT] and [FONT=Courier New]intel_agp[/FONT] modules to [FONT=Courier New]/etc/modprobe.d/blacklist.conf[/FONT] has no effect;
[*]installing the [FONT=Courier New]hibernate[/FONT] package has no effect;
[*]not sure what I'd be looking for, but nothing strikes me as relevant in [FONT=Courier New]/var/log/messages[/FONT].
[/LIST]
This is really strange. May it be a hardware failure of some sort? What else can I try to work this one out or at the very least understand what's happening?

Thank you so much for any help.

---

### Post by dcstar on 2010-10-25
> **Shinoda said:**
> Hey, all.

A weird problem arose a few months ago in my box and has plagued me ever since: the PC immediately reboots whenever I try to suspend or hibernate Ubuntu. It's actually instantaneous, as if I pushed the reset button.
..........
This is really strange. May it be a hardware failure of some sort? What else can I try to work this one out or at the very least understand what's happening?

Thank you so much for any help.

Make about ~10GB of space on your disk and do a fresh test 10.10 install and see what happens when you boot off it.

If that works ok then there is a bad config in your existing install.

---

