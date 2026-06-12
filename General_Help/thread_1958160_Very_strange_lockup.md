---
title: "Very strange lockup"
date: 2012-04-13
forum: General Help
---

### Post by Straemer on 2012-04-13
Ok, so my computer has been locking in a very strange manner recently. It started about 2 weeks ago, and has happened about 4 or 5 times. I'm running Ubuntu 11.10, kernel version 3.0.0-17-generic.

This usually happens when I've left my computer on for a while (it happened today when I was at work), but it did happen once when I was actually using it.

Basically what happens is the whole system locks up. If my monitor was on at the time it happened, the screen stays there, otherwise my monitor won't recognize input when I turn it back on.

USB devices seem to remain turned on (My mouse and keyboard still have lights on - my motherboard will still provide power to USB devices when my computer is on, but my mouse and keyboard only light up when the computer is on) and my CPU fans and indicator LEDS are still on as well.

I've tried ssh-ing into my computer in this state as well, but that just times out telling me the host isn't available.

The only pattern I seem to notice that causes this is that I tend to be doing a lot of disk I/O when it happens. The last time it happened I was tarring a rather large collection of files, other times I was torrenting stuff... (the files were being tarred on my internal drive, and the torrents were going to my external drive, so I somehow doubt it's one of the drives causing the problem)

I don't think I've installed any new packages that would have caused this... I do install updates regularly though.

Is this a known bug in the kernel? Any idea of what to do to solve this? Sorry if I've rambled on too much, I just want to provide as much information as possible.

---

### Post by matt_symes on 2012-04-13
Hi

Check for hardware problems such as an overheating chip computer or hard drive problems.

Check to see if the caps lock or other keyboard leds are blinking. This is indicative of a kernel crash.

Kind regards

---

