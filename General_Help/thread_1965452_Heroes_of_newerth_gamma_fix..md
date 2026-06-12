---
title: "Heroes of newerth gamma fix."
date: 2012-04-25
forum: General Help
---

### Post by knezan on 2012-04-25
So I recently transferd to ubuntu from windows so Im kind of new at this stuff. Anywho Im a huge fan of the game Heroes of newerth and Im playing it ALOT. The good thing about the game is that it already has an linux verision that works very well besides a few problems. Some I have already fixed and now one that I almost have fixed. It's a gamma problem, since the gamma options in HoN dousnt work in linux for some reason I needed to find a way to make the gamma higher.

I found a helpfull thread " [http://ubuntuforums.org/showthread.php?t=1543269](http://ubuntuforums.org/showthread.php?t=1543269) " that helped me with the problem but now I was thinking if there is anyways to improve it. What the script douse it that when ever you start the created file you start the game with 1.5 gamma, everything is fine and all but I was thinking if there is anyway to make the gamma switch back to 1.0 whenever I tab down?

Since Im new at this I would love some detailed instruction if there is any.

heres the script content. 

#!/bin/bash
xgamma -gamma 1.5
/home/knezan/HoN/hon.sh
./hon.sh
xgamma -gamma 1.0

What I know is that whenever the game is running the gamma is 1.5 and when its not running it goes back to 1.0. 

All help is appreciated.

Sorry if I place the thread in the wrong section, as I said , Im new to ubuntu aswell this forum. 

-knezan

---

