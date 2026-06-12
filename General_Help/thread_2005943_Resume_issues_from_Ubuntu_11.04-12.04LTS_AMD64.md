---
title: "Resume issues from Ubuntu 11.04-12.04LTS AMD64"
date: 2012-06-18
forum: General Help
---

### Post by NotSoRandomUsername on 2012-06-18
Hello,
I have issues resuming my laptop when it has suspend more than 20 Minutes (Or so). I've had this same issue on Ubuntu 11.04/11.10/12.04(Current). I have to do a hard reset in order for it to work. It's not a Xorg issue since it absolutely does nothing (HDD indicator doesn't go on, WiFi indicator does not come on , External mouse doesn't light up). I have tried to remove ACPID and ACPI which did not work. Also it does not write log files while in the inactive state Which makes it harder to troubleshoot. I have looked everywhere but can't seem to find a solution. I would be very grateful if someone would help me. 

[B]In short:
[/B]Issue: Frozen / Unresponsive laptop after trying to resume when it's been suspended for more than 20 Minutes (Or something).
Ubuntu versions where I encountered the same problem: 11.04 11.10 12.04.
  
[B]Laptop Specifications:
[/B]Packard Bell TK81
RAM: 6GB DDRIII
GPU: AMD HD6650M
CPU: AMD Phenom(tm) II N970 Quad-Core Processor
Software: Ubuntu 12.04 AMD64 Kernel 3.20.5

---

### Post by NotSoRandomUsername on 2012-06-18
Bump

---

### Post by Gadgetech on 2012-06-18
Since you mention that you have problems when it's been suspended more than 20 minutes, presumably it works if it's been suspended for only 10 minutes or so. This makes me think that it might be related to a power saving feature in your computer's BIOS settings. There may be something in there that times out after 20 minutes and tries to go to a hibernate or power off state. This is pure speculation, but it warrants looking into.

---

### Post by NotSoRandomUsername on 2012-06-18
Yes I thought the same but I have hibernation disabled and I can activate it using my keyboard meaning that there is a listener active and thus has not hibernated. On Windows 7 it worked fine. Still don't regret deleting Windows nor will I ever. Thanks for you're time anyway:)

---

### Post by NotSoRandomUsername on 2012-06-19
Once again a bump.

---

### Post by overdrank on 2012-06-19
Please do not bump your thread so quickly. Once a day (24 hr) is polite. Thanks

---

### Post by NotSoRandomUsername on 2012-06-19
Didnt know that my bad.

---

### Post by jmfal on 2012-06-27
Hi NotSoRandom,

I don't use a laptop so I can't help.

If you go to the "Hardware and Laptop" section of the forum and click on the "search this forum" tab,  and enter something like "resume problems" you might find a thread that will fix your problems.

---

### Post by NotSoRandomUsername on 2012-06-29
Thanks for your help it's appreciated.

---

### Post by bamdad.khan on 2012-10-13
hi,

have you found out what the problem was? i'm having the exact same issue you described (since 11.10). i have a question asked here: [http://askubuntu.com/questions/198495/why-doesnt-my-computer-resume-after-sleeping-overnight](http://askubuntu.com/questions/198495/why-doesnt-my-computer-resume-after-sleeping-overnight)

haven't been able to figure out what's wrong so far.

thanks,
bamdad

---

