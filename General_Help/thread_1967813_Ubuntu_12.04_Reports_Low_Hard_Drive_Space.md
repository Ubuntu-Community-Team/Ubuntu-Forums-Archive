---
title: "Ubuntu 12.04 Reports Low Hard Drive Space"
date: 2012-04-28
forum: General Help
---

### Post by TheMixtureMedia on 2012-04-28
Hey there guys not sure were to put this one in. I have Ubuntu 12.04 and my main drive is a 64gig SSD and Ubuntu says I have less then a gig left. I am not sure why I have nothing on that drive no games or other files. Can someone point me to how I can fix this issue please.

---

### Post by ventrical on 2012-04-28
> **TheMixtureMedia said:**
> Hey there guys not sure were to put this one in. I have Ubuntu 12.04 and my main drive is a 64gig SSD and Ubuntu says I have less then a gig left. I am not sure why I have nothing on that drive no games or other files. Can someone point me to how I can fix this issue please.

Are you using Disk Usage Analyzer or Disk Utility ?

---

### Post by TheMixtureMedia on 2012-04-28
When I go into properties of the home directory and it says I have about 800megs left. It comes up on screen and says that it is at the 1 gig mark for hard drive space. So I am not sure what to do or look for.

---

### Post by ventrical on 2012-04-28
> **TheMixtureMedia said:**
> When I go into properties of the home directory and it says I have about 800megs left. It comes up on screen and says that it is at the 1 gig mark for hard drive space. So I am not sure what to do or look for.


Could you go into the applications lens and run Disk Usage Analyzer, get a screenshot of that and post it?

---

### Post by TheMixtureMedia on 2012-04-28
Now it says I have under 800 megs left not sure what is going on.

---

### Post by pqwoerituytrueiwoq on 2012-04-28
how are your partitions laid out?
you are not using a /home partition with a size of ~2.6gb are you?
edit:
the ssd your only drive?
do you have trim enabled? that would really help
are you using noatime on the ssd in fstab? not doing so will result in massive disk usage over time without trim and wear the ssd out with ext4 at least

---

### Post by ventrical on 2012-04-29
Run the 'disk utility' app to get a better understandng of your partitions. This will tell you if there is anything up that is amiss with partitions.

---

### Post by ventrical on 2012-04-29
Here is a screenshot I am looking for.

---

### Post by saneearth on 2012-04-29
Looks like your home partition is only 1.5 GB in size. This appears to be the issue from your screenshot. I am not sure how your partitions are laid out, but it looks like your home got put one a partition more appropriate for swap. Did you let the Installer do the partitioning or did you do it yourself? I may be looking at it wrong, but that is the way it appears in your screenshot.

---

### Post by Gaygerbil on 2012-06-14
How would you fix this issue if this is what happened? My Gf installed Ubuntu 12.04 through the site and it didn't make her partition her HD's so I assumed that somehow they figured out a way to allow you to share the entire HD for both OS's (Windows and Ubuntu) however now she's getting an error of low disk space even though she has a ton of actual space left on her HD.

---

### Post by firekage on 2012-06-14
> **TheMixtureMedia said:**
> Hey there guys not sure were to put this one in. I have Ubuntu 12.04 and my main drive is a 64gig SSD and Ubuntu says I have less then a gig left. I am not sure why I have nothing on that drive no games or other files. Can someone point me to how I can fix this issue please.

I don't know if it will help you but i had similar problem with 11.10 - in my thread this is what were adviced to me, and it works:

> install the **dconf-tools** package and then run the **dconf-editor** and try changing the relevant settings in the following key:     Code:
     org.gnome.settings-daemon.plugins.housekeeping


I just disabled it because it always shown me warning, but i have few hard drive (over 500GB, over 640GB, and over 1TB) and he shown me warning with low disk space on root filesystem because in /media i have truecrypt container on partitions, and when truecrypt is used there is really low disk space on hdd (for an example: on 500GB hdd i have container that uses full space, so there was warning not because of mounted container but because of space on this hdd).

---

