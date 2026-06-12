---
title: "Slows Windows Boot After Installing Jaunty"
date: 2009-07-04
forum: General Help
---

### Post by pcooney on 2009-07-04
Problem:  I've noticed a drastic decrease in boot time for Windows XP after installing the Jaunty edition of Ubuntu.  

Background:

1.  I setup a dual boot configuration using the default GRUB boot loader. 
2.  Previously it would take seconds for Windows XP to finish loading after showing the desktop screen.  Now it takes a couple of minutes once the screen shows up.  
3.  After the initial boot windows seems to run as normal.  
3.  I performed a defrag before creating the Ubuntu partition 
4.  I only gave Ubuntu about 40 gigs for its partition.  
5.  The total windows partition size is 255 gigs, and I currently have approximately 148 gigs free. 
6.  Ubuntu loads quickly, and I've noticed no problems there.  

Thoughts:

I really don't know what to make of this.  I thought that once I selected windows from the boot loader menu that it would take over and not be affected by Ubuntu in any way.  I haven't installed any major update or software on the Windows partition since I've installed Ubuntu.  

I'll be glad to answer any questions.  I'd really appreciate any ideas!  Thanks!

---

### Post by TeoBigusGeekus on 2009-07-04
I think it is accidental.
Once you select windows from grub, Ubuntu has no interaction whatsoever with your system.
What can I say?
Other opinions?

---

### Post by Celauran on 2009-07-04
Is this an ongoing issue? Because you resized Windows' partition, the first time you boot into Windows after having installed Ubuntu will be slow. It should go back to normal after that, though.

---

### Post by pcooney on 2009-07-07
> **Celauran said:**
> Is this an ongoing issue? Because you resized Windows' partition, the first time you boot into Windows after having installed Ubuntu will be slow. It should go back to normal after that, though.


Yes it's an ongoing issue.

---

