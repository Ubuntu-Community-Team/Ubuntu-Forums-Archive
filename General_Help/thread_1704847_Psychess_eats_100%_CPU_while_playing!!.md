---
title: "Psychess eats 100% CPU while playing!!"
date: 2011-03-11
forum: General Help
---

### Post by Rushyang on 2011-03-11
Hey guys!

No doubt Psychess is a very nice game for playing chess. I was playing this game often. But one thing I observed today is Psychess starts to eat 100% CPU right after the moment we start the game. I came to know about this after observing the "System Monitor" applet graph on the panel. This must not be normal because it's common sense when developer develops a software they always consider the CPU usage.. Even when I develop scripts I always give a *sleep* after heavy resource usage. For the record, I installed DreamChess and it works fine.

---

### Post by searchfgold6789 on 2011-03-11
Well what are the stats of your computer? Have you compared them to the recommended minimum requirements on the website for the software if there are any?
I have an old P3, so alot of programs will hog CPU.
Also, I know of many games that give an option for setting the CPU usage. Maybe your hardware configuration is "telling" it to use a lot of CPU. Knowing your computer stats would help me answer this question better.
 - search

---

### Post by Rushyang on 2011-03-11
I have C2D E7300 2.66Ghz  processor & 4GB RAM sir.. There is no way a chess game should use whole C2D Processor!

---

### Post by howefield on 2011-03-11
Chess games can be sore on processors and RAM. After all, the object of the game involves pure calculation, and lots of it. Calculation is heavy on the processor and hash tables heavy on RAM.

Are you using an openings book ? If you are and the program is still eating you processor in the opening stage, I'd be concerned.

---

### Post by Rushyang on 2011-03-12
I am not using any openings book.. My question is just this: "When I start game, (not running ANY program/script/cron beside game at the same time), it starts eating 100% of my processor.. at the same time.. when I start DreamChess ONLY.. it's processor-friendly..

---

### Post by gmargo on 2011-03-12
What package are you talking about?  Did you mean **pychess**?

---

### Post by Lobais on 2011-03-25
If you are playing against an AI it will always use as much power as it can, in order to find the best move.

In PyChess specifically, two extra AI's are started which provide data for the hint and spy modes. These also use as much power as they can, but obviously with a very low priority.
If you don't use hint and/or spy mode, you can disable them in the preferences. This will make your system monitor look more calm.

---

### Post by geoaraujo on 2011-06-21
> **Lobais said:**
> If you don't use hint and/or spy mode, you can disable them in the preferences. This will make your system monitor look more calm.
Thank you!

---

