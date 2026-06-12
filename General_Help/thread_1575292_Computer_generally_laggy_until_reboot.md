---
title: "Computer generally laggy until reboot"
date: 2010-09-15
forum: General Help
---

### Post by Fotograf81 on 2010-09-15
Hello there,

I have some sort of an Issue with Ubuntu 10.04 which happens in about 1 of 5 boots - I think only when booted from "power off" and not just rebooted - but I'm trying to reproduce that:
If the problem occurs, the whole system performs very slow/laggy. I can't even play small movies or MP3s without gaps, file transfers per USB are at about 1MB/sec max, Compiz Effects are also laggy but perform excellently between the gaps. Even mouse and keyboard react with microlags. The whole system feels like being used over a VNC-connection.  (I know, it's hard to describe and I'm not a native speaker - sorry for that :/ )

top (even as root) does not show any processes taking ressources. The CPU's cores are about 95%+ idle even if a video is playing. No iowait and system and so on. I tried about everything I could think of, disabling the second screen, disabling compiz and so on.

The strange thing about it is, all the problems vanish if the system is rebooted although logging off and back in doesn't solve them.

I've installed munin on that PC and the very strange thing I saw was this:
The CPU-Diagram should always show 400% since it is an core2quad. But if these problems happen, about 200% are missing in the graph and are blank - but it's not constantly 200%. I've attached the image for you to see.
If rebooted the diagram is back to normal - that's what you can see for yesterday evening. Before going to bed I restarted => back to 400% and absolutely no lags.

[IMG]http://www.segnitz.net/_images/cpu-day.png[/IMG]



The Details about my system:

Dell Inspiron 530 Desktop (about 2 years old).
Core2Quad @ 2,4GHz
4GB RAM
NVidia GeForce GTX 260
GBit intel network adapter
Soundblaster XiFi Extreme Music bulk
500GB HardDisk, just about 8 weeks old
24inch EIZO + 20inch DELL Monitors


let me know if you need more details.


Thanks in advance!

---

