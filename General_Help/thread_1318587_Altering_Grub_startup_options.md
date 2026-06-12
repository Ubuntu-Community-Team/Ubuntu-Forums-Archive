---
title: "Altering Grub startup options?"
date: 2009-11-07
forum: General Help
---

### Post by luxobumbrata on 2009-11-07
I'm VERY new to Ubuntu, and to forums in general, so bear with me.

Anyway, I have Ubuntu and Windows XP separately partitioned, and when my computer is started, the GRUB OS select menu comes up quite nicely. However, This is a shared computer, and i'm the only one who wants to use Ubuntu. For the benifits of the other people, I want to increase the amount of time to choose the operating system, and move the xp select area to the top of the list.

To do this, i've read that you have to enter this: gksudo gedit /boot/grub/menu.lst - into the terminal. it asks for my password, and then it opens a **blank** GEdit window called menu.lst (/boot/grub). If im right, this pang is supposed to have some sort of something on it, but it dosent.    (What is gedit?)

So what's happening? and how can i alter the settings?

If it helps, i'm running Ubuntu 9.10, with GRUB version 1.97~beta 4

---

### Post by beastrace91 on 2009-11-07
This process changed some in 9.10 (which now uses Grub2) The file you want to edit to change the default and increase the time out duration is the /boot/grub/grub.cfg. You will need to edit this file as super user so do ```
sudo nano /boot/grub/grub.cfg
``` and make any edits you want to.

Regards,
~Jeff

---

### Post by luxobumbrata on 2009-11-07
> **beastrace91 said:**
> This process changed some in 9.10 (which now uses Grub2) The file you want to edit to change the default and increase the time out duration is the /boot/grub/grub.cfg. You will need to edit this file as super user so do ```
sudo nano /boot/grub/grub.cfg
``` and make any edits you want to.

Regards,
~Jeff
Thanks, that seemed to work quite well, hovever, it opens a large script telling me not to edit anything. I'm not used to this kind of thing.

---

