---
title: "Hibernate / Suspend issues"
date: 2010-11-23
forum: General Help
---

### Post by ranxerox on 2010-11-23
Note:  the following has *not* fixed the problem.  This problem is *not* solved for me.

Since I upgraded from 8.04 to 10.4 and then to 10.10 recently (yes, I know, long overdue) my IBM ThinkPad T42 has not been resuming from hibernation properly.  Once in a while it works but not generally.

I finally found a [solution]("http://www.ubuntugeek.com/fix-for-suspend-and-hibernation-problem-for-laptops.html") that seems to work.  At least so far.

Plus, it handles suspend by saving to disk and then saving to RAM, so if the power runs out during a suspend it should still resume from disk as if it were hibernated.  I have not checked that but the disk indicator looks like it really does work that way so I have high hopes.

In case the link above goes away, the bottom line is this:

[LIST]
[*] [FONT="Courier New"]sudo apt-get install uswsusp[/FONT]
[*] use [FONT="Courier New"]s2ram[/FONT] in [FONT="Courier New"]/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux[/FONT]
[*] use [FONT="Courier New"]s2disk[/FONT] in [FONT="Courier New"]/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux[/FONT]
[/LIST]

The [ubuntuGeek]("http://www.ubuntugeek.com/") page explains in a little more detail.  Thanks to whoever wrote it up, and thanks to the creators of [FONT="Courier New"]uswsusp[/FONT].

---

### Post by ranxerox on 2010-11-23
Well, it's the next morning and the machine wouldn't resume again.  Same behavior as before.  I am very disappointed.

10.x has broken hibernate for my T42.  It worked in 8.04 over a period of years.  This is written up in forums all over the internet so I'm not going to expect any joy from posting here.

---

### Post by makitso on 2010-11-23
I share your frustration.  I have three laptops S/R works intermittently on all of them (from 8.04 to 10.10).  My main one is a dual boot system but I mostly use WIN7 for this reason.  

I have been trying to get my wife to move to Ubuntu on her T61 Thinkpad.  This is the main reason for her not moving.  

I just don't think linux will ever be solid and reliable in this area.

---

