---
title: "Laptop froze and forced to hard reboot"
date: 2012-01-23
forum: General Help
---

### Post by coldjeanz on 2012-01-23
Running Wubi.

I tried every single one of those commands that is supposed to force a clean reboot and nothing would work. My laptop just completely froze in the middle of using it and I was unable to get control again. I had to hard reboot finally after 15 minutes of listening to a 3 second portion of a song on a loop. Once I hard rebooted it took longer than usual to get back to the desktop and now my fan is running really loud and won't stop.

I'm utterly disgusted with Linux/Ubuntu up to this point. Never once in the last 7 years of using Windows did it ever freeze on me. In the week that I've been using Ubuntu I've had it crash on me twice, only the first time I was able to get control of it again. Absolutely ridiculous.

---

### Post by SuaSwe on 2012-01-23
Lucky you didn't pay for it then, ey! ;) Sometimes Ubuntu takes a bit of work. If you're looking for a totally problem-free OS with tech support providing fixes you pay to guarantee, Linux is probably not for you. 

At this particular moment though, it sounds to me like something could be hogging resources on the machine. Have you had a look at System Monitor (Applications > System Tools on newest version) or similar to see if something suspect is going on? It could also be something vendor-related - could you provide some more detail on the computer itself?

---

### Post by coldjeanz on 2012-01-23
I installed Ubuntu because I used to hear people talking about how smooth it is and how you rarely experience all the nagging problems of Windows. 

While it is true Ubuntu uses up a lot less memory than Windows, it does have its own fair share of problems. The CPU usage spikes really high when I'm using Chrome. It's always in the 20-30's. I'm using Windows right now and the CPU usage is at 0-2% constantly as I type this using Chrome. CPU usage in Ubuntu seems to be really high with just about anything. But the memory usage is fairly low. What could be causing the high CPU usage with Ubuntu?

I should also mention that Banshee seems to crash quite a bit. Today when I was using it (prior to the hard reboot) my fan went crazy and the CPU usage spiked to 86% and I couldn't figure out why. I looked at Banshee and the program had froze and I had to force quit it.

Laptop specs: intel core i5 430m 4 GB RAM, bought it almost 2 years ago

It's a crappy display model though so it's probably a bit older than that and was used quite a bit. Needless to say I'm never buying a display model again, only reason I picked it up was because I had some trade in value with another laptop.

---

### Post by SuaSwe on 2012-01-23
Haha, yep, that's a risk with display models and such!

I was looking around for Chrome CPU issues and noticed that there appears to be some Task Manager function within Chrome which can be brought up by Shift+Esc (or right-click along the top and select Task Manager) - not sure if it works in Ubuntu but maybe it could give some clue, such as whether it might be a plugin causing the high CPU load. 

Regarding Banshee, it seems it does have some history of crashing - see [this post]("http://ubuntuforums.org/showthread.php?t=1490527"), for example - some diagnostic info contained in there!

---

