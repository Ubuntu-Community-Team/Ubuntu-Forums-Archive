---
title: "Ubuntu bugs: Can they get more attention? Will they get more attention?"
date: 2011-05-08
forum: General Help
---

### Post by andrei_1 on 2011-05-08
I appreciate Canonical's efforts in improving the user experience and Unity is generally likable. However, this is not to say that in general Ubuntu Natty feels like pre-alpha software. It seems that Ubuntu is becoming increasingly challenged in handling such basic things as multi-monitor support and wake-up from suspend that users took for granted 10 years ago.

Here's for example this thread of mine; the problems were not entirely solved and recurrent issues made me stop using the external monitor: [http://ubuntuforums.org/showthread.php?t=1742284](http://ubuntuforums.org/showthread.php?t=1742284) - I will not open a bug report for this simply because I can't - the issues are too serious and erratic that my bug description would probably be marked as 'Incomplete'.

So basically I'm worried: Canonical seems to become increasingly preoccupied with issues that while laudable are too disconnected from the users' basic needs.

Is there at least a concern for making Ubuntu more stable especially in light of the recent efforts that might have spread Canonical's resources too thin?

---

### Post by r-senior on 2011-05-08
Don't forget that Canonical don't write and/or maintain all of what ends up as Ubuntu. The resume from suspend is down to the power management code in the kernel for example.

---

### Post by andrei_1 on 2011-05-08
> **r-senior said:**
> Don't forget that Canonical don't write and/or maintain all of what ends up as Ubuntu. The resume from suspend is down to the power management code in the kernel for example.

Of course, but it's their duty to make sure that ultimately what they deliver is stable and usable. This was the point I was making above. They might not have the resources to do that because they are spent on other directions.

PS: And they do actually write code, contribute code and fix bugs reported on Launchpad for all core/critical components of the distribution.

---

### Post by Quackers on 2011-05-08
Suspend/hibernation mechanisms differ wildly from machine to machine and manufacturer to manufacturer. Problems in this are are often caused by a poorly written DSDT (part of your bios) or poor ACPI management. Both of these are dealt with by manufacturers rather than operating systems.
In fact, if you re-compile a DSDT on a brand new computer you are likely to find errors - possibly hundreds of them!

---

### Post by andrei_1 on 2011-05-08
> **Quackers said:**
> Suspend/hibernation mechanisms differ wildly from machine to machine and manufacturer to manufacturer. Problems in this are are often caused by a poorly written DSDT (part of your bios) or poor ACPI management. Both of these are dealt with by manufacturers rather than operating systems.
In fact, if you re-compile a DSDT on a brand new computer you are likely to find errors - possibly hundreds of them!

Suspend/hibernation worked fine in Ubuntu Maverick and ironically it also worked in Natty - until came a massive update for many packages a few days ago (after Natty's release, this update also worsened the multi-monitor support). Needless to say, it would work perfectly in any version of Windows (no, I will not go back to Windows). If you peruse Launchpad, you'll see many bugs related to suspend issues (and other hardware issues like wireless cards support etc.) that come and go and then come back again with various kernel and/or other updates.

However, instead of talking about the various details in my argument (I could include many more bugs and annoyances for some of which I have already opened Launchpad bug reports), could you please instead focus on the main point of my topic?

---

### Post by powerpleb on 2011-05-08
It's the little bugs that get me. Like not being able to use the numbered shortcuts until I've opened a program that isn't on the task-bar, or program windows somehow managing to wander across into different desktops, or the gapless playback not working in Banshee or Rhythmbox.

All frustrating in their seeming insignificance.

---

