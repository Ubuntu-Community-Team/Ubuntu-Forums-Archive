---
title: "How to run memtest"
date: 2011-04-01
forum: General Help
---

### Post by borgward on 2011-04-01
I tried to run memtest, memtest memtest 86 memtest86 from the command line. All I get is command not found. I also tried those commands preceded w/sudo.
Synaptic Package Manager shows that memtest86 is installed.

---

### Post by MooPi on 2011-04-01
Reboot your computer and right after the bois splash tap the shift key. This should bring up the grub menu and you can select memtest from that menu.

---

### Post by seawolf167 on 2011-04-01
You can also run it from a live cd if needed. Instructions and the stand-alone live cd can be found [here]("http://www.memtest86.com/").

---

### Post by borgward on 2011-04-02
How long do I need to run it for my laptop?.

I have been told to run it for a week. That might be prudent for a server that others are relying on, but is running it 168 hours realistic for non critical use?

I can run, stop, run, until I have run it enough hours, or do I need to run from start to finish x number of hours w/no interruption?

---

### Post by Anonymous is Incognito on 2011-04-02
Generally running it overnight is generally enough, depending on the amount of RAM in your PC.

Some say that if you have loads of RAM it may tell you that everything is fine while it is not entirely (so minor problems).

If you want to be really careful, you can remove several RAM sticks and letting it run. This is something a small portion of the sysadmins sometimes do for production servers. It is not critical, and I would call it extreme paranoia for a home environment.

---

### Post by seawolf167 on 2011-04-02
I generally run it for 7+ cycles. When I'm OCing a new computer for myself, I'll run it for 3-4 days once I have everything tweaked to where I think the final values are, but you shouldn't need to run it more than say 9+ hours overnight if all you are doing it testing your RAM to make sure that it is factory-ok at stock settings. Any errors with new RAM at stock timings, frequency, etc. should be RMA'd.

---

