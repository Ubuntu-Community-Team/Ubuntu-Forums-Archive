---
title: "Sluggish/choppy compiz animations."
date: 2012-05-22
forum: General Help
---

### Post by brad1138 on 2012-05-22
I am happy with 12.04, Unity is actually growing on me. But the animations (shrink, zoom, etc) are commonly choppy. My machine is fairly fast (see sig) and should have no problem with any of the Unity animations. I saw a thread about problems with Nvidia driver, but I thought that problem caused it not to work at all. 

Any Ideas?

Thanks,
Brad

---

### Post by Linuxratty on 2012-05-22
> **brad1138 said:**
> I am happy with 12.04, Unity is actually growing on me. But the animations (shrink, zoom, etc) are commonly choppy. My machine is fairly fast (see sig) and should have no problem with any of the Unity animations. I saw a thread about problems with Nvidia driver, but I thought that problem caused it not to work at all. 

Any Ideas?

Thanks,
Brad

 I've had this happen. What I would do is turn Compiz off and turn it back on...It would then look for drivers..This happened at least once a week for over a year...Once it found the drivers it would ask if I wanted to keep the changes and I say yes. Then I'd go into the setting manager and reset the features I use.
 You can try this and see if it works.

---

### Post by wildmanne39 on 2012-05-22
Hi, see if this link helps.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

There are issues with the nvidia drivers in 12.04 depending on which card you have.
Thanks

---

### Post by brad1138 on 2012-05-23
> **wildmanne39 said:**
> Hi, see if this link helps.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)

There are issues with the nvidia drivers in 12.04 depending on which card you have.
Thanks

Thanks, that did seem to make a difference. 

IMHO the bigger issue really is what that link talks about and I have posted about before. From 10.10 to 11.04, compiz went from version .86 to .94, animations/graphics were smooth as silk even on slow machines in 10.10 (.86) and before, but 11.04 (.94) and after they have been choppy even on fast computers (even when not running Unity in 11.04). I have installed 6.06 through 10.10 on plenty of slow machines, early athlon XPs with 512 megs of ram and a nvidia 6200gs' and it was smooth. Smoother than my current machine. 

I am guessing whatever change was done to .94 was needed to be done to accommodate Unity. when I was running 11.04, there was a tread about reverting compiz to .86 because others noticed the same thing, it worked for a while but then conflicted with an update.

I guess what is frustrating is I could install 10.04, still supported, and have beautiful, silky animations. If I want a more current release, I have to spend time trying to make it look as good as it did years ago, and it never gets there. I would like to know what happened in .94, but I am not a programmer so I probably wouldn't understand it.

Just annoying I guess.

Thanks,
Brad

---

### Post by wildmanne39 on 2012-05-23
Hi, me to I have used compiz since I began with ubuntu about five years ago and it is up setting, I found out this release that most of the trouble is with the drivers and unity but I have not found a great solution.

I switched to xubuntu and the nouveau driver for a while and that made everything pretty smooth.
Thanks

---

### Post by debili on 2012-06-29
hi there,
I'm having the same issue with my GTX 560ti on ubuntu 12.04 If i leave compiz at it's default settings the animations aren´t smooth and i'm missing some frames . but when i uncheck ´detect refresh rate' and ´sync to vblank' the animations seem smooth , but if i move a window horizontaly i see an anoying line, lines or in other words tearing of that window.  pretty frustrating not to be able to get a smooth experience on ubuntu, my previous card was a GT520, I had the same issue..
if you had some suggestions, they're welcome thanx

---

