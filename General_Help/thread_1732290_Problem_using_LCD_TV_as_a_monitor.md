---
title: "Problem using LCD TV as a monitor"
date: 2011-04-18
forum: General Help
---

### Post by blackmini on 2011-04-18
I have an old spare parts PC which my 5 yr old had been using with 9.10 installed with auto login etc. Ideal for educational games etc. When his old CRT monitor died I thought no problem... his LCD TV has a VGA input. The problem is that the TV will only see a PC output of xxxx X xxxx resolution. I set the PC to the correct resolution and all worked fine apart from losing the picture during the auto login process, due to a change in the resolution. Once login was complete the picture returned.

However... Once I upgraded the system to 10.10 on a larger HD I found that when I lost picture during the login process it was gone for good. Booting with a proper monitor attached shows that all is working ok. resolution is correct etc.

I'm stumped... any ideas?

Many thanks in advance

---

### Post by andrewc6l on 2011-04-19
If it's a Samsung LCD TV, this is a pretty common problem. You will probably need to add a modeline to your /etc/X11/xorg.conf file. Try searching the web with "*your model number*" and modeline - hopefully someone has already done it.

[http://andrewmemory.wordpress.com/2009/10/25/modeline-for-samsung-ln32a450c/](http://andrewmemory.wordpress.com/2009/10/25/modeline-for-samsung-ln32a450c/)

---

### Post by SeijiSensei on 2011-04-19
What TV and what video card?

---

### Post by blackmini on 2011-04-20
Hi,
The TV is a Technika xX22/14C and the card is a Radeon 9600 XT 256MB AGP
Hope that's helpful.
Many thanks :)

---

### Post by blackmini on 2011-04-20
No luck with the line mode search... my fault for buying a cheapo TV ;)
But thanks for a clue!

---

### Post by Grenage on 2011-04-20
> **blackmini said:**
> No luck with the line mode search... my fault for buying a cheapo TV ;)
But thanks for a clue!

As already stated, it's probably an EDID issue, which can be sorted with an xorg.conf.  It could probably also be sorted using xrandr, but I have no experience with it.

I have a rough guide [here]("http://www.grenage.com/xorg.html"), which can probably take you through the basic steps necessary.

---

