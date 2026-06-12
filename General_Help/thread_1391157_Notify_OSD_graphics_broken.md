---
title: "Notify OSD graphics broken"
date: 2010-01-26
forum: General Help
---

### Post by jimmyxx on 2010-01-26
Hey all,
I've updated my thinkpad T41 from Jaunty to Karmic and the notify OSD graphics are broken.

See the screenshot here:
[http://varlogrant.blogspot.com/2009/11/notify-osd-is-broken-under-ubuntu-koala.html](http://varlogrant.blogspot.com/2009/11/notify-osd-is-broken-under-ubuntu-koala.html)

(this isn't my blog, just someone with the same issue as me!!). All OSD alerts look like this.

I don't use the desktop effects on the laptop. Anyone got any ideas how to sort it?

Thanks!

---

### Post by ibuclaw on 2010-01-26
> **jimmyxx said:**
> Hey all,
I've updated my thinkpad T41 from Jaunty to Karmic and the notify OSD graphics are broken.

See the screenshot here:
[http://varlogrant.blogspot.com/2009/11/notify-osd-is-broken-under-ubuntu-koala.html](http://varlogrant.blogspot.com/2009/11/notify-osd-is-broken-under-ubuntu-koala.html)

(this isn't my blog, just someone with the same issue as me!!). All OSD alerts look like this.

I don't use the desktop effects on the laptop. Anyone got any ideas how to sort it?

Thanks!

What's the graphics card / drivers in use?

---

### Post by jimmyxx on 2010-01-26
> **tinivole said:**
> What's the graphics card / drivers in use?

The T41 has: **AGP 4x - ATI Mobility Radeon 7500**, 'lspci -v' shows:

```

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
        Subsystem: IBM Device 0530
        Flags: bus master, stepping, fast Back2Back, 66MHz, medium devsel, latency 66, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=128M]
        I/O ports at 3000 [size=256]
        Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
        [virtual] Expansion ROM at c0120000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel modules: radeon, radeonfb

```

Thanks

---

### Post by jimmyxx on 2010-01-26
I've just noticed that open office is also graphically broken...

See attached screen shot - how odd? I reckon it will probably be related? if not I'll create a separate thread for the open office issues.

Thanks

---

### Post by ibuclaw on 2010-01-26
This seems to be a known problem with an open ticket: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/444139)

In that link is quite a few possible workarounds until Lucid is released.

The most promising looks to be: Option "AGPSize" "32" in xorg.conf.


Have a look here also: [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_7500)
and here: [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_9000](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_9000)
For possible hints.

Regards
Iain

---

### Post by louieb on 2010-01-26
I get that on my T30 every now and then.   Seems to be isolated to v 9.10  - v 9.04 and v 10.04 alpha don't have the problem. 
Found my fix here [Graphical Corruption with Comiz  Enable/Disabled]("http://ubuntuforums.org/showthread.php?t=1314537&highlight=solved")
Look at this bug [https://bugs.launchpad.net/ubuntu/+s...ti/+bug/416001]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/416001")

and the fix that worked for me - edit your xorg.conf as in the Launchpad comment by  Grant Bowman.

---

### Post by Nylo on 2010-01-29
Here's my sad story.

My notify-osd is working but there is no message.  Unlike the original poster nothing else is affected.  Just the notify-osd.

Does anyone know how to fix it?

[img]http://www.tarzoom.com/photo/Screenshot.jpg[/img]

---

### Post by jimmyxx on 2010-01-29
Thanks all for your comments.

The issue is fixed, if you're having the same issues as me and use a Radeon Mobility 7500 then read this for details on the quick and easy fix:

[http://ubuntuforums.org/showpost.php?p=8368055&postcount=4](http://ubuntuforums.org/showpost.php?p=8368055&postcount=4)

[I]'To say it short: in xorg.conf under "Device", add
Option "RenderAccel" "off"'[/I]

---

### Post by Nylo on 2010-02-10
> **jimmyxx said:**
> Thanks all for your comments.

The issue is fixed, if you're having the same issues as me and use a Radeon Mobility 7500 then read this for details on the quick and easy fix:

[http://ubuntuforums.org/showpost.php?p=8368055&postcount=4](http://ubuntuforums.org/showpost.php?p=8368055&postcount=4)

[I]'To say it short: in xorg.conf under "Device", add
Option "RenderAccel" "off"'[/I]

I tried this fix with no luck.  Here is what happed.

"sudo Xorg -configure" creates a "xorg.conf.new" file but not in /etc/X11.  It shows up in my home file in my name folder.  It will not let me write to it.  When I try to use terminal it says I have no permission.  Im new to X/ubuntu but am trying to learn.

---

