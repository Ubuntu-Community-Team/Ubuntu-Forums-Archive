---
title: "Jpilot error. Palm detected but get error in Jpilot"
date: 2006-02-16
forum: General Help
---

### Post by ade234uk on 2006-02-16
My Palm is being detected, all I need to do now is get it to sync properly with Jpilot. When I try to sync it throws up the following error?

dlp_ReadSysInfo error
Exiting with status SYNC_ERROR_PI_CONNECT
Finished

Really look forward to your help on.

---

### Post by SWAT on 2006-02-17
damn, I still have to write a howto for this. I remember that I have to tap "sync" on my palm, then wait 10 seconds, then cancel the syncing, then tap "sync" again and then click on "sync" in jpilot. I have my Palm Zire working perfectly here :)

---

### Post by UnrulyGrrl99 on 2006-02-17
what is the port you have JPilot set to use?  /dev/ttyUSB0 should work fine

I have a T2 that works flawlessly with Jpilot,, syncing by just hitting the sync button on the cradle.  So it is possible

Are you using a USB cradle or a serial cradle? [shoulda asked that first before telling you to use a USB device path :)]

Also, are you using  the Gnome palm conduit as well? that is installed by default I think, and having it running at the same
time will likely interfere with JPilot's access to the device

finally, can you post the output of ```
dmesg|tail -20
``` after you hit the sync button?
That should tell us more

---

### Post by ade234uk on 2006-02-19
Ok I have got my Palm recognised but I get the following error in jpilot when I press the hotsync button on my palm


This comes up in a new window

Warning (gpilotd)
The base directory

---

### Post by UnrulyGrrl99 on 2006-02-22
Try killing gpilotd.  From what I've seen so far, you cannot have the
Gnome "pilot daemon" and JPilot running at the same time.  

To find and kill gpilotd,
```
ps -ef|grep gpilotd
```
The number in the second column is the PID.   Use that here:
```
kill -9 $PID
``` replacing $PID with the number from the second column.

Then restart JPilot and try syncing again.

I think the Gnome pilot daemon will start on reboot every time unless you remove it
from the startup files, or wherever it is being started from.  I don't have access at the
moment to my laptop where i have all of this setup.
Good luck, you are almost there

---

### Post by mahasmb on 2007-09-06
> **SWAT said:**
> damn, I still have to write a howto for this. I remember that I have to tap "sync" on my palm, then wait 10 seconds, then cancel the syncing, then tap "sync" again and then click on "sync" in jpilot. I have my Palm Zire working perfectly here :)

That's very weird indeed, but it worked for me. Any reasons why it's messed up like that?

---

