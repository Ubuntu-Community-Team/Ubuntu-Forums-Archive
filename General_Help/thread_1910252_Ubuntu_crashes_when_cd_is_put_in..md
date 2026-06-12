---
title: "Ubuntu crashes when cd is put in."
date: 2012-01-16
forum: General Help
---

### Post by ahouchens on 2012-01-16
Hello, I am new to Ubuntu but I am a quick learner and very patient. The more I troubleshoot an issue, the more determined I become!

Here's the problem:
When I insert a cd or dvd of any kind into my cd/dvd rom drive, Ubuntu 11.1 crashes. 
The only way to recover is to hard reset the machine.
If I leave the cd in the machine while it is restarting, it will crash as soon as I log in.
This requires me to remove the disk as soon as I hard reset it.

However I found out some more info in this scenario:
1. I put in the CD.
2. I quickly click on the file browser and I see the media shows up in the left. 
3. As soon as I click the icon I get this error:
[INDENT]> DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending [/INDENT]4.Ubuntu crashes, requiring hard reset.

How can i retrieve some additional info to help anyone out there help me troubleshoot this? EDIT:  BTW I know how to run commands in terminal. :smile:

---

### Post by TeoBigusGeekus on 2012-01-17
An [old bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/355522") that's resurfaced.
Try [this]("http://ubuntuforums.org/showthread.php?t=1175638") thread.

---

### Post by ahouchens on 2012-01-17
> **TeoBigusGeekus said:**
> An [old bug]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/355522") that's resurfaced.
Try [this]("http://ubuntuforums.org/showthread.php?t=1175638") thread.


... I can't thank you enough. I was having a hard time isolating other threads that share my exact problem. It looks like there are some suggested solutions on the thread you recommended! Thank you again! I will post back here if any of the solutions on that thread did indeed work.

---

