---
title: "GRUB2 Resolution (esp. Recovery Mode)"
date: 2011-04-24
forum: General Help
---

### Post by Chriske on 2011-04-24
Hi,

**_Problem:_**[INDENT]I recently reinstalled Ubuntu 10.04.
[/INDENT][INDENT]Since I did that I have had a problem with GRUB: I cannot see the Recovery Mode menu - at least not anything intelligible.

I can see the normal first GRUB menu with all installed operating systems, recovery modes, and MEMTEST, etc, but cannot see the Recovery Mode menu. What I do notice (if I select it) are some fuzzy lines at the top of the screen. I also notice the Ubuntu splash screen does not appear any more either.

Clearly it seems there is a resolution issue. I have a 1440 x 900 monitor and the current version NVIDIA driver.

This happened some time ago on previous Ubuntu releases, but was not an issue when I originally installed 10.04.


[/INDENT]**_Attempted Fix_**:[INDENT]I installed the StartUp-Manager and have tried all the resolution combinations with no success. Some yield bigger more centrally displayed fuzzy lines, but still nothing legible.


[/INDENT]Although this isn't "life-threatening" I'm just a bit worried that I might need the Recovery Menu and not be able to use it.

Any suggestions would be much appreciated.

Many thanks.

---

### Post by ikt on 2011-04-24
[http://ubuntuforums.org/showthread.php?t=1418590](http://ubuntuforums.org/showthread.php?t=1418590)

I don't think you have a problem with grub, I'm pretty sure it is with ubuntu/xorg graphics config.

---

### Post by Chriske on 2011-04-24
Many thanks ikt.

I think you could well be right there.

I just tried the procedure in that link and it made no difference, unfortunately.

Thanks again.

---

### Post by Chriske on 2011-04-27
So, what I did was reinstall 10.04.

Last time I installed Ubuntu I ran the updates from within the Recovery Menu and then booted into Ubuntu and updated the hardware drivers. Besides the Xorg problems I also noticed I was losing windows controls periodically.

This time I first booted into Ubuntu, updated the hardware drivers, rebooted, and then did all the other updates via Update Manager.

That cured the problems.

It seems the order/where these updates are performed from is important.

Hope this helps somebody. ;)

---

