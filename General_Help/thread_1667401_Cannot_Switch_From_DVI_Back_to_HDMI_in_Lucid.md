---
title: "Cannot Switch From DVI Back to HDMI in Lucid"
date: 2011-01-14
forum: General Help
---

### Post by silverbullet763 on 2011-01-14
Having a bit of an issue with my Lucid x64 HTPC. I can get the image to appear through DVI on a spare external monitor, but when it is disconnected and switched back to HDMI I get not picture on the TV any longer. I switched the sound output to an external USB device for testing the unit and noticed on reboot that I had lost everything via HDMI even though the setting had been switched back previously. Obviously a setting must be off here somewhere, but I've yet to find it. I've rebooted with only the HDMI connected, but still nothing. Any ideas to fix this? Thanks.

---

### Post by silverbullet763 on 2011-01-17
I upgraded from Lucid to Meerkat in  an attempt to rule out an issue with the OS. A clean install didn't fair  any better. I've tried everything I can think of including the detect  monitor feature in Ubuntu and a fresh xorg configuration file, but it  just isn't working. I've updated the BIOS to the latest as well. At this  point, I think it may be some sort of hardware failure, but I'd like to  check with a few fine folk here before I go to Asus directly. Can  anyone think of other possible solutions?

---

### Post by silverbullet763 on 2011-01-30
After an exhausting week of really sitting down and trying to solve this, I managed to get everything working together again.

Backstory: The HTPC was re-setup with Lucid on a small 19" Samsung via DVI after the HDMI went out. At first, I thought that an update had broken something. After a fresh install, I went to plug it back into my Pioneer 1019 receiver via HDMI. The display still failed to recognize it and all I had was a black screen. No audio, nothing. Over the course of a week, I tried new cables, updated the distro to Meerkat, changed drivers and purchased a GT 240 to replace the on-board ATI 4250. I also updated the firmware on the Pioneer to 1.056.

I thought that there may have been some weird handshake issues between the ATI and my receiver that could have caused the problem. When I switched the cable, rather than go through the trouble of plugging it into the receiver, I plugged it into my Panasonic television directly and noticed that it displayed, so I thought Ahh Ha, bad cable! Plugging it into the 1019 with my shiny new cable, I was once again greeted by my old friend black screen.

The next thing was to put in the GT 240 (gigantic pain to configure audio was secretly coming). Again, this displayed great on the Panasonic, but no dice with the Pioneer. I tried everything from checking different resolutions to xconfig, but nothing. I knew the receiver was functioning correctly, due to the fact that all my other devices worked perfectly. I even switched the ports around.

The Fix: Just when I was about to give up and throw the HTPC out my front door, I ran across a thread over on AVS, where they were discussing EDID Override. A few folks there had issues with their HTPCs not displaying correctly or audio issues, so I figured there was nothing to lose by giving it a shot. They were all discussing Windows HTPCs, but a user there had provided the EDID of their Pioneer 1019 in INF form.

I opened the INF (he/she had turned it into a driver) with a program called En Tech Taiwan Monitor Asset Manager Version 2.58.0.906 on my Windows laptop. I resaved the file as a .bin to use with Ubuntu

1) Installed ghex (in case of any necessary modifications to EDID) and read-edid.

2) Saved &#8220;1019.bin&#8221; from my flash drive to the desktop.

3) In the terminal, I changed the directory to the Desktop and typed parse-edid "1019.bin" | grep

4) The EDID checksum passed, so I logged in as root and copied "1019.bin" to /etc/X11

5) Opened /etc/X11/xorg.conf as root and in the &#8220;Screen&#8221; section added Option "CustomEDID" "DFP-   1:/etc/X11/1019.bin" (Replace DFP with whatever yours is from nvidia-settings)
  
6) Saved the file, restarted, and my display was back!

EDID basically forces a video source to describe its capabilities. The override fixed whatever errors or limitations existed that prevented the connection from functioning in the first place (I'm sure someone here or on AVS has a much better way of explaining this than I do). My DFP is now listed as a "Pioneer 1019" in nvidia-settings. 

More info [http://www.avsforum.com/avs-vb/showthread.php?t=1091403](http://www.avsforum.com/avs-vb/showthread.php?t=1091403) Your issue may not require this approach, so it is best to rule out other possible causes first. A lot of the discussion is Windows based, but with a bit of research  many of the same ideas can be applied to Linux as well. They also have a linux HTPC chat area, This turned out to be way too long, but hopefully someone with a similar issue will be saved a few headaches.

---

