---
title: "Windows get dark?"
date: 2009-10-01
forum: General Help
---

### Post by ludoludoludo on 2009-10-01
Hey - 
I'm fairly new to ubuntu, been using it about a month now with very few problems.  But I'm having one reoccurring problem.  Every now and then I'll be doing something and the window will grey out.  It seems like it would be memory-related, but I have 2GB and my systems monitor is showing only 30% in use when this happens.  It DOES happen almost consistently with [http://www.formula1.com](http://www.formula1.com) but every now and then it'll happen while doing other things (not always internet related!).  Any info on this would be greatly appreciated.  Thanks ! - mike

---

### Post by earthpigg on 2009-10-01
windows grey out to indicate to you that the given program isn't responding.

often, it is just momentary... letting you know the program won't respond until its done with whatever complex mathematical calculation it is doing.

if it ***never*** un-greys out, then that program is frozen... stuck in some sort of infinite loop. imagine if you gave a piece of paper with 'please flip paper over' written on both sides to something that has no common sense, but will follow directions exactly... like a computer :lolflag:.

has more to do with CPU than memory. your entire computer locking up is when we would suspect memory as the culprit. 

maybe we could increase your performance by taking a look at what is eating up CPU cycles...

install htop
```
sudo apt-get install htop
```

run htop
```
htop
```

sort by CPU and keep an eye on it. does anything seem out of the ordinary to you? this is where that common sense that you and i have, but a computer does not, comes in handy.

---

### Post by ludoludoludo on 2009-10-03
thanks - I figured it was something along those lines.  I've been monitoring everything and I got Mozilla to grey out on the Formula 1 website.  It showed my CPU as peaking at 69%, and Mozilla's use went up.  Other than that, nothing changed.  Maybe it's something with their website? 
Another time it greyed out I was using word processor.  I noticed that my wireless connection was being reset for some reason (borrow the neighbors, not too sure what's going on there). 

But at least I know what it means now.  Thanks !

---

