---
title: "Can I run dual monitors without more than mobo graphics"
date: 2012-10-08
forum: General Help
---

### Post by mightyguy198 on 2012-10-08
I recently got a second monitor really cheap but when i've plugged it in and tried to get it to be detected it only see's my monitor as unknown.

Beyond my motherboards onboard graphics I am running no other graphics cards, could this be an issue?

I have two of this monitor: [http://www.idealo.co.uk/compare/2438895/acer-g195hqv.html](http://www.idealo.co.uk/compare/2438895/acer-g195hqv.html)

Also its being run through a VGA splitter which again might be causing the issue as I only have one VGA port.

Running lspci | grep "VGA" gave me this:

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

---

### Post by wyliecoyoteuk on 2012-10-08
Unless your on board graphics supports multiple monitors (it will have 2 output ports), you need another card.
Even if your graphics has 2 output ports, it may only support driving one monitor, or if one is a DVI, it may not support analogue output.
What make/model of Motherboard?

---

### Post by mightyguy198 on 2012-10-08
Hi its an Asus P8Z68-V LX 

It has a VGA and a DVI slot.

If i need a graphics card can you recommend a very cheap one simply for the purposes of running a second monitor?

---

