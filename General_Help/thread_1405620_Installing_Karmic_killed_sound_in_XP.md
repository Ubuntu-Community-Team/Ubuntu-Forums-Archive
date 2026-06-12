---
title: "Installing Karmic killed sound in XP"
date: 2010-02-12
forum: General Help
---

### Post by Paulgirardin on 2010-02-12
I've just resolved a Grub problem after reinstalling XP.

See this thread:[http://ubuntuforums.org/showthread.php?p=8817166#post8817166](http://ubuntuforums.org/showthread.php?p=8817166#post8817166)

I've installed Jaunty and then Karmic in recent weeks (clean installs) after having a Jaunty WUBI install.
After the Jaunty install the sound in XP started behaving poorly,but came right after some reboots.
After the Karmic install I got no sound in XP.So I reinstalled XP and sound was ok,but I had a Grub problem and reinstalled Grub2.
This killed the sound in the newly installed XP.

I know this doesn't make much sense -Installing Grub shouldn't have anything to do with XP's sound.

The motherboard is a ASUS P5K SE with Realtek ALC883 Audio built in,but I'm using a Creative CA0106 Audigy as the sound card.
I've checked that the selected sound card in XP is still the Audigy and I've checked the driver.

This is the output of  aplay -l in Ubuntu:

```
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

If anyone has any ideas I'd be interested to hear them.

It isn't a big deal though.99% of my usage is in Ubuntu.I only use XP for a couple of apps.

---

### Post by Yingy on 2010-02-13
I had a similar problem with my XP sound not working after install of Karmic.  Upon looking for drivers for my SB Live 24 bit I came upon this driver pack for Windows.  It's unsupported by Creative and my card was reading X-Fi for about a day but now everything is back to normal.  It has to do with the P17 chipset.  I also have my on board sound card disabled in my Bios.  That way there is no debate over which is the default card.  I know its frustrating to have no sound and I hope something here or someone can help you soon.  Best of Luck.

[http://forums.creative.com/t5/Sound-Blaster/SB-P17X-Series-Support-Pack-2-0-OUTDATED-AudigySE-Value-LS/m-p/533291]("http://[URL")

---

### Post by lenoirrichelieu on 2010-02-13
[FONT=Times New Roman]Edit /etc/init.d/alsa-utils, and comment the 378th line:[/FONT]
[FONT=Times New Roman]# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1[/FONT]
[FONT=Times New Roman]I had a similar issue and this solved the problem[/FONT]

---

### Post by Jive Turkey on 2010-02-13
> **king aaron said:**
> Hi,
I am King Aaron. I am new here.
Reinstall motherboard drivers.

In windows of course

---

### Post by Paulgirardin on 2010-02-13
I edited /etc/init.d/alsa-utils as directed and disabled the on-board sound in Bios and this did the trick.

Thanks all for the tips.:KS

---

