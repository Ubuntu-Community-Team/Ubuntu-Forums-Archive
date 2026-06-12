---
title: "why do i feel slow? (new to linux)"
date: 2006-04-03
forum: General Help
---

### Post by newpants2003 on 2006-04-03
1. for example: using firefox, when i swich a tab is's like a 0.5s delay, for the same computer it does not happen to windows, and same situation for many other apps. 
it just the way it is? or i could do some setting about?
2. kde and gnome which one is better? 
someone tell me the kde is more powerful is that right?
3. and the pwer manager for gnome is way toooooo simple for a laptop, is there a simmilar one like in KDE?

thanxxx a lot.

---

### Post by professor_chaos on 2006-04-03
what are your system specs?

I find my linux system is as fast, if not faster in many desktop uses than windoze.

---

### Post by Jason_25 on 2006-04-03
1. Do you think millions of experienced computers users would use linux if delays like you mentioned were "just the way it is".  Save that for the windows world.  Post your hardware specs if you expect help on a performance problem.

2.  This is an extremely technical debate.  

3.  What features do you feel are missing?

---

### Post by nanotube on 2006-04-03
[QUOTE=newpants2003]1. for example: using firefox, when i swich a tab is's like a 0.5s delay, for the same computer it does not happen to windows, and same situation for many other apps. 
it just the way it is? or i could do some setting about?
[/quote]
the firefox that comes with ubuntu is for some reason pretty slow. you should install firefox 1.5, by following these instructions:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)
> 
2. kde and gnome which one is better? 
someone tell me the kde is more powerful is that right?

kde vs gnome is a kind of a long-standing discussion. you can learn a lot by searching these forums for kde vs gnome threads. :) in general, yes, there seem to be a lot more options to tweak in kde, but it also seems that kde is somewhat more resource-hungry and somewhat less stable.
> 
3. and the pwer manager for gnome is way toooooo simple for a laptop, is there a simmilar one like in KDE?
thanxxx a lot.
dont know anything about the kde power manager...

---

### Post by newpants2003 on 2006-04-03
centrino 1.1 (running 600 most time)
512mb
1gb swat
30gb hd 4200

(dell latitude x1)

feel the same for other linux system too.....

hope someone can tell me how to run the ubuntu as smooth as winxp.

for the power manager, what i really want is when you close the laptop it will suspend to the ram automaticlly

---

### Post by nanotube on 2006-04-03
well, you seem to have been complaining about the speed of firefox, not ubuntu in general, is that correct? if so, then if you upgrade firefox to 1.5 as per the instructions in the link i posted earlier, it will be much much faster.

as to the suspend when you close lid, you would have to fiddle around with some acpi shell scripts. most notably, /etc/acpi/lid.sh. but dont go mucking around with it before finding detailed instructions on how to do that. just search this forum. :)

---

### Post by Christmas on 2006-04-03
Hmmm i think in firefox i get the same problem and for example when moving another window in "front" of the firefox open window it has some kind of "traces" meaning it moves very slow, like mouse trails from xp for example. I also tried epiphany (which) i'm using now, but it's the same. Anyway it's no such a big deal.

---

### Post by Christmas on 2006-04-03
And btw i heared that GNOME is not using 2D acceleration. Is that true, and if it is, can this be the problem?

---

