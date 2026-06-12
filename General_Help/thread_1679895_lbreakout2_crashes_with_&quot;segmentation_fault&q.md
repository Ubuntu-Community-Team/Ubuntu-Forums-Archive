---
title: "lbreakout2 crashes with &quot;segmentation fault&quot;"
date: 2011-02-01
forum: General Help
---

### Post by JoJerome on 2011-02-01
Wasting too much time with this game the other day, the whole system froze up and I had to do a hard shutdown. Ever since then, the program won't load. No other programs seem to be affected. Tried uninstalling then reinstalling lbreakout2, to no avail.

```

~$ lbreakout2
LBreakout2 2.6.1
Copyright 2001-2005 Michael Speck
Published under GNU GPL
---
Looking up data in: /usr/share/games/lbreakout2
Looking up custom levels in: /home/mp/.lgames/lbreakout2-levels
Loading theme 'AbsoluteB'
Saving highscore chart in: /var/games
Segmentation fault

```

Of course, this could be nature's little way of telling me I should be doing less nostalgic arcade games and more homework, but still, would love to know if there's a fix for this. Thanks all!

---

### Post by JoJerome on 2011-02-07
Got the answer off another forum. 

[http://kubuntuforums.net/forums/index.php?topic=3115532.0](http://kubuntuforums.net/forums/index.php?topic=3115532.0)

But just in case anyone else on this forum has a similar problem...

```

sudo rm /var/games/lbreakout2.hscr
rm -r ~/.lgames

```

Since the error seemed to be in the high score files, I wondered if removing them would do the trick. Turned out in my naiveté I kinda/sorta had it right! Now, back to homework procrastination...

---

