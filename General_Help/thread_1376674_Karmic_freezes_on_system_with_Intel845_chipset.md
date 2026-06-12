---
title: "Karmic freezes on system with Intel845 chipset"
date: 2010-01-09
forum: General Help
---

### Post by jcobban on 2010-01-09
I am still desperately seeking a solution to the frozen GUI in Karmic.

Although I have no firm documentation my assumption is that the problem is related to the relatively old Intel 845 chipset which implements the on-board graphics and support for suspend/resume, which are the two features of Karmic which fail.

Other posters have suggested that if I am having so much trouble with Karmic I should just go back to Jaunty.  However Jaunty's support for the Intel 845 was much worse.  The display was constantly flickering, frequently so badly that I could not even click on hyperlinks, or select specific cells in a spreadsheet.  And suspend/resume, which as an environmentally conscious user I would like to exploit, did not work at all.  In Karmic the support for Intel graphics has been moved into the kernel, which resolves those problems.  Furthermore Karmic is generally a much better release than Intrepid or Jaunty.

People have frequently pointed me at a posted procedure for installing the Intrepid version of Xorg to get around problems in Jaunty and Karmic.  I was skeptical because the symptoms reported in that procedure are not what I am experiencing.  I was not observing "performance" problems, although that may have been because I have turned off all of the graphics goodies in the UI.  Furthermore, in part because Karmic is so much better, I really do not want to move backwards. But since I have been unsuccessful in getting the problem addressed, I have followed that procedure.  The consequences are unacceptable.  I am back to the screen flickering, and suspend hangs the system!

I would have expected that simply based upon demographics there would be some employees of Intel working as volunteers on Ubuntu who would be contributing expertise to the support of their employer's hardware.  I can appreciate that everyone is more interested in adding support for the latest chipsets and graphics cards, but there must still be millions of Intel based PCs using the 845 chipset out there.

I would really like to be able to use my Ubuntu system as my primary workstation, but I cannot until I can resolve this problem.

---

