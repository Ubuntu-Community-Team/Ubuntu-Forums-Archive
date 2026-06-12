---
title: "Ubuntu 9.04 hangs when idle"
date: 2009-11-27
forum: General Help
---

### Post by MauritsMB on 2009-11-27
Hello everyone,

Since two months I am using Ubuntu 9.04 (don't feel like upgrading yet, since I only just get to know the system). I seem to have a problem with Ubuntu whenever my PC hibernates, goes idle or whatever it is called. I saw a thread with this problem for the 9.10 version, but somehow I couldn't find a solution to my problem.

The thing is, every time my goes idle, the computer wont respond en the screen stays blank, I can only restart my pc by pushing the reboot button.

As for my PC info ia am using :
AMD Athlon 64 X2 Dual Core Processor 4400+ 
1.8 GB Memory 

I hope someone could help me or direct me to a solution for the problem.

Cheers guys!

---

### Post by MauritsMB on 2009-12-03
Does anyone have a suggestion?

---

### Post by MauritsMB on 2009-12-15
is there no one who can help? 

Thanks!

---

### Post by ean5533 on 2009-12-15
> **MauritsMB said:**
> Hello everyone,

Since two months I am using Ubuntu 9.04 (don't feel like upgrading yet, since I only just get to know the system). I seem to have a problem with Ubuntu whenever my PC hibernates, goes idle or whatever it is called. I saw a thread with this problem for the 9.10 version, but somehow I couldn't find a solution to my problem.

The thing is, every time my goes idle, the computer wont respond en the screen stays blank, I can only restart my pc by pushing the reboot button.

As for my PC info ia am using :
AMD Athlon 64 X2 Dual Core Processor 4400+ 
1.8 GB Memory 

I hope someone could help me or direct me to a solution for the problem.

Cheers guys!
My AMD Athlon 64 X2 laptop couldn't handle hibernation either. I know hibernate has been one feature that's been actively worked on in the last few months, but I don't know if it's gotten any better. 

I actually just turned off hibernate completely. You can do this by going to Power Settings in the system preferences menu. Make sure to change the settings both for when you're on AC power and on battery power (two different tabs).

If hibernate is a necessity, I'm afraid I can't help much, but maybe someone else can.

---

### Post by MauritsMB on 2009-12-15
The strange thing is that in my Power Management I already set the settings to never suspend or hibernate. Still after ca. 2 hours it hibernates/suspends (i suspect) and freezes. Its I think similar to the problem with 9.10, but I dont know a solution. I will try setting a screensaver, maybe that'll work?

---

### Post by ean5533 on 2009-12-15
> **MauritsMB said:**
> The strange thing is that in my Power Management I already set the settings to never suspend or hibernate. Still after ca. 2 hours it hibernates/suspends (i suspect) and freezes. Its I think similar to the problem with 9.10, but I dont know a solution. I will try setting a screensaver, maybe that'll work?

On that note, I know that there was a bug in whatever version of gnome-power-manager shipped with 9.10, it wasn't actually saving settings changes. Computers were sleeping/hibernating, displays turning off, and so forth regardless of settings. A recent update solved that problem a week or two ago (for me, at least). Maybe it solved the problem for you too? Do the normal update process (sudo apt-get update && sudo apt-get upgrade) and then try messing with your power settings. Maybe the problem fixed itself.

---

