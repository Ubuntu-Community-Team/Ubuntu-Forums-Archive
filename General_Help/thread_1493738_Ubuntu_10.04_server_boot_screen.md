---
title: "Ubuntu 10.04 server boot screen"
date: 2010-05-26
forum: General Help
---

### Post by derek71 on 2010-05-26
I have searched through the forums and did not a relevant post, so here goes...

I have installed Ubuntu 10.04 server as the basis of a file server.  Under previous versions of Ubuntu, the list of boot steps was visible and now version 10 it is covered with a boot screen.

Is there a way to turn off this screen so that the bootup processes can be seen?

---

### Post by obscurant1st on 2010-05-26
"perhaps remove the quiet splash on the entry from grub"
Quoted from IRC #ubuntu :)

---

### Post by derek71 on 2010-05-27
I found the grub file location in Ubuntu 10.04 and modified it to show the boot processes.  I would like to make another change to make the boot steps persistent:  I noticed that the screen showing the boot progress clears when the prompt appears.  I have a related (I think) question: with the new version of Ubuntu, my terminal occupies only a quarter of the screen.  I am not sure if this is a grub level setting or other configuration.  I have already tried the GRUB_GFXMODE option without luck.

---

### Post by derek71 on 2010-06-19
To refine my previous question a bit, I see that the boot screen resolution changes part of the way through the startup sequence.

I wondered what controlled this change in the screen settings?  I only need a text screen to view the messages, so video graphics are not really needed.

---

