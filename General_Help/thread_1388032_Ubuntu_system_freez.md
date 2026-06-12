---
title: "Ubuntu system freez"
date: 2010-01-22
forum: General Help
---

### Post by 1995youssef4 on 2010-01-22
I had just installed ubuntu 9.10. It worked fine till i downloaded compizconfig and when i clicked on the ckeck box to try the effect the system froze and the mouse didnt move and sticked in its position. Nothing works its completely frozen. I pressed the power button for several seconds to shut the laptop then turned it on again and now it dont log in in to my account, it is freezed again. closed the laptop by the same way and opened again but with nothing different so i formatted it again same happened. I formatted about 3 times and now it dint want to open.
need help fixing this issue. 
* I got 2 GB RAM
  intel core 2 duo 2.4 GH

---

### Post by quixote on 2010-01-23
When you say "formatted it" do you mean you booted from a liveCD and reinstalled?  Or do you mean something else?

If the first, then the problem has to be a sudden hardware failure.  There's no way a compiz setting would survive a reformat.

If grub still loads, you can boot into recovery mode and run ```
metacity --replace
```.  Then run```
halt now
``` to exit.  Start up in the regular mode, and see if that helped.

---

