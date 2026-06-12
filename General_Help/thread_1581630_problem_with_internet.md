---
title: "problem with internet"
date: 2010-09-25
forum: General Help
---

### Post by pingpong89 on 2010-09-25
Hi,
I have been trying to install ubuntu 10.4 on a laptop toshiba satelite c650-150d from a cd and have run into a few problems.
The first problem I came across was after installation the computer ejected the disk and my screen told me to take it out, close the tray and press enter. The screen continued to show this message and kept loading indefinitely and not restarting. I forced the computer to turn off and then turned it back on. Nothing seemed to be wrong but in fact I could not connect to the internet. I went through the help and run into another problem in 5.2.2. Check for device recognition, when i type 'sudo lshw -C network' into the terminal, I get SCSI but never an actual output.
Another problem is that the computer seems unable to turn off on its own and needs to be force.
I have reinstalled ubuntu from different cds and this has not made a difference.
Thanks alot for your help.

---

### Post by 666f6f on 2010-09-25
> **pingpong89 said:**
> Hi,
I have been trying to install ubuntu 10.4 on a laptop toshiba satelite c650-150d from a cd and have run into a few problems.

Not all hardware work out of the box in the GNU/Linux world. If you don't pick your equipment carefully, be prepared to get your hands dirty :)

> **pingpong89 said:**
> The first problem I came across was after installation the computer ejected the disk and my screen told me to take it out, close the tray and press enter. The screen continued to show this message and kept loading indefinitely and not restarting. I forced the computer to turn off and then turned it back on.

Hmm, it seems that power management doesn't work.

> **pingpong89 said:**
> Nothing seemed to be wrong but in fact I could not connect to the internet.

Today it must be the "Toshiba Satellite C650" day! There is another thread going on right now [here]("http://ubuntuforums.org/showthread.php?t=1581515") about network not working.

> **pingpong89 said:**
> I went through the help and run into another problem in 5.2.2. Check for device recognition, when i type 'sudo lshw -C network' into the terminal, I get SCSI but never an actual output.

Can you post the exact output of ```
sudo lshw -C network
```

> **pingpong89 said:**
> Another problem is that the computer seems unable to turn off on its own and needs to be force.

Power management doesn't work. We need to fix that somehow..

**UPDATE:** To fix power management, have a look at [this]("http://guide.ubuntuforums.org/showthread.php?t=1503491") thread. User coreyh says [those instructions worked perfectly for his Satellite C650]("http://guide.ubuntuforums.org/showpost.php?p=9767117&postcount=24").

> **pingpong89 said:**
> I have reinstalled ubuntu from different cds and this has not made a difference.

It shouldn't make a difference.

> **pingpong89 said:**
> Thanks alot for your help.

Welcome to the forums!

---

