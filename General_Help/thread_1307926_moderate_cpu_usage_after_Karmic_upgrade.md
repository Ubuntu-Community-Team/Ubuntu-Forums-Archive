---
title: "moderate cpu usage after Karmic upgrade"
date: 2009-10-31
forum: General Help
---

### Post by klight on 2009-10-31
I've upgraded from Jaunty to Karmic and I'm seeing a constant disk access and 50%+ cpu usage from both cpu's.

Restarting udev will cause the cpu usage to return to normal and stop the disk access.

Before restarting udev, top shows very little activity with dbus-daemon and devkit-disks-daemon having around 12% CPU.  gnome-system-monitor shows the most active process as gvfs-gdu-volume-monitor at 6%.  The graphs show both cpu's at over 50%.

The logs do not show anything that correlates to these symptoms.  I've searched but not found any posts or bugs that seem to match.  Any suggestions?

---

### Post by klight on 2009-10-31
After killing any process with activity, I determined that mountall was the culprit causing disk activity and cpu usage.

I found bug # 456806 and post #8 ([https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/456806/comments/8]("https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/456806/comments/8")) has the solution.

---

### Post by aneganov on 2010-07-13
Ubuntu 9.10
Confirm this, devkit-disks-daemon is eating 10-15% all the time. 
Fix with editing mountall.conf didn't help.

Any ideas?

---

### Post by PrimaryMaster on 2010-07-27
Same problem here. I kill mountall and all is well. Editing mountall.conf doesn't work. 

Help please. I now have to run terminal and kill mountall each boot up. Darn.

---

