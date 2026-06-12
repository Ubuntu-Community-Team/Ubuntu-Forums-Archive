---
title: "Need help on setting permanent display resolution"
date: 2011-07-19
forum: General Help
---

### Post by vcrpcant on 2011-07-19
Hi,

I need help on setting permanent display resolution.

I want my pc to always start in 1024x768, even if I switch monitors and graphics board.
Is this possible?

I'm on 10.04 32 bit.
Thanks on advance

---

### Post by dandnsmith on 2011-07-19
Try System|Preferences|Monitors - I think that was what you asked for (gets the desktop res set)

---

### Post by neba on 2011-07-19
Are you using Nvidia? That is what I have on my pc. I open up nvidia Xserver then go to 'XServer Display Configuration' find 'Resolution'  change it to the resolution you want, then click 'apply' to make sure it works. If everything works fine, click 'Save to Configuration File'. This works for me. every time I restart up. 
******Make sure you back up your x server file first.*********
easy way to do that is going to /ect and coping X11 to your desktop. that way if you have any problems then you can just replace that file and everything will be how you had it.

---

### Post by vcrpcant on 2011-07-20
> **dandnsmith said:**
> Try System|Preferences|Monitors - I think that was what you asked for (gets the desktop res set)
that's only temporary. When I restart it gets another resolution:(

---

### Post by vcrpcant on 2011-07-20
> **neba said:**
> Are you using Nvidia? That is what I have on my pc. I open up nvidia Xserver then go to 'XServer Display Configuration' find 'Resolution'  change it to the resolution you want, then click 'apply' to make sure it works. If everything works fine, click 'Save to Configuration File'. This works for me. every time I restart up. 
******Make sure you back up your x server file first.*********
easy way to do that is going to /ect and coping X11 to your desktop. that way if you have any problems then you can just replace that file and everything will be how you had it.

I forgot to mention I'm using VGA onboard (ATI ES1000) :(

Anyone has some idea? :confused:

---

### Post by dandnsmith on 2011-07-20
It's not that temporary - I've been using it for 6 months over multiple reboots (lost count) without it ever changing.
I'm prepared to believe that change of monitor or graphics card might change things, but Ive the feeling that I did the graphics card change, checked it, and found it was still set (all with Ubuntu 10.04)

---

