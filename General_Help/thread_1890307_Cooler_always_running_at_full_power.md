---
title: "Cooler always running at full power"
date: 2011-12-03
forum: General Help
---

### Post by Novak on 2011-12-03
Since i installed kubuntu (few days ago) my cooler works at full power and this causes faster discharging of thr battery(i don't like it!).Before kubuntu i used SLED 11 and cooler worked normally.I using HP ProBook 4530s.What should i do?Someone please help me!:(

---

### Post by Basher101 on 2011-12-03
KDE is a heavyweight in terms of an interface. I read that it has some CPU issues that let it run at 100% load all the time. You should switch to Gnome or unity or anything else in particular, or you could search the forums for solutions. But changing the Desktop Environment should give the fastest and easiest resolution to your problem.


regards

---

### Post by Novak on 2011-12-03
With command "top" i see system using CPU from 7% to 15%,but cooler working manic.It is an Intel Core i5 2410M 2.30GHz.

---

### Post by Basher101 on 2011-12-03
I have not much expirience with KDE as i do not use it at all...still try another Desktop Environment and see if the issue remains there. If it does then it could be a kernel bug of some sort...

---

### Post by Mark Phelps on 2011-12-03
Sorry ... but overheating is a known problem with the recent kernels being used in Ubuntu 11.10.  They're still working on fixing this.

---

### Post by tartalo on 2011-12-03
Although the author uses a Thinkpad the Howto is valid for you too:
[http://forums.debian.net/viewtopic.php?f=16&t=62579](http://forums.debian.net/viewtopic.php?f=16&t=62579)

KDE has a plasma widget that allows monitoring temperatures, activate it and keep a close eye, just in case.

---

### Post by 2F4U on 2011-12-03
Try disabling some or even all of the graphical effects and see if it helps. If it does, try enabling effects one by until the machine is getting hot again. Some of the effects in KDE place a real burden on CPU and graphics card.

---

### Post by Redblade20XX on 2011-12-03
Since your running kubuntu, try and disable some of the index filing services such as nepomuk and akondai server. There is a bug in the server, I believe, that causes it to reproduce several processes of itself and use up all your resources. Hopefully this also helps!

- Red

---

### Post by oldtimer7777 on 2011-12-03
> **Novak said:**
> Since i installed kubuntu (few days ago) my cooler works at full power and this causes faster discharging of thr battery(i don't like it!).Before kubuntu i used SLED 11 and cooler worked normally.I using HP ProBook 4530s.What should i do?Someone please help me!:(

I would check your BIOS settings and see if you can change your CPU Fan speed, and adjust it from there. That is what I use for the same type of issue myself.

---

### Post by Novak on 2011-12-04
ok

---

### Post by Novak on 2012-01-05
There is no BIOS options for adjust cpu speed or fan speed.I turned off switchable graphic from BIOS (to reduce temps-no efect),tried to change line in grub GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1 i915.lvds_downclock=1".Still temps. are always above 45 degrees and fan always works very loudly,and i am so frustrated.

---

