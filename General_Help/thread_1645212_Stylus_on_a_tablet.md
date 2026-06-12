---
title: "Stylus on a tablet"
date: 2010-12-14
forum: General Help
---

### Post by rafa2010 on 2010-12-14
Hi All,

Just recently installed ubuntu 10.10 on my Fujitsu Lifebook tablet.  Must say everything works super, the stylus works off the box, sound, graphics, perfect.  I even installed Cell writer and xournal and am amazed at how good it works.  One tiny problem, though.  I wish to rotate my monitor, which, is also easy to do either using xrandr or even by going to the system>preference>monitors.  The problem is that as soon as I do, my stylus/pointer get misaligned.  That is, my pointer appears on a different part of the screen than where I actually put the stylus.  If I were using a mouse, I already know how to align by using synclient, but with the stylus, I'm in the dark.  The funny thing is, I believe the problem is really that Ubuntu is compensating when it should do nothing, that is, I believe even if the monitor is rotated, the stylus should not be realigned, but I think ubuntu is trying to realign when I rotate.  For instance,if I rotate the screen on a per software basis (like the document viewer), my stylus keeps working just fine.  Its just when I rotate the screen that I have a problem.  Does anyone have any clue how to align the stylus when the monitor is rotated?

Thanks!

:-)

---

### Post by Favux on 2010-12-14
Hi rafa2010,

Welcome to Ubuntu forums!

What you need to do is rotate the Wacom devices: stylus, eraser, and touch (if your tablet pc has it) along with the screen.  You do that using the Wacom driver.  I have example scripts on the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").  Methods 1 and 3 should work for you.

However most Fujitsu users use the fjbtndrv (fujitsu button driver).  In addition to rotating things it adds bezel button function.  I think [Robert Gerlach' PPA]("https://launchpad.net/~khnz/+archive/ppa?field.series_filter=maverick") has a working one for Maverick.  I know there were some bugs, some threads on that, but I think it was ironed out.

Hope this helps.

---

