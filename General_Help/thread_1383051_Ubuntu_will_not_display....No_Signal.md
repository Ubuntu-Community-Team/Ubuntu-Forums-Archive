---
title: "Ubuntu will not display....No Signal"
date: 2010-01-16
forum: General Help
---

### Post by Boris and Bailey on 2010-01-16
When I start Ubuntu, the Ubuntu logo appears, then the screen goes black and "No Signal" appears on the monitor screen.

Earlier today, I installed a new processor, a dual-channel AMD from a single channel AMD. I decided to put the entire computer into a new case since I was dismantling everything. I have two hard drives: one for Ubuntu and one for Windows XP.

When I started it up, I got errors 13 and 17. I went into the BIOS and changed the disk order. Now Grub appears and I can get into Windows, but I cannot get into Ubuntu.

Anyone with any ideas on what I can do to access Ubuntu?

---

### Post by dcstar on 2010-01-16
> **Boris and Bailey said:**
> When I start Ubuntu, the Ubuntu logo appears, then the screen goes black and "No Signal" appears on the monitor screen.

Earlier today, I installed a new processor, a dual-channel AMD from a single channel AMD. I decided to put the entire computer into a new case since I was dismantling everything. I have two hard drives: one for Ubuntu and one for Windows XP.

When I started it up, I got errors 13 and 17. I went into the BIOS and changed the disk order. Now Grub appears and I can get into Windows, but I cannot get into Ubuntu.

Anyone with any ideas on what I can do to access Ubuntu?

Put the video card back in the same slot it was originally in.

---

### Post by pastalavista on 2010-01-16
> **dcstar said:**
> Put the video card back in the same slot it was originally in.
That's a pretty good guess because he didn't say he moved it. I'm curious if you're right.

---

### Post by Boris and Bailey on 2010-01-16
Thank you for answering. There is just one PCI-E slot and that's what I use for the video card. I did have to take it out so I could remove the circuit board. It's a logical guess. Windows XP works, so that makes me think something else is going on. (If I had my way, Adobe Systems would make their softwares for Linux as well and then I'd get rid of Windows in a heartbeat, but that's off the subject.) Any other ideas on why Ubuntu does not get a signal on the monitor?

---

### Post by pastalavista on 2010-01-16
Have you tried booting Ubuntu in recovery mode? If you can, open a terminal and enter ```
sudo dpkg-reconfigure xserver-xorg
```and try the main boot again.

---

### Post by Boris and Bailey on 2010-01-16
that worked,pasta! Thank you very much!

---

### Post by pastalavista on 2010-01-16
> **Boris and Bailey said:**
> that worked,pasta! Thank you very much!
You're welcome, glad I could help. I hate to see people stuck with just Windows ;) Be sure and mark this post 'solved' with the thread tool.

:D

---

### Post by dcstar on 2010-01-21
> **Boris and Bailey said:**
> that worked,pasta! Thank you very much!

If you are still using 5.10, I hope you are aware that it is no longer supported and a later Ubuntu version would not have had the problem because they auto-detect the video card on every boot-up.

---

