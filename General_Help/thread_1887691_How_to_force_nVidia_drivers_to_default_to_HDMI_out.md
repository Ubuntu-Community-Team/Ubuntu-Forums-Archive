---
title: "How to force nVidia drivers to default to HDMI out on boot"
date: 2011-11-27
forum: General Help
---

### Post by chuckhriczko on 2011-11-27
Hi all,
I have a laptop with an nVidia 310m graphics card I believe. The screen on my laptop cracked to the point of not being able to see anything. Now,  Using the default driver, I'm assuming Nouveau, Linux will automatically output to HDMI which let's me see at least some of the screen. However the nvidia drivers do not output to HDMI on boot. I'd like to use the overscan feature on the nvidia drivers as I can't see all of the screen but every time I use the nvidia drivers it wont output to HDMI and I can't see the screen. And I can't use the BIOS to do this as I can't see anything till Linux boots. Any ideas how to make the nvidia drivers do this?

---

### Post by efflandt on 2011-11-27
Trying to switch default display during initial boot may be a hardware issue for the particular graphics.  I think ATI and Intel automatically switch to an external display if they sense that one is connected, but nvidia does not.  So I imagine that you cannot even see the grub menu, much less use the text console to make changes.

I have a laptop that my boss' grandsons first trashed the old original hard drive, then thought that happened again (Windows was infected), so once I fixed the virus, I set it up to dual boot Ubuntu. Then they broke half of the screen diagonally and the part of the screen that did show would sometimes freeze or was very laggy.  I could not configure WinXP to use the external display because I could not see enough of its window.  But I managed to drag the window over in Linux where I was able to switch it to external display only, at least for X (gnome at that time).

But without a even a text display, you would not even be able to edit xorg.conf to do that, unless you put the laptop drive in an external USB enclosure and knew how to modify /etc/X11/xorg.conf to use HDMI as primary or mirrored display.  I am not even sure how to do that because the old laptop external was VGA and my desktop has a minimal xorg.conf that uses whatever single display automatically (whether HDMI or DVI).

Your external display is likely referred to as DFP-1 (since my single display is DFP-0 in NVIDIA X server settings app).  Nvidia refers to VGA as "CRT" and digital as "DFP".  Even though it appears to be for an earlier nvidia version, this may help [http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-b.html)

---

