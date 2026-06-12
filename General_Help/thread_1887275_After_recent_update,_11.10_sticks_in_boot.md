---
title: "After recent update, 11.10 sticks in boot"
date: 2011-11-26
forum: General Help
---

### Post by strange_cathect on 2011-11-26
I have a fresh install of 11.10. I performed some updates today. However, now I am stuck in the Ubuntu splash screen upon boot. I am unable to progress beyond this point.

Can anyone assist me on this or know what happened?

Thanks

---

### Post by helios16v on 2011-11-26
I don't know how much this will help but what I've found from installing Ubuntu 11.10 is to stay away from it and if you ARE diving in to the new bugs since 11.04 then you must do a clean install and wipe the drive prior to installing it.

I tried to update the computer at work and the whole thing wouldn't work, after a really long boot time, GNOME would work but apps would stay open for more then a few seconds even if they did open. I decided to cut my losses and install 11.04 again as a fresh install and ignored the update that appears until I read about it being more stable.

EDIT:
This thread may help

[http://ubuntuforums.org/showthread.php?t=1883103](http://ubuntuforums.org/showthread.php?t=1883103)

---

### Post by strange_cathect on 2011-11-26
I wonder if it is the new update to the kernal. This has some similar behavior that was reported a few days ago.

---

### Post by Bliepo32 on 2011-11-26
GRUB gives an option to boot older kernels. Give it a try and see if it works.

---

### Post by strange_cathect on 2011-11-26
When I first had the problem, I selected for a normal boot. However now, GRUB2 is not giving me an option for another kernel. 

When I boot I just get the Ubuntu splash where it hangs forever.

---

### Post by strange_cathect on 2011-11-26
Ok, was able to use Cont+Alt+F1 to get to command line and was able to log in. 

Now I need to figure out what to do next? Ugh, this is annoying.

---

### Post by strange_cathect on 2011-11-26
Ok, getting a warning message: **Failed to load NVIDIA kernel module. No drivers available**

**Fatal: Module navidia-current not found.**

This is clearly a video driver problem related to the kernel upgrade. Does anyone have any experience with resolving this?

---

### Post by strange_cathect on 2011-11-26
I purged nvidia-common then re-installed and rebooted. All better.

---

