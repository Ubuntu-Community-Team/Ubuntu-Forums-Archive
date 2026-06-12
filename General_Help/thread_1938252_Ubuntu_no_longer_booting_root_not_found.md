---
title: "Ubuntu no longer booting: root not found"
date: 2012-03-09
forum: General Help
---

### Post by F. Schnackenpfefferhausen on 2012-03-09
Hello,

I got a problem wit Ubuntu 10.04 LTS Server Edition. (Happened after the computer turned of, power loss or so)
On startup it forces a disk check, but then crashes. Writes something about iptables. I've attached a "screen shot" of the situation.

Interestingly, I can't boot from live-CDs either. It always ends up with a kernel panic (not syncing).
When booting Ubuntu 11.10 Desktop it looks as in the second picture.

Those errors don't seem to be consistent either, I've also seen other ones on other tries. It generally seems about not being able to find the root partition and then there's a kernel panic. Why would that even matter for a live CD?

---

### Post by tenshi_ on 2012-03-09
Could you check what happens when you press "C" to cancel the partition check during the live CD boot? does it continue to boot normally from the live CD?
Cause if it doesn't I would bet for a hardware problem most likely a memory issue, But if it does, one thing i can think about is a partition problem.:(
So far and with so little information I couldn't tell but this could be a problem of a corrupted partition that ubuntu by itself can't work out, I faced a similar problem before and I had to use a different distro to check and repair the partition to be able to boot again.
Though, this was about a year ago and perhaps with an Oneiric or Precise Live CD this can be sorted out now.:!:

---

### Post by F. Schnackenpfefferhausen on 2012-03-09
I don't think there's a partition check. lat time I tried to select "Check file system" i got straight to the mentioned kernel panic. Now I tried it again, and it seems to be running the check.
Also Knoppix stopped with a Kernel Panic during boot, at a later try I went till the graphic user interface and then there was a kernel panic, related to the radeon driver I think.
As I said, the behavior is very inconsistent.

**Edit**: Concerning memory stuff: There seem to be Segmentation Violations, but I have run memtest and it showed nothing.

---

### Post by jwbrase on 2012-03-09
There should be a memory test entry in grub. You might want to try running that to see if it might be a memory issue.

EDIT: Ninja'ed by your post about having run memtest.

---

