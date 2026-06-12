---
title: "Overclocking in ubuntu"
date: 2012-02-14
forum: General Help
---

### Post by vanquishedangel on 2012-02-14
OK, this is a thread in response to the lack of success on the topic, so please don't post that overclocking is dangerous, or you should do it from the bio's or anything like that. There are a million threads with those posts in it, this one is about what i have found and you may add to it if you found anything.

My computer doesn't have a bios option to overclock anything, it is not in the bios that this can be done.

I overclock my ATI 6450 card and have for awhile to great success using amdoverdrivectrl, I would also like to do the same for other aspects of my computer but to no success, people in linux don't post what they know about it as in how to do it, and what programs to use.

Also if people know how to overclock using other programs, that would be something to post in this thread.

I have found that to limited success, powertweak still works in the latest Lubuntu. it requires a few old lib's that are not in the repositories anymore, but still available online. it doesn't have the updated code to see all things to tweak but many still work and it needs updating, if i knew how i would do it myself, but alas i do not.

A good thing about powertweak is that it refers to manufacture specifications of the hardware to tweak. alot less risk of damage then.

so the settings i use for amdoverdrivectrl is 

Low: gpu 100 mhz, memory 150, voltage .870
medium: gpu 400mhz, memory 667, voltage .900
High: gpu 725 mhz, memory 800mhz, voltage 1.000

and for powertweak I just lowered latencey for now, til i can work with it more.

MORE: I have noticed that my system is running way better than before with better appearance to even with just the latency changes, to note I also added some changes to my system in /etc/default/grub like "pcie_aspm=force" to the "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" line to look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force" to get rid of an apparent graphics power drain that the newer kernels have and this helped alot. (source is here [http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html](http://www.webupd8.org/2011/06/linux-kernel-power-issue-fix.html)).
Another thing i did was run "sudo apt-get build-dep (program name)" for all programs I need full functionality of, like wine for example or the ati drivers from jockey as well, or libreoffice. Also I use openjdk-7 it improved everything.

My spec are HP DC7100 3.8 HT ghz processor, 4 gigs ram, ATI radeon HD 6450

---

