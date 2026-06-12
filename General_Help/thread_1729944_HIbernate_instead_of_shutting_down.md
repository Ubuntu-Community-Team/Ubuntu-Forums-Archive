---
title: "HIbernate instead of shutting down?"
date: 2011-04-15
forum: General Help
---

### Post by telegiovi on 2011-04-15
Hello everyone!
I discovered that it is possible to hibernate the PC.  I do not understand which difference (practical) there is between hibernate and shutting down; can I simply Hibernate every time that I finish with my PC?
What do you think about? Isn't it easier? And quicker?
Thank you for an opinion.

---

### Post by DanneStrat on 2011-04-15
> **telegiovi said:**
> Hello everyone!
I discovered that it is possible to hibernate the PC.  I do not understand which difference (practical) there is between hibernate and shutting down; can I simply Hibernate every time that I finish with my PC?
What do you think about? Isn't it easier? And quicker?
Thank you for an opinion.

Hi!

Hibernate is a power-saving system state.

When you hibernate the computer the contents of

RAM is written to an image-file on the

harddisk(swap partition or swap-file)and the computer is 

completely shut down.

When you power it on again, the system´s previous state is 

restored from the image.

You could actually use hibernate instead of shutdown if you feel it´s faster.

---

### Post by lithopsian on 2011-04-15
Hibernate used to be a lot faster than rebooting, but in many cases this isn't true any more.  It can even be slower.

It allows a complete power down of the machine while remembering exactly the state of every application and window.  The similar suspend (to RAM) also remembers the exact state but continues to use some power.

Hibernate doesn't always work reliably or at all.  More and more complex hardware sometimes just won't come back properly from hibernation.

Hibernate requires a root partition at least the size of your RAM.  This didn't used to be an issue since you needed at least that much to safely run your computer, but with 4GB and more of RAM there is simply no need for that much swap any more except for hibernation.  Space is cheap though.

If it works reliably for you and is quicker than rebooting then feel free to use it.  Certain things only happen when you reboot fully, such as checking your hard drives, so reboot occasionally.  Consider dropping the fsck interval if you work this way, so that the drivers may be checked as often as every time you reboot.

---

### Post by nerdy_kid on 2011-04-15
In my experience, hibernating on Linux has been a terribly slow and painful process.  Last time I did it it took about twice as long to resume from hibernate as it did to boot Ubuntu and login.  I havn't tried it recently, maybe its improved.

---

