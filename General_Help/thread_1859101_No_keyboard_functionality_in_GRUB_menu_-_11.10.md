---
title: "No keyboard functionality in GRUB menu - 11.10"
date: 2011-10-13
forum: General Help
---

### Post by Musmanno on 2011-10-13
Hey guys - installed 11.10 and it has been working well. I'm pleased with it. Only problem is that I do occasionally need to boot into Windows and there is no keyboard functionality in the GRUB menu when I boot. I tried other keys besides the arrows, and nothing seems to work. GRUB counts down like it should and boots into the default (11.10), but I can't make a selection.

Anything I can do to fix this short of attempting to reinstall 11.10 to see if GRUB works better the second time?

Toshiba Satellite i3 laptop.

---

### Post by Musmanno on 2011-10-13
Threads just flying by today. Can anyone help with this or point me in the right direction. Hate to reinstall the OS if I don't need to.

---

### Post by effenberg0x0 on 2011-10-13
Let grub go into default and load the system. Open a terminal and run 

```
sudo apt-get update && sudo apt-get upgrade
sudo update-grub
```

And reboot.
```
sudo reboot now
```

If you still have no keyboard on grub, once again log in the system, but attach your /etc/default/grub to your next post here.

Regards,
Effenberg

---

### Post by Musmanno on 2011-10-13
Thank you, sir. I'm going to give that a try shortly and will report back.

---

### Post by oldfred on 2011-10-13
Long time ago I had same issue. It was a BIOS setting. 

Both Windows & Ubuntu seem to load their own drivers, but grub follows BIOS so if BIOS is set not to use USB keyboard it does not work.

---

### Post by effenberg0x0 on 2011-10-13
> **oldfred said:**
> It was a BIOS setting.

Good advice. I was thinking more of [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/771376](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/771376) and duplicates.

But it's definitely important to check if BIOS is set to support USB, Legacy USB. Some BIOS also ask "Plug and Play OS?", but nowadays Linux/Windows do not respect this setting.

Regards,
Effenberg

---

### Post by Musmanno on 2011-10-14
Thanks guys. I tried the GRUB update posted above, and that seemed to fix it when I did a restart. Doing a cold boot the problem persisted. I went into BIOS and noticed I had it set for fast boot (a change I made some time ago and forgot about). Changed that setting back to "normal" and the problem is solved. I wouldn't have thought to check the BIOS for this problem, so thank you!

---

