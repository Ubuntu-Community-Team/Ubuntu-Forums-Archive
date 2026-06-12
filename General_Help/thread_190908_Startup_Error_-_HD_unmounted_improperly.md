---
title: "Startup Error - HD unmounted improperly?"
date: 2006-06-06
forum: General Help
---

### Post by roamunit on 2006-06-06
Not sure if this is the right support forum to post this in, but I figured I'd put it here.

I recently installed Ubuntu for the first time, and I ended up putting it on my slave hard-drive, hdb, in order to avoid having to resize the partitions on my main drive. Everything was fine, I rebooted a few times, and then I booted back into Windows. However, when I later tried to boot back into Ubuntu, it failed to mount the slave HD as root. To cut to the chase, a fsck fixed my problems - something about a missing partition table or a corrupted groups entry, can't remember the exact error - and suggested that it was because hdb was unmounted uncleanly.

Which brings me to my question: how can I avoid this sort of error in the future? I saw a post that suggested that many Linux distros don't like being installed on a slave drive; is it likely that this was the cause of my problems? The OS didn't crash or anything, so I'm a little uncertain as to why hdb wouldn't be properly unmounted. :confused:

---

### Post by RAOF on 2006-06-06
How did you shutdown your computer?  If you go System->Quit->Shutdown, Ubuntu should properly unmount everything.  If you just turn the computer off, it won't be properly unmounted (and the filesystem will possibly be corrupted, as you found).

---

### Post by roamunit on 2006-06-06
I shut down through the usual System->Quit->Reboot method - I'm new to Ubuntu, but I'm certainly not new to computers :wink: - although there was a hard boot later on. That was after I had already gotten the "unable to mount" error and gotten booted into a basic, no-frills prompt, so I doubt I really damaged anything that wasn't already damaged. 

I had just recently installed followed the wiki's intstructions for installing the fglrx driver for my Radeon 9800, FWIW, but it seemed to be doing fine, and still seems to be doing fine now that I've gotten the system back up and running.

---

