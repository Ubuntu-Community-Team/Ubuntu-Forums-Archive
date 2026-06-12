---
title: "updating query"
date: 2010-10-09
forum: General Help
---

### Post by rdh61 on 2010-10-09
Hi,

I have (for once) a perfectly working system (lucid). Several times in the past I have picked up annoying little bugs after running update manager. I wish to avoid this, and have two queries about it.

1) Often it seems to be new kernel files that bring the bugs. If I install updated kernels, is there an easy way to uninstall them without breaking the system? In the past I have uninstalled updated kernels, leaving the old ones, and then my system has not been able to boot.

2)  I wish only to install a few at a time, so that it's easier to know and remove the source of any bugs. But update manager selects updates by default.  If there are many files to update, unselecting them takes a long time. Is there any way to have the tick-boxes unselected by default?

Many thanks.

---

### Post by t4thfavor on 2010-10-09
synaptic can uninstall kernels, and without uninstalling you can select an older kernel at boot time by hittig esc in the short time when the grub menu appears.

as for the other Q I don't really know. try synaptic for that too it's much more powerful than update-manager, but I hear it's less "safe" as it will allow you to uninstall stuff that you need to boot the system, like all your kernels.

---

### Post by rdh61 on 2010-10-12
Hmm... The last time I used Synaptic to uninstall the most recent kernel (leaving the old one), I couldn't boot up any more. If the situation comes up again I won't remove the new one, just boot into the old one through the boot menu.

As to my second question, I've discovered the answer. Right click anywhere in the list of updates and click on "uncheck all". Perhaps there should be a button to make it more obvious.

Thanks for your answer.

---

