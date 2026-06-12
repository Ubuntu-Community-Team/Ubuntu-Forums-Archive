---
title: "suddenly slow boot"
date: 2012-07-11
forum: General Help
---

### Post by jasonjob on 2012-07-11
Odd problem.  Doesn't seem to fit anywhere else.

This morning my machine started taking an extra 30 - 40 seconds to boot.  I have made no hardware or software changes in the last few days.  Using Ubuntu 11.04.  Everything has been working pretty much perfectly.

POST is fine. GRUB runs fine. Purple Ubuntu splash-screen (text, not graphics) is fine. At the point where the screen blanks and then X and Gnome start, it now stalls for a bit.

Previous behaviour was a couple of seconds of screen change, and continuous disc activity.

Current behaviour is a blank screen, with small bursts of disc activity separated by several seconds of no activity.  This lasts for 30 to 40 seconds, and then the desktop arrives.

Everything else is as before - no performance drop, no crashes, shutdown is fine.  Buggered if I know what's happened :) Any thoughts?

---

### Post by oldfred on 2012-07-11
I would check log files like dmesg to see where the delay may be occurring.

---

### Post by jasonjob on 2012-07-11
> **oldfred said:**
> I would check log files like dmesg to see where the delay may be occurring.

Thanks - any idea roughly what I should be looking for?  Will it be something immediately before or after the pause?

---

### Post by oldfred on 2012-07-11
Never seen if it is the one before or after a long pause. I think after but am not sure. Also any errors, or repeated attempts at loading a driver and then a timeout.

Post the few command around any long pauses, you do not need to post the full demesg as it is long and most is not a problem. 

System -> Administration->Log File Viewer 
Look for repeated entries or long times between entries
or:
egrep -e fatal /var/log/dmesg
egrep -e modules /var/log/syslog

---

### Post by jasonjob on 2012-07-11
Okay - dmesg has no pause, but I found this in syslog:

Jul 12 13:34:06 Carnelian kernel: [   27.625934] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Jul 12 13:34:06 Carnelian kernel: [   27.625939] ata3.00: BMDMA stat 0x25
Jul 12 13:34:06 Carnelian kernel: [   27.625942] ata3.00: failed command: READ DMA
Jul 12 13:34:06 Carnelian kernel: [   27.625948] ata3.00: cmd c8/00:08:87:7d:a0/00:00:00:00:00/e1 tag 0 dma 4096 in
Jul 12 13:34:06 Carnelian kernel: [   27.625949]          res 51/40:00:8d:7d:a0/00:00:00:00:00/e1 Emask 0x9 (media error)
Jul 12 13:34:06 Carnelian kernel: [   27.625951] ata3.00: status: { DRDY ERR }
Jul 12 13:34:06 Carnelian kernel: [   27.625953] ata3.00: error: { UNC }
Jul 12 13:34:06 Carnelian kernel: [   27.768457] ata3.00: configured for UDMA/133
Jul 12 13:34:06 Carnelian kernel: [   27.768470] ata3: EH complete

This repeats 12 times, the exact number of disc activity bursts, over the right period of time (about 30 seconds).

Not happy about what I think I'm seeing here - do "ata3" and "media error" mean my hard drive is on the way out, and this delay is a sign of the OS trying to read something off the damaged sector(s) during startup?

---

### Post by jasonjob on 2012-07-11
just searched "BMDMA stat 0x25", and I've got a hit about someone with bad sectors on a drive getting the same thing, which he thought might have been due to a power failure.  I *did* have one of those now I think about it - have had them before to no (known) ill effect, so I just put it out of mind.  Could that be it?  

There was mention of a badblocks tool that may fix this, but I'm not familiar with it.

---

### Post by oldfred on 2012-07-12
All I know is Disk Utility and that it shows green for ok. Click on drive and it has Smart Status. 
You can run a variety of checks but I do not know when errors exceed a certain level and drive is considered as about to fail.

---

### Post by jasonjob on 2012-07-14
Well, I've done a backup (which took several hours for only 60-odd Gb), and installed on a new drive - copying back took less than half an hour.  Wonderful things hard drives...

Thanks for the help.

---

