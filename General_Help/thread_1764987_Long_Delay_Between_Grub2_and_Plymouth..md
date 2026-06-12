---
title: "Long Delay Between Grub2 and Plymouth."
date: 2011-05-22
forum: General Help
---

### Post by DinoT1985 on 2011-05-22
Hi ):P

I'm running Natty with Unity 3D. I had a long black screen with no Plymouth Ubuntu logo boot. After the black screen, Natty loaded straight into desktop.

Then I installed this
[http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/](http://paolobernardi.wordpress.com/2011/05/01/fix-plymouth-on-ubuntu-after-installing-nvidia-or-ati-proprietary-drivers-for-ubuntu-11-04-natty/) 
Which now gives my Grub2, about 10 seconds of black screen, Plymouth Ubuntu Text boot and then desktop.

Any way to remove that long delay?

HP Pavilion dv7 Notebook PC
Ubuntu 11.04 amd64.
NVIDIA Driver Version: 270.41.06 (Recommended driver)
1440x900-24 Resolution

---

### Post by DinoT1985 on 2011-05-23
Bump.

Also now when I boot, Unity is the default size with lenses missing. If I log out and log back in again, its back to the way I had it. There is only me as a user on the laptop.

EDIT: Reverting the changes from the scrip and that solved this problem. Now only the delay to get rid off.

---

### Post by DinoT1985 on 2011-05-23
bump

---

### Post by AMSlider on 2011-05-26
I get the same long pause, not sure howto fix it though... I get the grub2 menu, then a long pause (10 seconds) of black screen, then the ubuntu screen with the loading progress bar for a split second, then the GDM login screen.  Sorry I couldn't be more helpful, but I'm experiencing the same thing.

I've got an Nvidia 8600GTS, running on an LG FLATRON M2762D at 1920x1080

---

### Post by nema.arpit on 2012-07-23
Sorry to bump this old thread, but has any one found the cause or a fix? I am having the same problem on Precise : I have a 10-15s delay between selecting the OS and the loading progress bar.
EDIT: I searched around for a bit and finally found that my ureadahead is not working correctly.

---

### Post by tazzarkin on 2012-11-21
Same problem.  Any fix to this?

---

### Post by wildmanne39 on 2012-11-22
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

