---
title: "Asus A50IJ"
date: 2011-07-26
forum: General Help
---

### Post by Karlas on 2011-07-26
Hello I just bought asusn a50ij and of course I installed ubuntu,now I have few problems:
when I try to add CPU frequency scaling monitor to panel it says:

CPU frequency scaling unsupported

Next problem:my cpu temp is 49 without any reason.and I cant see my graphic card temp,when I go to Harware Drivers I doesnt show any drivers at all,so I dunno whether its nvidia or raedon it doesnt say anything!
HELP!

Also I installed jupiter and each time I turn on my computer it goes to Maximum Performance how can I turn it off?

---

### Post by Mark Phelps on 2011-07-26
You should NEVER just force an install of any Linux distro onto new, untried, hardware.  Seeing what will work, and what will not, is the main reason for being able to run the Distros in LiveCD mode.

You've not given us any hardware specs for your laptop, so there's basically no way we can even GUESS what will work, and what will not.

Those CPU temps are to be expected, if scaling really is NOT supported, and if you run the laptop a full-scale, you will seriously shorten its life.

As to video drivers, once again, without info, we can't advise you.  Open a terminal, enter "lspci", look for the line containing "VGA" -- and post the results back here.  If you have an Intel chipset (very likely), those drivers are installed automatically -- and there are likely NOT to be any updates.

---

### Post by Karlas on 2011-07-27
CPU intel Celeron T3500 2.1 Ghz Dual.
Graphic Card Intel GMA 4500M&#8207;

---

