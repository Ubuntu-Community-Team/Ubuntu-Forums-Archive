---
title: "Issues with external hard-drive after power cut"
date: 2010-01-02
forum: General Help
---

### Post by sizzler25 on 2010-01-02
Hi, 

I initially installed ubuntu 9.04 to an external hard drive which worked fine with my computer and then upgraded to 9.10 via the update manager and this also seemed to work fine. However, I recently experienced a power cut and since then ubuntu randomly crashes when I try to input anything (like clicking on firefox for example); I get a message along the lines of "input/output error" (I also get a pop-up warning but it only shows little squares :confused:). I can't even shut down, which means I have to resort to the unhealthy option of simply turning the power off. Upon reboot, there is a filesystem check due to the unclean shutdown and I evetually end up running fsck and typing "yes" to fixing disconnected inodes. However it is only usually a matter of time before the whole thing happens again.

I tried reinstalling ubuntu 9.10 from scratch but this hasn't helped - I even tried going back to 9.04 to see if this made a difference but I still get the same problem (I currently still have jaunty installed). This time when go to shutdown after a crash I get an "unable to read inode block" message.

Does this mean my external HD is corrupted? Is there anyway to fix this or am I going to have to bite the bullet and buy a new HD?

Any help much appreciated!

---

### Post by Groundswell on 2010-01-02
everything looks likes it's pointing to damage to the hd. did you have it plugged into a decent UPS or at least a decent pwr strip? 

try a low level reformat using gparted or something simlar. (it should be on a live boot cd, if not they make live boot cd's specifically for gparted

also there's some script that erases all data on the disk permanently by overwriting everything with 0's. can't remember where it is.

if you don't have a decent power strip of ups to plug it into, check the power supply on your computer, if it has an output plug try that.

---

### Post by sizzler25 on 2010-01-09
Hi,

I did have it plugged in to a surge protect power strip. I went ahead and ordered an internal HD (now that I have a bit more confidence opening up my computer!) and everthing seems to be working in order. I've reformatted the external HD so hopefully it will be useful as data-backup.

Thanks for posting :)

---

