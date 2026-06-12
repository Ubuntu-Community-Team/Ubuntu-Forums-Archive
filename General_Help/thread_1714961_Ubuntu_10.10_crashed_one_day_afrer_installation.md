---
title: "Ubuntu 10.10 crashed one day afrer installation"
date: 2011-03-26
forum: General Help
---

### Post by tagomago on 2011-03-26
Hi there,

I have installed 10.10 on my desktop pc to try it out. 
First problem i got was - microphone not working. 
Trying here or there in GUI tools i got system crash - keyboard completely blocked, screen showing some rest of windows. No reaction for normal Alt+SysRq

Here are relevant system details:

[LIST]
[*]AMD Athlon(tm) 64 Processor 3200+
[*]Sound card ATI technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
[*]Graphic card ATI Technologies Inc RS482 [Radeon Xpress 200] (prog-if 00 [VGA controller] Sybsystem: Micro-Star International Co., Ltd. Aspire L250
[/LIST]
Here is a kernel log:
Mar 25 21:20:54 indim kernel: [ 6378.743955] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Mar 25 21:26:27 indim kernel: [ 6712.059536] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
Mar 25 21:26:27 indim kernel: [ 6712.066647] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
Mar 25 21:26:27 indim kernel: [ 6712.068265] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
Mar 25 21:26:27 indim kernel: [ 6712.078870] [drm:radeon_cs_ioctl] *ERROR* Failed to parse relocation -12!
Mar 26 10:02:42 indim kernel: imklog 4.2.0, log source = /proc/kmsg started.

Question1: is Ubuntu supporting normal line-in microphones via ATI card? (if not, then this system not of my interest)
Question2: why is it crashed? (i dont understand log messages)

Thanks,
tagomago

---

