---
title: "overheating risk?"
date: 2011-03-10
forum: General Help
---

### Post by leeshaub on 2011-03-10
How big is overheating of a risk?

---

### Post by Grenage on 2011-03-10
That's a rather situational question.  A desktop or laptop at stock speeds is unlikely to suffer; 'some' laptops have issues with automatic fan controls.

---

### Post by leeshaub on 2011-03-10
have you hear that this is a HP Pavilon one of the ones that some thing goes bad on the video card.
-lee

---

### Post by Grenage on 2011-03-10
Generally graphical overheating is limited to overclocking, a defective fan, or very rarely by bad design; it's also normally easy to spot, because you'll get graphical corruption.

I wouldn't worry about it unless you see the signs.

---

### Post by psusi on 2011-03-10
Overheating of what?  Risk of what?  Computers are generally built to shut down if the cpu gets too hot these days.

---

### Post by leeshaub on 2011-03-11
it's a 5 year old computer on its way out

---

### Post by Grenage on 2011-03-11
While we don't know why it might be 'on its way out', five years isn't that old; not to mention, we still don't know why you think overheating might be a problem.

---

### Post by pqwoerituytrueiwoq on 2011-03-11
if it has sensors you can watch the temp
sudo apt-get install sensors-applet
overheating is a high risk if you block the airflow

---

### Post by northd_tech on 2011-03-28
> **leeshaub said:**
> have you hear that this is a HP Pavilon one of the ones that some thing goes bad on the video card.
-lee
I've read often before that the "higher-end" (once upon a time) HP Pavilion DV9700-9800-9900 series are very prone to [COLOR=Red]Graphics Processor (GPU) overheating[/COLOR].  I know that my HP DV98xx runs quite warm (especially during downloads, peer-to-peer file sharing, virus scanning, hard disk defragmenting, etc).  It seems like the [COLOR=Red]**hard disk, CPU fan outlet,** and **battery**[/COLOR] are the warmest areas on my HP laptop, and I sometimes see temperatures of 140-160F at the highest using the **sensors-applet** under Gnome (under the heavy use situations that I listed above), and it seems to run slightly (about 10-15 degrees F) cooler under Ubuntu than it does under Win Vista.  I suspect this might have to do with the specifics of power management, but I don't have any links to document this "hunch" of mine.  

I always make sure to keep the dual fan intake areas open (I have an older broken plastic laptop cooling pad about 2 cm [~ 1 inch] thick that I ALWAYS set my laptop on so that it can get cooling air, and the 17-inch wide HP laptop fan intakes "overhang" the edge of the narrower plastic cooling pad.).  This really cheap cooling pad once had dual USB-powered cooling fans, but one of the fan blades broke off causing a horrible screeching sound so I later used it just as a spacer "pedestal" to get cooling air.

Here is a hobby project "build" on a HP DV9700 (quite similar to my HP laptop):

[http://1journey.net/1candle/cp/cooling.htm](http://1journey.net/1candle/cp/cooling.htm)

and some more information about heating-prone laptops:

[http://repair4laptop.org/notebook_overheating_problems.html](http://repair4laptop.org/notebook_overheating_problems.html)

It is probably best to search this forum for the following strings and see if you see any common problems with hardware (I've seen Toshiba laptop fan problems being quite common):

**lm-sensors**
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

**sensors**
[http://ubuntuforums.org/tags.php?tag=sensors](http://ubuntuforums.org/tags.php?tag=sensors)

**sensors-applet**
[http://ubuntuforums.org/tags.php?tag=sensors-applet](http://ubuntuforums.org/tags.php?tag=sensors-applet)

EDIT:  Oh yes, I sometimes (about every 4 to 8 weeks) turn off the computer and **both GENTLY vacuum out and blow out** the fan inlets and outlets with a small "shop vac" to get the dust out of the CPU and GPU cooling fins.  Unfortunately, my HP laptop often accompanies me out into **very dusty** "desert" areas on dirt roads (but I try to keep it sealed up inside its case as much as possible and do this monthly-or-so "maintenance" and it has survived for about 3+ years now).

---

