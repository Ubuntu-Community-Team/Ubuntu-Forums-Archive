---
title: "W7-Xubuntu Dual Boot Hangs at Boot Selection"
date: 2012-08-11
forum: General Help
---

### Post by Benjiboy180 on 2012-08-11
Hello there. My problem is one that I am sure crops up quite often, but seems to be pretty user specific, so none of the fixes I have found seem to quite apply to me. 

My computer (an HP Pavillion dv6910us) is about 4 years old and originally came with Vista (upgraded to W7 when it came out). Recently I have decided that I am done with Windows (or should I say Windoze?) altogether and went on a Linux spree (made easy by Open Source programs!) and installed it on both my wife's computer (clean install) and mine (dual boot with windows 7).

Originally, my computer had a separate drive for recovery stuff (called D:). It has long since died for whatever reason and completely stopped doing it's job, so a whole 12 GB of harddrive space was just sitting there. So I reformatted it (from Windows) and then installed Voyager/Xubuntu 12.04 on that partition (which was handy because it was already partitioned, completely unused and just about the size I was looking for to try out Linux on this machine). 

The install went great! I used a Live USB to do it and it got up and running no problem. However, when I did my first restart, the bootup hung (as in froze, no keyboard functionality, etc.) on the Gnu Grub screen where you select which boot you want (i.e. Xubuntu, Xubuntu recovery, two memory tests and Windows 7). Since I was unable to do anything (and default boot didn't kick in at the allotted time), I restarted. 

This happened a few times, so I boot from a Live USB again and ran Boot Repair. Upon restart I was able to chose which boot I wanted (chose windows) and it was fine. 

However, I have noticed this happening off and on, though usually I can get it to work without having to run Boot Repair each and every time to get it to work. 

Is this some problem with how/where my /boot is installed? I know that the Boot Repair tool said something about /boot being located far away from something and maybe it needed to be moved (or a new one created closer). 

Anyway, I tried to be as comprehensive as I could with what little knowledge I have of Ubuntu/Linux. I am still trying to wrap my head around all of this stuff, but I am eager to learn (so a situation like this doesn't dismay me, I just see an opportunity to learn something).

I appreciate any assistance that anyone has (and sorry about all of the text, I just wanted to be thorough). I know you will probably want me to copy some logs or .conf files, and I can do that if you just let me know what exactly you want!

~Cheers

---

