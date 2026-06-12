---
title: "Partition Issues: Resizing and Removing"
date: 2012-04-20
forum: General Help
---

### Post by JoshuaMiller0 on 2012-04-20
Hi,

At the moment my partition problem is as follows, I have these operating systems installed in the order I installed them to default settings. My hard drive is 300GB big without anything on there. Doing default settings in installing Ubuntu and Xubuntu I do not knwo exactly how big each partition is.

[LIST]
[*]Windows 7: ~150GB at installation of Ubuntu, not sure of whether that was changed when installed Xubuntu
[*]Ubuntu 11.10 32 bit: ~150GB when I installed it, reduced to either 75GB when Xubuntu was installed or reduced to 100GB depending on hoe default settings modify the partitions.
[*]Subunit 10.04 32 bit: either ~150GB or 100GB (same as above)
[/LIST]
It is top priority that windows and all its documents and everything are **completely secure**, I refuse to do anything involving risks to them.


My ideal situation is to have all partitions resized and to remove Ubuntu all together (Ubuntu is too powerful for this old machine, so I resorted to Xubuntu which runs beautifully, and I love the 'theme' and windows manage didn't like I loved gnome in Ubuntu 10.04)


My ideal situation:

[LIST]
[*]Xubuntu 12.04 (when it is bug free ;) 32 bit: As little space as you can have without noticeably reducing speed. (I guess about 20GB at the most)
[*]Windows 7: the remainder of the space
[*]Ubuntu 11.10 completely removed, I have already moved all files off of it onto my current Xubuntu)
[/LIST]
What I somewhat tried so far:
I first tried to use GParted on Ubuntu 11.10 to resize the partitons to my liking, however I found that 1. It was not clear on what partition was for what and 2. Both Xubuntu and Ubuntu Partitions seemed to be locked - I am no pro at doing such things however.
I then tried using GParted on Xubuntu 10.04, however when it was loading/ searching for partitions a bunch of error messages came up saying they were locked and they did not show up onscreen.


Please help me with this ASAP as to me this is quite urgent.


Thanks,
Josh

---

### Post by Cheesemill on 2012-04-20
Boot from a Live CD and then run gparted (you cant use gparted on drives that are currently in use).

Post a screenshot here and I'll take a look.

> It is top priority that windows and all its documents and everything are **completely secure**, I refuse to do anything involving risks to them.In that case don't touch your partitions at all, any operation involving moving or resizing partitions has an element of risk, I've lost data when there was a power cut in the middle of a gparted operation.

Your data obviously isn't that important to you if you don't already have proper backups. What are you going to do when your drive fails (they **all** do eventually).

---

### Post by Mark Phelps on 2012-04-21
The SAFEST way to resize Win7 OS partitions is to use the Win7 Disk Management utility -- and yes, you can resize the OS partition from inside Win7, it just might have to reboot to do it.

But BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will allow you to make repairs later if you need to.

But, notice I said SAFEST -- meaning, as you have already been told, there is STILL a possibility of data corruption.

Having backups is the only way to protect against damage when doing any partition work.

---

