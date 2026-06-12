---
title: "After installing 11.4, Brother printer vomits blank paper"
date: 2011-08-27
forum: General Help
---

### Post by malenkylizards on 2011-08-27
I had no problem printing from my Brother HL-2140 printer...until I upgraded to 11.4.  After I did so, I installed the printer, and had no apparent trouble; it shows up in the Printing window with a check.  However, when I try to print anything, it continually spits out paper without printing anything on it, and will apparently go through the entire stack.  It can't be stopped without turning off the printer manually, at which point it jams and I have to tug the paper out.  How can I solve this?  Thanks for your help!

EDIT: Another detail, I'm running a dual-boot with Ubuntu 11.4 and Windows XP.  The printer works just fine on the Windows side, so there shouldn't be any problems with the mechanics or toner; I just replaced the cartridge a month or two before, anyway.  Is there any terminal output I can post in order to help troubleshoot this?

---

### Post by malenkylizards on 2011-08-29
Bump.  I could really use some help with this!  My whole family is starting school this week and we're going to need to be able to print stuff soon.  Is there any way I can solve this problem, and is there any more information I can give you?

---

### Post by uRock on 2011-08-29
Post 5 in this thread looks to be promising, [http://ubuntuforums.org/showthread.php?t=1748457](http://ubuntuforums.org/showthread.php?t=1748457) 

This one offers post upgrade fixes as well, [http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by xandr55 on 2011-09-13
Any luck with fixing this? I seem to have the same problem. If the suggestions above helped you fix it maybe indicate what specifically and mark the thread as solved?

Ok for my problem (Brother HL 2040, xubuntu 11.4) the fix suggested in that first link worked. 

From nixuntu on that thread:

[INDENT]the default driver "Brother HL-2140 Foomatic/Postscript" is what makes it print out all them blank pages change it to "Brother HL-2140 Foomatic/hpijs-pcl5e (recommended)" and it will print just fine.[/INDENT]

---

