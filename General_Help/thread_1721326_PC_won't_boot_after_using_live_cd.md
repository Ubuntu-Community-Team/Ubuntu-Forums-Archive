---
title: "PC won't boot after using live cd"
date: 2011-04-04
forum: General Help
---

### Post by dancol on 2011-04-04
Hello,  I'm having a problem with my Vaio laptop after using an Ubuntu live cd, when I turn it on it doesn't boot, a black screen is displayed and it beeps three times (one long , two short), I think this has something to do with the video card.  The last time I used the live cd I didn't wait for Ubuntu to shutdown completly and removed the cd when it was still on the process of shuting down.  What can be causing this problem? Please help me fix my laptop.

---

### Post by Dupointx on 2011-04-04
> **dancol said:**
> Hello,  I'm having a problem with my Vaio laptop after using an Ubuntu live cd, when I turn it on it doesn't boot, a black screen is displayed and it beeps three times (one long , two short), I think this has something to do with the video card.  The last time I used the live cd I didn't wait for Ubuntu to shutdown completly and removed the cd when it was still on the process of shuting down.  What can be causing this problem? Please help me fix my laptop.

Your receiving a hardware malfunction error 'Beep' code from the mother board in your laptop.
In this case it sounds like your hardware may be damaged.
Stopping the Live-CD before proper shutdown shouldn't matter by the way.

From [Wikipedia article]("http://en.wikipedia.org/wiki/Power-on_self-test"):''
**Original IBM POST beep codes**

1 long, 2 short beeps - [Display adapter]("http://en.wikipedia.org/wiki/Display_adapter") problem (MDA, CGA)''

Maybe your video card is busted?

That's about all I can do to help. You should consider taking your computer to a expert or getting warranty service if you have it.

---

### Post by dancol on 2011-04-04
Hmmm, so it was just a coincidence that the video card failed when I removed the live cd? Thanks for your help.

---

### Post by Dupointx on 2011-04-04
> **dancol said:**
> Hmmm, so it was just a coincidence that the video card failed when I removed the live cd? Thanks for your help.
From what I know, the computer loads most of Ubuntu into RAM when using a live-CD, and then if you need more data Ubuntu reads it off the CD (hence the slow down that occurs). Removing the CD won't cause Ubuntu to crash right then and there, but it may cause problems when you open a application like Firefox for example.

Trying to pinpoint what caused the failure is futile, it could have been damaged before using the live-cd (this is speculation since you didn't specify). I've had hardware fail and it's pretty random, but sometimes it looks like cause and affect, but it's just not worth worrying about.

Tip: if your laptop came with Windows and it's under warranty I wouldn't tell them about using Ubuntu. They may try to act like they are not responsible for repairing your computer. As long as you didn't install they won't be able to tell, since there is no trace of the Live-CD after shutdown.

---

### Post by dancol on 2011-04-04
Ok I will take it to an expert, thank you very much.

---

