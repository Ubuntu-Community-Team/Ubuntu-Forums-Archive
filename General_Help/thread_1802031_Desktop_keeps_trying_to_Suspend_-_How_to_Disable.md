---
title: "Desktop keeps trying to Suspend - How to Disable?"
date: 2011-07-11
forum: General Help
---

### Post by dfour on 2011-07-11
I'm managing a desktop that is several states away. The person I'm working with has no internet and the computer IQ of a twig. We're running Ubuntu 10.04

It's a Dell 230 Slim tower. Ubuntu keeps trying to suspend the machine randomly for no reason. I had him disable suspend in the BIOS because the computer was just suspending sporadically. Now he gets a popup that says "Failed to Suspend, the computer failed to suspend. The failure was reported as cannot suspend"

He is running a custom Ubuntu distro I made. I have this same distro running on dozens of other computers with no issues. I can't figure out why this is happening. Is there anyway I can completely disable anything that would make the computer suspend from the CLI? Or where are the logs that I can look at to see what may be causing this? I can SSH into his machine but nothing more.

Thanks

---

### Post by DawieS on 2011-07-11
Does your custom Ubuntu version include the **System > Preferences > Power Management** options?

It is far easier to do there, than trying to change it in the BIOS. Select **Never** and click on **Make Default**.:wink:

---

### Post by wildmanne39 on 2011-07-12
Hi, also you can right click the desktop set screensaver to never,and in that window is the power management settings, set hard drive and screen going blank to never.

---

