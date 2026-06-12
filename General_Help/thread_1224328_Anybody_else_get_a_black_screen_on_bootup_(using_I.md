---
title: "Anybody else get a black screen on bootup? (using Intel 82G33/G31 onboard chipset + V"
date: 2009-07-27
forum: General Help
---

### Post by Rawblues on 2009-07-27
...my truncated title should have said "+ VGA connected TFT monitor)"

I have an annoying problem in that when I try to boot up into Ubuntu Jaunty, after the "loading" message, I just get a blank screen and the system stops. It doesn't always happen, but perhaps about 60% of the time.

Sometimes the system boots cleanly and my vga-connected tft monitor is set up correctly in 1440*900 24bit mode, and at other times, I get this....

"Ubuntu is running in low-graphics mode. 

The following error was encountered. You may need to update your configuration to solve this.

(EE) intel(0) No valid modes
(EE) Screen(s) found, but none have a usable configuration."

Anybody else had this kind of problem, and if so, what's the cure?

I've tried everything I can think of....

---

### Post by adam.ec on 2009-07-27
Yep, had exactly the same problem on Intel G31 motherboard. I followed the solutions on Canonicals release notes page for the Intel chipsets on Jaunty. This solved the problem you have just described but since I have suffered a whole stream of other unsavoury problems with graphics and absolute murder with USB. To be honest I have dropped back to 8.04 LTS as at least for me it is a lot more stable.

The odd few programs that I needed bang up-to-date I have installed from source but to be honest that was only Python, Django, Gimp and HP Printer Drivers. OpenOffice 3.1 is available as a package for 8.04. Hardy has been so.... er... hardy that i will probably wait for 10.x LTS before I upgrade again and make another mistake.

---

### Post by Rawblues on 2009-07-27
Thanks for your reply, adam.ec.

I was hoping to investigate Linux and Ubuntu as a possible development platform, but this doesn't look look too promising. Perhaps I need to wait a couple of months for things to stabilise a bit. 

I would reinstall with a previous stable version, but it would take be ages to get back to where I am, and who knows, I might just have a hardware setup that it just doesn't like! Annoying, though, because it all works with XP.

---

