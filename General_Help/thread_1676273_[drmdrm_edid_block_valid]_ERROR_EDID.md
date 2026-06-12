---
title: "[drm:drm_edid_block_valid] *ERROR* EDID"
date: 2011-01-26
forum: General Help
---

### Post by kshawkeye on 2011-01-26
Hey, when I boot up my Ubuntu 10.10 Server, I see these errors:

> 
[   7.606823] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 132
[   7.606905] [drm:drm_edid_block_valid] *ERROR* EDID Raw EDID:
[   7.746220] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 132
[   7.746290] [drm:drm_edid_block_valid] *ERROR* EDID Raw EDID:
[   7.848594] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 132
[   7.848654] [drm:drm_edid_block_valid] *ERROR* EDID Raw EDID:
[   7.950904] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 132
[   7.950964] [drm:drm_edid_block_valid] *ERROR* EDID Raw EDID:


I tried to search for it, but it seems to only be me. Any ideas what might be causing this?

---

### Post by JoeFriday49 on 2011-02-07
It's not just you...  I started a thread this morning about basically the same thing.  My syslog get's this added every 10 seconds:

Feb  7 12:10:52 AMD-64 kernel: [ 3911.629330] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 138
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629332] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629334] <3>0f 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629336] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629338] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629340] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 01 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629342] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629344] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629346] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629349] <3>03 03 03 03 03 03 03 03 03 03 03 03 03 03 03 03  ................
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629350] 
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629353] radeon 0000:01:05.0: DVI-D-1: EDID block 0 invalid.
Feb  7 12:10:52 AMD-64 kernel: [ 3911.629356] [drm:radeon_dvi_detect] *ERROR* DVI-D-1: probed a monitor but no|invalid EDID

I "think" my problem comes from scanning for a digital monitor, but I have no digital ports...  Maybe someone that's figured this out will come along...

---

### Post by farproc on 2011-08-08
I have this issue, connecting an Asus eeePC to an LG LCD.

The LG works with other laptops, the eeePC works with other screens. Nonetheless I suspect the problem is with the LG 32LZ50 (purchased in 2K4) not implementing the extended display identification data spec properly, coupled with the ATOM N150's integrated graphic chipset.

In a nutshell - DVI cables allow a screen to send an EDID block of data to the video card describing supported modes and so on. The video drivers think the checksum is wrong.

Why this is, is one question. How to "fix" it is another. Given that the fault is hardware related, potential fixes would involve updating the display or video firmware.

Workarounds that Ive seen involve passing setting  GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" in /etc/default/grub to (presumably) turn off the edid negotiation entirely.

Why this setting gets passed to the grub of all things I can't say. My problems also seem to run a bit deeper, so I can't comment on whether this "fix" actually fixes anything.

---

### Post by williambertram on 2013-03-04
I'm also receiving this, Ubuntu 12.10 Server (no desktop environment installed that I'm aware of).  One thing I've noticed is that the error seems to occur every time I boot headless.  When a monitor is plugged in, it never occurs.  Also strange - When the error occurs something odd happens with UFW.  I have to login, then disable / enable ufw and then everything works fine.  I don't have to do this when a monitor is plugged in, in this case it starts up normally and no need to disable / enable ufw.

I also don't have an xorg.conf to modify, so really not sure where to go with this one.

This guy seems to be having a similar problem, but again I have no xorg.conf because I'm running Ubuntu Server.

[http://askubuntu.com/questions/211039/getting-system-to-boot-in-headless-mode-set-up-without-display-problems](http://askubuntu.com/questions/211039/getting-system-to-boot-in-headless-mode-set-up-without-display-problems)

More ideas here, but again, directly tied to modifying xorg.conf.  

[http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/6201-running-ubuntu-without-a-monitor-attached-x-fails.html](http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/6201-running-ubuntu-without-a-monitor-attached-x-fails.html)

So I don't know.  I'm just going to plug an old monitor into it, but from what I'm seeing it doesn't seem to be tied to X, based on the fact that I'm receiving the error and don't even have x installed.  At least in my case it seems to be a bug related to having a monitor plugged in.  Which seems to be an unwelcome bug for a server.  Think I might also just try cutting off the end of a VGA cable, sealing the end up good, and trying a reboot with that plugged in.  Some other time though.  This annoyance has killed my desire to proceed on tonight.


> **farproc said:**
> I have this issue, connecting an Asus eeePC to an LG LCD.

The LG works with other laptops, the eeePC works with other screens. Nonetheless I suspect the problem is with the LG 32LZ50 (purchased in 2K4) not implementing the extended display identification data spec properly, coupled with the ATOM N150's integrated graphic chipset.

In a nutshell - DVI cables allow a screen to send an EDID block of data to the video card describing supported modes and so on. The video drivers think the checksum is wrong.

Why this is, is one question. How to "fix" it is another. Given that the fault is hardware related, potential fixes would involve updating the display or video firmware.

Workarounds that Ive seen involve passing setting  GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" in /etc/default/grub to (presumably) turn off the edid negotiation entirely.

Why this setting gets passed to the grub of all things I can't say. My problems also seem to run a bit deeper, so I can't comment on whether this "fix" actually fixes anything.

---

