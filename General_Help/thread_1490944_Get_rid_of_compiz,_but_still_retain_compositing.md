---
title: "Get rid of compiz, but still retain compositing"
date: 2010-05-23
forum: General Help
---

### Post by tom.swartz07 on 2010-05-23
Hi all,

Ive been having some really severe problems with compiz on my computer, and Im at a point of utter frustration. 

I want to take compiz off of my computer, but I do not want to lose compositing effects, because I run docky (which needs it to run)


Essentially, the problem with compiz, in a nutshell, is that it continually freezes on me when I try to scroll a webpage too fast, or if a fast-paced flash video plays, or anything that might choke up the window manager does. I end up having to pull up a terminal, killall compiz, then restart it manually; it works again until I try to scroll too quickly or something and then it will lock up again.



I know I could run compiz on this computer, but I dont know why this current version will not cooperate, so in lieu of finding a solution, I kinda want to just purge it.


Any ideas on how I could do this?

---

### Post by -humanaut- on 2010-05-23
I believe the default Ubuntu installation has compositing without compiz installed. You should be able to remove it and turn on the default visual effects.

---

### Post by tom.swartz07 on 2010-05-23
> **-humanaut- said:**
> I believe the default Ubuntu installation has compositing without compiz installed. You should be able to remove it and turn on the default visual effects.

see, this is where Im not too sure- i think compiz is installed by default, but it doesnt have the 'high gloss' effects enabled at the time. 

I believe that metacity is also installed by default? Does anyone know if that has compositing?

---

### Post by Elfy on 2010-05-23
Yes - it does. I use awn - the mnetacity compositing works fine. I turn off compiz completely

Alf+F2 - gconf-editor

/apps/metacity/general - enable the compositing manager

---

### Post by tom.swartz07 on 2010-05-23
> **forestpiskie said:**
> Yes - it does. I use awn - the mnetacity compositing works fine. I turn off compiz completely

Alf+F2 - gconf-editor

/apps/metacity/general - enable the compositing manager

perfecto! 
Just as i refreshed the page, I ticked the box that does the same thing in ubuntu tweak. haha


Ill see how this pans out for the time being!

Thanks guys!

---

