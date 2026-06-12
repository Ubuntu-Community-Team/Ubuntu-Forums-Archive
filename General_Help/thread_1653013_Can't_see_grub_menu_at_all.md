---
title: "Can't see grub menu at all"
date: 2010-12-26
forum: General Help
---

### Post by DAC1138 on 2010-12-26
I recently moved back to linux after a brief on/off affair with Windows. I just installed Ubuntu Maverick on my netbook (hp mini 1000) and I don't see a grub menu at all. I'm not dual booting. Linux is the only OS on this machine.

I tried installing the startup-manager program and changing screen resolutions and even the delay time, but I don't see anything. I did some forum searching and some threads mentioned holding the shift key. That's a no go as well. The computer totally ignored the shift key and doesn't do anything.

I'm trying to get a custom kernel built, but the first step is making sure I'm going to be able to boot it.

---

### Post by mcduck on 2010-12-26
Just press the Shift key during boot and the Grub menu will appear. (yes, it really *is* the correct key. If it doesn't work for you, you are pressing it too late or something.)

Of course you can also just edit /etc/default/grub to make the menu always visible...

---

### Post by DAC1138 on 2010-12-26
> **mcduck said:**
> Just press the Shift key during boot and the Grub menu will appear. (yes, it really *is* the correct key. If it doesn't work for you, you are pressing it too late or something.)

Of course you can also just edit /etc/default/grub to make the menu always visible...

I don't think I did something correct, but I did edit /etc/default/grub and corrected this line: 'GRUB_HIDDEN_TIMEOUT_QUIET=false'

I then existed and ran update-grub.

Upon bootup I noticed no difference. So I rebooted a second time and tapped shift like I was playing a pinball machine. Still no change.

-edit-
I got it. I went back and took another look and saw some other lines that mentioned "hidden", so I changed those. Here is what the top of my config is set for, for those of you that have this problem in the future:

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=5
#GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=5
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=" vga=792 splash"

---

### Post by Quackers on 2010-12-26
I think you hold the shift key down during boot. It looks for a depressed shift key.
Unless grub has changed, this is from drs305's guide regarding the hidden timout

"GRUB_HIDDEN_TIMEOUT=0 [ Note: This setting only applies to computers with only a single operating system. ]

    The hidden timeout option allows a screen to be displayed without the Grub 2 menu, awaiting input from the user for a given number of seconds. It is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
    On single-OS computers:
        The menu will be hidden unless the user adds a # symbol to the beginning of this line ( # GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
        If a background image is designated in 05_debian_theme it will be displayed rather than a blank screen during a hidden menu timeout."

---

### Post by DAC1138 on 2010-12-26
> **Quackers said:**
> I think you hold the shift key down during boot. It looks for a depressed shift key.
Unless grub has changed, this is from drs305's guide regarding the hidden timout

"GRUB_HIDDEN_TIMEOUT=0 [ Note: This setting only applies to computers with only a single operating system. ]

    The hidden timeout option allows a screen to be displayed without the Grub 2 menu, awaiting input from the user for a given number of seconds. It is available to single-OS computers - if multiple OS's are known to Grub 2, this option is bypassed.
    On single-OS computers:
        The menu will be hidden unless the user adds a # symbol to the beginning of this line ( # GRUB_HIDDEN_TIMEOUT=0 ) and the GRUB_TIMEOUT value is greater than 0.
        If a background image is designated in 05_debian_theme it will be displayed rather than a blank screen during a hidden menu timeout."

The first few times I tried holding the shift key immediately after the BIOS bootup screen. The next few times I tried tapping the shift key. I think it was definitely the config file change.

---

