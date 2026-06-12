---
title: "Youtube Flash video blanks GUI"
date: 2012-04-13
forum: General Help
---

### Post by Rebelli0us on 2012-04-13
Some youtube videos (in full screen) seem to crash the GUI, and all I get is a white screen.

It seems the OS has crashed but then I can Alt+Tab into a Windows VM and the VM works just fine. But when I Alt+Tab back into the Ubuntu shell I still have white screen. Mouse is mostly invisible, but Ctrl+Alt+Del brings up the shutdown dialog so I can restart without having to reset.

I’ve used Flash-Aid but the problem continues, and it happens with a FEW videos but most work OK. Just before the video corruption, the movie stalls & freezes in full screen. 

Also if I run the same video in a Windows VM, there is NO problem. Browser is Firefox with default plugins (see below). I’m using the open source AMD driver because the proprietary one causes random freezing/crashing.

Any ideas?

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=215958&stc=1&d=1334325988[/IMG]

---

### Post by lovinglinux on 2012-04-13
Disable hardware acceleration in flash and check if the problem persists.

To do that, see the first item at [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by Rebelli0us on 2012-04-13
> **lovinglinux said:**
> Disable hardware acceleration in flash and check if the problem persists.

To do that, see the first item at [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

Thank you, I will try and report back

Adobe Flash is the ugliest bloat-ware. It’s just a media player, why hasn’t anybody else produced an alternative? I’m sure VLC media player is capable of streaming video.

---

### Post by nomodeset on 2012-05-30
Same problem here. Flash player (plugin-container) tends to freeze after some time while playing a YouTube video in full screen mode. Did disabling hw acceleration actually help? AMD does not support VDPAU, so this setting should be irrelevant now anyway, or?

I know, there are other solutions to play Flash videos, but I want to try the cause of this issue. Things I noticed:
- plugin-container continues to download the video even after freeze
- changing the CPU priority does not help
- video quality (480p etc.) does not affect the behavior

My CPU is kinda old and Flash without hw acceleration eats like 100% of it. However, I can not reproduce this issue while running other CPU intensive applications.

Ubuntu 12.04 (x86) + XFCE 4.8
Flash Player 11.2.202.235

Intel Pentium D 930 3.0GHz
2GB RAM
ATI Radeon HD 5670 (fglrx 12.4)

---

### Post by Rebelli0us on 2012-05-30
> **nomodeset said:**
> Same problem here. Flash player (plugin-container) tends to freeze after some time while playing a YouTube video in full screen mode. Did disabling hw acceleration actually help? AMD does not support VDPAU, so this setting should be irrelevant now anyway, or?

I know, there are other solutions to play Flash videos, but I want to try the cause of this issue. Things I noticed:
- plugin-container continues to download the video even after freeze
- changing the CPU priority does not help
- video quality (480p etc.) does not affect the behavior

My CPU is kinda old and Flash without hw acceleration eats like 100% of it. However, I can not reproduce this issue while running other CPU intensive applications.

Ubuntu 12.04 (x86) + XFCE 4.8
Flash Player 11.2.202.235

Intel Pentium D 930 3.0GHz
2GB RAM
ATI Radeon HD 5670 (fglrx 12.4)


I was watching a European sitcom series, I suspect the video files were corrupted or had video encoding errors. It hasn’t happened since. As I said above, the same videos played just fine in a Windows VM, so it’s a Linux problem -- probably unhandled errors.

Adobe doesn’t seem to support Linux, they don’t see profits in an OS with 1% market share. Too bad this Adobe crap has become the standard.

---

