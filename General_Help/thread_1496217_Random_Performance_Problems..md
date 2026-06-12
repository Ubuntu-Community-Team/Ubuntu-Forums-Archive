---
title: "Random Performance Problems."
date: 2010-05-29
forum: General Help
---

### Post by Beelzebud on 2010-05-29
For the past two nights I have seen some very odd behavior from Ubuntu 10.04LTS.   

While watching an xvid file tonight, the audio suddenly stopped, and then the HDD started chugging away, and the entire system got unresponsive.   Mouse input was laggy to the extreme, and the system was just bogged down.  When this happens I also lose my title bars on any open windows.   

If I log out, and then log back in the problem goes away, but this is getting very annoying.

I use AWN as my main taskbar, and until tonight I was using Drapes to change my desktop background.   I suspect Drapes may be part of the problem, because it makes the system shutter every time it changes the background.   It's very hard to narrow down though.  I've noticed that I lose all transparency effects on AWN when this happens.  I've tried opening System Monitor while it's happening, but every program just hangs until the system finally stops chugging.   After it's done being unresponsive I have no transparency, and no title bars on windows.   Restarting the Xserver by logging out and logging back in fixes it.  

I'm using a Geforce 6600 with the newest driver in the Ubuntu driver installer.   Compiz is enabled, but no fancy effects are activated.   

Anyone else seeing these types of random (seemingly) performance problems?   Missing window title bars, mouse lag, and lots of HDD activity?

Is there any log file that I might be able to look over to help sort out why this is happening?   I've been very pleased with 10.04, but if this continues to happen, I won't be able to keep using it.

---

### Post by finlost on 2010-05-29
Screensaver enabled?

---

### Post by Beelzebud on 2010-05-29
No, the screen saver is disabled.

---

### Post by Beelzebud on 2010-05-29
Hmm I just took a look at a log file at  /var/log/syslog and I'm seeing Out Of Memory errors with VLC at the time of the crash.   

Is VLC known to have memory leaks?

---

### Post by Beelzebud on 2010-05-29
Ok just to put a cap on this thread, I did some more searching and found that VLC does indeed seem to have a memory leak ATM...

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/575460](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/575460)

Hopefully they fix this soon..

---

