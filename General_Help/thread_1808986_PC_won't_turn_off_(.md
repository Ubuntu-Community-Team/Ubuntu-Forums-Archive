---
title: "PC won't turn off :("
date: 2011-07-21
forum: General Help
---

### Post by ausairman on 2011-07-21
Hi everyone,
You probably need more info to diagnose this but I'll just tell you what I know and you can let me know how to extract more info. I am running the latest version of Ubuntu on my 64-bit 2nd gen i7, with 8gb of ram. I am running both windows and ubuntu on separate partitions.

When I shut down ubuntu, it always gets stuck on that ubuntu logo after a few seconds. I suspect it's to do with the way that ubuntu tells the computer to switch off. Windows shuts down/turns off fine.

Are there any log files I can somehow post here that will help to resolve this?

---

### Post by MG&amp;TL on 2011-07-21
Manually force a turn-off (i.e. hold the power switch), and see what sort of things pop up on screen. Obviously you can't post all of them, but if there's something that doesn't look right, remember that and post that. I don't know whether this will bring anything up, but I think it's worth a go.

---

### Post by ausairman on 2011-07-21
Well, nothing pops up when I press the power button, it just turns off. Some text appears as its shutting down, but then it just goes to the ubuntu logo and stays there. Can I disable that logo to find out where it's getting stuck?

I'm also not getting any errors that it didn't shut down properly, presumably because it did shut down and just didn't tell my computer to shut down properly... I'm using an optiplex 990, which is a fairly new machine so is it possilbe that they use some fancy bios command to switch off that the ubuntu community hasn't had a chance to implement yet?

---

### Post by sisyphus1978 on 2011-07-21
Try ```
sudo shutdown -h now
``` in a terminal.

---

### Post by MG&amp;TL on 2011-07-21
Or if you want to restart:

```
sudo reboot 
```Is there ones for logout and suspend as well, or are they graphical only? Only a workaround if it does work, but it's better then nothing. :)

Often I find as new releases come around, less bugs appear, so if you are lucky, it may get fixed with the next release?

Have you tried doing this with different desktop environments? Try it with GNOME (Ubuntu classic) as well as Unity. If Unity doesn't work, but gnome does, you could always try unity 2d, and see if it is the 3d that is the problem.

---

### Post by MG&amp;TL on 2011-07-21
There's a 'man' entry for 'reboot' and 'shutdown', a page for logout (although this does not seem to be a terminal command, more a function, e.g. int logout(); :confused:

Suspend does not have a page.

---

### Post by MG&amp;TL on 2011-07-21
> **ausairman said:**
> I'm using an optiplex 990, which is a fairly new machine so is it possilbe that they use some fancy bios command to switch off that the ubuntu community hasn't had a chance to implement yet?

Possible, but unlikely, I would have thought. Unless my view of operating systems and computers is VERY warped, BIOS stays pretty much constant. (hence** Basic** Input/Output System, I suppose)

---

### Post by ausairman on 2011-07-21
I just ran a bunch of updates for the first time in 2 weeks and the computer switched off fine!

I'm assuming that means it's fixed, touch wood.. Thanks for the feedback :)

---

