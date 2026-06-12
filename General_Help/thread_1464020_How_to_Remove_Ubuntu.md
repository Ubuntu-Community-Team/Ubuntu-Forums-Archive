---
title: "How to Remove Ubuntu?"
date: 2010-04-27
forum: General Help
---

### Post by johnproyal on 2010-04-27
So I installed, and it didn't work, mostly due to Toshiba not having any support for Linux, but now I can't even boot into Ubuntu (it hangs at a certain line) so I figure I'll wait for someone to post a fix and then try again later.

For right now, how do I remove Ubuntu from my hard drive? I set a partition for it and swap room. I want to do this mostly so I won't have to choose Windows every time I turn on my computer. Thanks for any help.

It was the Lucid RC, on a Toshiba L505D laptop.

---

### Post by stephenmac7 on 2010-04-27
Reinstall windows.

---

### Post by johnproyal on 2010-04-27
Is there anyway where I wouldn't have to do that?

---

### Post by P4man on 2010-04-27
I dont think he wants to reinstall, he dualbooted.

If you did a wubi install, I think you can remove it from windows control panel, add/remove, but im not sure.

if you did a regular install, you will need a windows cd to reinstall windows bootloader. With XP its called FIXBOOT or FIXMBR (by memory). If its a newer windows, then Im not sure, but just booting the cd, recovery mode and having it "fix" you windows will do the trick I think.

alternatively, you can keep ubuntu and modify grub to insta-boot windows.

---

### Post by johnproyal on 2010-04-27
> **P4man said:**
> if you did a regular install, you will need a windows cd to reinstall windows bootloader. With XP its called FIXBOOT or FIXMBR (by memory). If its a newer windows, then Im not sure, but just booting the cd, recovery mode and having it "fix" you windows will do the trick I think.

The laptop didn't come with a CD, but I imagine I could burn one.

Would this remove the Ubuntu partition?

---

### Post by P4man on 2010-04-27
is it a wubi install (installed inside windows, same partition) or not?

---

### Post by johnproyal on 2010-04-27
> **P4man said:**
> is it a wubi install (installed inside windows, same partition) or not?

No, I installed using a Live CD.

---

### Post by aysiu on 2010-04-27
+1 for Wubi. Sorry you didn't use it. Removing Ubuntu would have been as easy as uninstalling any program in Windows.

Since your computer didn't come with Windows CDs, what does it come with? A recovery partition?

---

### Post by P4man on 2010-04-27
OKay. Then no, this will not remove the ubuntu partition. However, you should not delete the ubuntu partition before you reinstalled windows bootloader, otherwise you will end up with an unbootable machine.

So boot windows cd first (which version?), run recovery/repair/fixmbr until grub is gone, and then you can remove/reformat the ubuntu partition from within windows.

---

### Post by johnproyal on 2010-04-27
> **aysiu said:**
> +1 for Wubi. Sorry you didn't use it. Removing Ubuntu would have been as easy as uninstalling any program in Windows.

Since your computer didn't come with Windows CDs, what does it come with? A recovery partition?

Yes, it came with a recovery partition.

I'll be sure to use Wubi instead of making the mistake not to next time. I just wasn't sure if it would have worked with Lucid.

---

### Post by aysiu on 2010-04-27
This may help:
[http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php](http://www.ambience.sk/fdisk-master-boot-record-windows-linux-lilo-fixmbr.php)

---

### Post by P4man on 2010-04-28
> **johnproyal said:**
> Yes, it came with a recovery partition.

I'll be sure to use Wubi instead of making the mistake not to next time. I just wasn't sure if it would have worked with Lucid.

Actually, I would (rather strongly) recommend against wubi, unless it just for a quick test to see if things work.Wubi introduces a slew of its own problems, like difficulties growing the partition, very limited recovery options if something goes wrong, the fact any serious windows problem may bring down ubuntu as well, etc. The fact its easier to remove is about the only advantage.

---

