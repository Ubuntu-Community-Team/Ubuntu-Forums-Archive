---
title: "&quot;Unknown Application&quot; constantly uses 50% of cpu."
date: 2009-08-06
forum: General Help
---

### Post by rjlm on 2009-08-06
As stated in the title, 50% of both cores of my cpu is being constantly used. This is based on what gnome-system-monitor states in the "Resources" tab: 
[ATTACH]123838[/ATTACH]

However, in the processes tab of the same application, and also in the "top" application ran in the terminal, there is no process listed to account for such a large constant use of my cpu. The only possible hint at one is a blank process that keeps appearing and disappearing constantly in system monitor. (However, because I fairly recently migrated from a Windows OS, it may be that this is normal functionality: I am not yet wholly familiar with which processes are which etc yet) [ATTACH]123837[/ATTACH] and [ATTACH]123836[/ATTACH]

The only actual proper reference I can find to this unknown process is that when I tell Ubuntu to shut down, this window appears: [ATTACH]123839[/ATTACH] 
As soon as i click "Logout Anyway" the graph in system monitor -> resources steeply drops to a normal cpu usage level.

I have been using Ubuntu for a month or so, and this has only just started happening, and is certainly not normal behaviour. I recently increased the size of my ubuntu partition (and also marginally increased the size of the swap partition) using the g-parted live cd, if this information helps, although I have confirmed, based on information elsewhere on the forum, that my swap partition is correctly registered with the right UUID in fstab.

I apologise if there is a really simple fix to this, however, as I said, I am unfamiliar with the process structure for Linux at the moment.

Any help is much appreciated :)

Thanks, Josh.

Edit: Some information about my system:
Ubuntu Jaunty Jackalope
Using Compiz with the Emerald decorator, but same problem occurs using Metacity with gtk.
Intel® Core&#8482;2 Duo Desktop Processor E6400
1.25 GB DDR2 Ram
GeForce 7300GS
Let us know if you need any other specs etc.

---

### Post by Wayne_V on 2009-08-06
does "ps -eHcafww" show the unknown process?  try running that commands several times quickly if it doesn't show it the first time.

if you can get the PID of unknown process maybe you can figure out what it is from the /proc/<PID> directory.

---

### Post by rjlm on 2009-08-06
Hi, thanks for the quick reply.

I ran the process you asked, however i haven't a hope in hell of understanding the output it gave me. I've attached it here, can you see anything dodgy at all: [ATTACH]123842[/ATTACH]

Cheers.

---

### Post by rjlm on 2009-08-06
Aha! Problem solved, I had forgotten that I had turned on the option in remote desktop to "Allow others to view your desktop", because I wanted to try it out with a friend. Turning this option off returned my cpu to normal levels. No idea why enabling remote desktop would cause this, but oh well. 

Thanks for your help anyways.

:D

Edit: Just one more thing, how do i mark this thread as solved? Cheers.

---

