---
title: "Replaing Fedora with Ubuntu on a Dual Boot"
date: 2012-01-18
forum: General Help
---

### Post by Jedwinjim on 2012-01-18
Hi, 

I'm trying to replace the Fedora partition (200gig) of my hard drive with Ubuntu 11.10 on a dual boot system (the other part being windows vista - 50gig).

When I put Ubuntu 11.10 in it gives me the following options:

Install side by side with Windows Vista - this is no good as it only allows up to 10gig of space as windows obviously takes up about 40fif here.

Replace Windows with Ubuntu - Not what I'm trying to do.

Advanced partition - I'm not sure what's going on here as I'm not great with computers! (all looks a bit confusing to me!)


The simplest way for me to do this is to completely erase everything & do a clean windows install, and then install Ubuntu side by side - but this would be immensely time consuming to start from fresh & also it's taken a while to get everything on windows the way I want it - I don't want to go through that again!

Is there a relatively simple way to just overwrite the Fedora partition with Ubuntu? (as is probably obvious already I'm not great with computers so layman's terms are greatly appreciated!)

Many thanks..

---

### Post by Matt__ on 2012-01-18
choose advanced,
identify which is your fedora partition (by size or format (ext3 I expect)) and highlight it.(check the format box too)
install ubuntu there by clicking 'Install Now'

[Illustrated dual boot guide](http://members.iinet.net/~herman546/)

---

### Post by Jedwinjim on 2012-01-18
Hi Matt, thanks for your response, although following your instructions I get the following error message:

"No root file system is defined. Please correct this from the partitioning menu."

Needless to say that doesn't mean a lot to me!

---

### Post by Matt__ on 2012-01-19
Ok in the advanced partitioning menu select the required partition and choose the 'change' or format option.
 in the pop up that appears:

[LIST]
[*]keep the same partition size in bytes
[*]select EXT4 for the partition format from the drop down box (If I recall its called "use as")
[*]check the format check box
[*]select / as mount point
[/LIST]
should be good to go now, enjoy Ubuntu.

---

