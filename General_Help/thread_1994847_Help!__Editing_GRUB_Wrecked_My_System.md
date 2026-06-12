---
title: "Help!  Editing GRUB Wrecked My System"
date: 2012-06-03
forum: General Help
---

### Post by km782 on 2012-06-03
I am running Mythbuntu 12.04 and have been having some problems with my TV tuner card.  Someone suggested that I edit the GRUB and add noapic or irqpoll.  When I tried noapic it didn't fix the problem and it caused problems with my wireless card.  Next I tried irqpoll.  That caused even more problems and now Mythtv won't work (can't connect to backend) in addition to my wireless card.  I tried editing GRUB again and deleting those options so that the line is back to what it originally was: 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

I ran sudo update-grub and restarted.  However my computer still has the same problems with wifi and Mythtv.  What can I do to restore my computer and reverse the changes from noapic and irqpoll?

---

### Post by km782 on 2012-06-03
Please ignore this.  I fixed the problem.  It was something unrelated to grub

---

