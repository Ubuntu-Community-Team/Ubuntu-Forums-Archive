---
title: "Ubuntu locks up entirely on seemingly random occurrences"
date: 2010-05-24
forum: General Help
---

### Post by lennybird on 2010-05-24
Sempron 3100+, 512mb 400mhz RAM, Ubuntu 10.04 32-bit.


From what I've noticed, the computer seems to primarily lock up when an internet browser is open and/or being navigated (I'm testing this observation, now). I've tried Firefox and then installed Chrome; same thing. CTRL+ALT+F1 unresponsive, mouse is frozen.

Note that this is an old build given to me by a friend. The build originally had one stick of 512mb and 256mb. I took out the 256 for diagnostic purposes. Additionally, the computer originally had an nVidia 6200 graphics card, which I replaced with a 6600 I had lying around--again for diagnostic purposes. I installed the recommended video drivers respectively. After three re-installations of Ubuntu, 2 different browsers, 2 different graphics cards, running memtest86 and singling out the RAM, and using a can of air to eliminate any overheating issues, I'm unsure what to do next. I have a feeling this is operating system related, though. In BIOS, the CPU fan seems to be running at fine RPMs, but no temperature is given (thanks to terrible HP motherboards...)

Do note I am entirely new to the Ubuntu/Linux OS, and wanted a cheap, nice solution for this salvaged PC that I'm giving to my little sister. 

Any ideas?

Appreciate it,
-Jake

edit #1: Left the computer idling on desktop with no browser open; seemed okay for hours on end. I opened Chrome to the google homepage (with the Pac-Man flash theme at the time), and it did not freeze then as well when set to idle for hours at a time.

---

### Post by sylvester_0 on 2010-05-24
Please run
```
sudo apt-get install memtest86+
```
in a terminal then reboot and select memtest86+ at the grub screen. Let it run through the memory test a few times (I usually do at least 3.)

---

### Post by lennybird on 2010-05-25
> **sylvester_0 said:**
> Please run
```
sudo apt-get install memtest86+
```in a terminal then reboot and select memtest86+ at the grub screen. Let it run through the memory test a few times (I usually do at least 3.)

I think I did this already (though I got to memtest86 by some other means), it did more than 3 passes when I did it with no problems found (it was running for about 40 minutes). Tomorrow morning, I will run it again longer, though.

---

