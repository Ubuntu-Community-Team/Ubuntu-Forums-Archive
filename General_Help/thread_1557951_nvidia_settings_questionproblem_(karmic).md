---
title: "nvidia settings question/problem (karmic)"
date: 2010-08-21
forum: General Help
---

### Post by mal209 on 2010-08-21
Hi everyone, im new to linux and have been having trouble with nvidia settings.

the problem is i am using a HDTV as a moniter so i have to adjust the "overscan" function.  this is saved in "nvidia-settings" and can be run with the "-l" command at startup (so my research as shown).

my problem is that adding "nvidia-settings -l" to my startup app's doesnt take any effect.  typing that same command into the terminal or run windows doesnt work either.  the only variation that has worked for me is to use the "gksu" prefix (does not work with the standard "sudo" prefix).

when i use "gksu nvidia-settings -l" in the terminal, it loads my settings, but also pops up the x-server settings graphical interface.

is there a way to load the nvidia-settings without bringing up the graphical window?

Thanks in advance,
Michael.

---

