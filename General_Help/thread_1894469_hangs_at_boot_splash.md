---
title: "hangs at boot splash"
date: 2011-12-12
forum: General Help
---

### Post by bmike1 on 2011-12-12
I have Ubuntu 11.10 on another computer. I changed xorg.conf on it. Now it hangs at startup. How do you get it so you can watch the startup sequence so I can see where it hangs? I finally got it to give me the grubmenu and I selected 'normal startup'. Then I let it run a bit and  I hit a bunch of buttons until text showed. (I figured out I hit cntrl at F7) Anyway, a  bunch of text scrolled by with what it is doing followed by 'ok' or 'fail'. From what I can see only one thing failed: 'Stopping automatic crash report generation'.
What did I do? Can we fix it?

never mind.... there was a typo in the file I edited.

---

### Post by shakabra on 2011-12-13
Press shift as the machine is booting. This will bring you to GRUB. The kernel listed on top is your current kernel. Press 'e' so you can edit that kernel. Look for where it says 'quiet splash' and remove those two words. Then press F10 to boot your new configuration......


And I just saw your edit.

---

### Post by Bucky Ball on 2011-12-13
Before editing xorg.conf (or any other important file) *make a backup of the file!!!* Then if you screw up you can just put the old (working) file back where it was and start again. ;)

Could you please mark the thread as 'solved' from 'thread tools' to save time and help others.

---

