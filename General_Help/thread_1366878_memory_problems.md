---
title: "memory problems"
date: 2009-12-28
forum: General Help
---

### Post by jlaugh on 2009-12-28
I recently installed Ubuntu. I now have problems with the overall speed of the computer. Ubuntu seems to think that I only have 243MB of mem and uses 89% of that all the time with no programs running. Apparently it has split the memory into two halves and I can't seem to change it. i haven't been able to install any pluggins or other software cause the computer is trying to do to much at once. How can I change the setup to recognize all the memory available or am I just stuck with it? I really don't want to go back to Microsoft but I will if I cant have a computer that runs right.

---

### Post by jlaugh on 2009-12-28
bump

---

### Post by HappyFeet on 2009-12-28
Are you sure the memory is seated correctly?

---

### Post by jlaugh on 2009-12-28
Yes in fact it hasn't been touched. I installed ubuntu after windows got corrupted and I didn't have a recovery disk. In the system monitor it has two CPU's listed and shows only half my memory.

---

### Post by Sef on 2009-12-29
1) Please wait at least 24 hours before bumping your thread.

2) Run memtest86.  It is in GRUB's start up boot menu.   Run it overnight and see if anything comes up.  For more information on memtest86, click [here]("http://www.memtest86.com/").

---

### Post by jlaugh on 2009-12-29
the memtest didn't work the last time I tried it, but I will try again and see if the outcome is different.

---

### Post by jlaugh on 2009-12-29
really need some help here

---

### Post by -kg- on 2009-12-29
> **jlaugh said:**
> the memtest didn't work the last time I tried it, but I will try again and see if the outcome is different.

So were you able to run the Memtest?  If not...

Memory *does* go bad.  Sometimes after quite a while; sometimes after a very short period.  You can get brand new memory that is faulty.

You previous posts give me a sneaking suspicion...did Windows actually become corrupt, or did one of your memory cards give out on you?  Do you have two memory cards installed, or is it just one?

If you have two cards installed, what would give me these suspicions is that you show only half of your installed memory.  That would be a good indication of a faulty memory card.  Also...

I just read back over the original question and you state that it shows 243 MB of memory (half of what's installed).  Are you running a laptop?  Some of your RAM may be dedicated to graphics, which would also explain the high usage.  You might want to switch off any special effects, which would take a higher amount of RAM for video processing.

If nothing else, try these steps (naturally, you should shut your computer down completely before taking these steps):

Get into your computer case and unplug and replug each of your memory cards a couple of times each.  Then boot your computer and see if the reported memory has changed.

If not:

Shut it down, then take one of the cards out of the case, leaving the other plugged in.  Reboot the computer again (or at least, try to).  If you are able to boot into the computer and it shows the same amount of memory, then shut it down again, plug the memory card that you removed back in, and remove the other and reboot.

If you find that one of the cards is bad (i.e., you can't boot the computer at all with that card plugged in), all you need do is replace it. This can be a plus, because you can find out if it can be upgraded and get more RAM to install. If it reports the same amount of memory no matter which card is inserted, or if it reports any difference in RAM amount when you remove one or the other of the cards, then you have a different problem.

---

### Post by lukeiamyourfather on 2009-12-29
How much memory is shown as installed during POST? If it doesn't show the full amount during POST then its likely a hardware or BIOS issue and unrelated to Ubuntu. Cheers!

---

### Post by jlaugh on 2009-12-29
i will try that tonight.

---

