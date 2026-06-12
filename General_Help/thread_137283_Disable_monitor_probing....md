---
title: "Disable monitor probing..."
date: 2006-02-27
forum: General Help
---

### Post by gumbald on 2006-02-27
I would like to run an Ubuntu machine without a monitor, purely to be controlled by VNC, however on first attempts it wants to limit the resolution to 640x480 obviously. Is there a way to force the resolution to make it more reasonable for my VNC viewing?

TIA,
Jamie

---

### Post by cheredenine on 2006-02-27
How strange!  I have the exact same question and have just got here to look for an answer...  If i find anything I'll post, otherwise I'm all ears!

---

### Post by cheredenine on 2006-02-27
I managed to get some joy using this link:

[http://www.ubuntuforums.org/showthread.php?t=119530&highlight=force+resolution](http://www.ubuntuforums.org/showthread.php?t=119530&highlight=force+resolution)

Second post down mentions "sudo dpkg-reconfigure xserver-xorg"...  I took the poster's advice and kept everything to defaults, but when it came to setting up the monitor and display system my Ubuntu box (no monitor, accessed over VNC) mentioned 'generic monitor' and let me fiddle with display resolutions.  Low and behold when the PC restarts i can reconfigure it from 640x480 up to 1024x768....    Its probably possible to go higher, but thats enough for my needs!

---

### Post by gumbald on 2006-02-27
I did have trouble on my main Ubuntu machine which runs through a KVM in that it obviously probes the KVM for a resolution. I'd not thought of it that way without a monitor, so I'll try that and get back to you...

---

