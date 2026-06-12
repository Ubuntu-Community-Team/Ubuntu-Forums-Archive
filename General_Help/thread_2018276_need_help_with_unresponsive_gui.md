---
title: "need help with unresponsive gui"
date: 2012-07-06
forum: General Help
---

### Post by motoclaw on 2012-07-06
a few days ago, 4 days as of this morning i decided to install Ubuntu 12.04.
i installed from the cd and i installed updates and the recommended third party software.
everything went fine and for a few hours i had fun getting used to the new operating system.
everything was dandy except all of a sudden i found myeslf unable to click on the left bar (with all the buttons). this was strange. i was also unable to click on the top bar aswell. my mouse could move freely and i could click and right click on the tabs in Firefox.
clicking repeatedly had no effect on the sidebar whatsoever, it was as if it were a part of my desktop background.
right clicking on my tab and selecting move to a new window allowed the whole sidebar to be click-able again, aswell as the top bar. the problem was that no i was able to click on the side and top bar, Firefox and all of its tabs were unclickable aswell.
i cant drag any of my windows either.
i thought this was a unity problem so someone gave me the advise of using ''unity   --restart'' or refresh or whatever. it didnt work either
The second day i got a fresh .iso of 12.04 and a new cd. i burnt it then re-installed it on this computer. i had the same exact probem. another thing (least of my troubles) i cant click on the flash videos in firefix such as youtube. i can load them but they are just as unclickable as my left bar <

thats pretty much all i know, and anyone needs extra info i probably wont be sleeping ;D so plz post.

---

### Post by motoclaw on 2012-07-06
still nothing.i have tried:
-new flash plugin
-new user
-new install

please people, just toss ideas at me.

---

### Post by motoclaw on 2012-07-06
workspace switcher wont switch at all only does top left window. cant even click on the top left workspace either i have to actually press enter.

---

### Post by sdowney717 on 2012-07-06
try running with a different desktop called gnome-shell
from a terminal window type in 
> sudo apt-get install gnome-shell
If you have to then install it from a recovery terminal window (boot into recovery mode) since your mouse clicking is not working well.

Then log out and on the ubuntu round  symbol next to your sign in name, click it and select the new desktop gnome not ubuntu.
then log in with your name and password.
See if that makes a difference.

---

### Post by krustenBrot on 2012-07-06
a) Have you tried using Unity 2D?

To switch from standard Unity to Unity 2D **log out **click on the little ubuntu symbol right next to your Username and select **Unity 2D** from the drop down menu. Then log in as usual.

b) Does it happen when you are running or doing a particular task?

---

### Post by krustenBrot on 2012-07-06
> **sdowney717 said:**
> try running with a different desktop called gnome-shell
from a terminal window type in 

If you have to then install it from a recovery terminal window (boot into recovery mode) since your mouse clicking is not working well.

Then log out and on the gnome round foot symbol next to your sign in name password, click it and select the new desktop.
then log in with your name and password.
See if that makes a difference.


I would first suggest using Unity 2D do determine if its compiz or something graphic card related before installing a completely new desktop environment - i reckon this can be quite irritating for a new user.

---

### Post by motoclaw on 2012-07-06
> **krustenBrot said:**
> 
b) Does it happen when you are running or doing a particular task?
  its hard to tell because most of the time i always have firefox up to check on this thread. i do know for sure is that it affects every program. it isnt just a select few. most of the time i can use the arrowkeys in said program but i cant click. or i can click and i cant click elsewhere.

but in the meantime im trying the above method with gnome ^

---

### Post by motoclaw on 2012-07-06
trying unity 2d as we speak ill be a min or two

---

### Post by motoclaw on 2012-07-06
so far unity 2d works flawlessly. even as im typing i can move my mouse over the left buttons and they all react normally. the little ubuntu button drop down thing next to my name only had unity and unity 2d isnt there supposed to be unity 3d? if not then i have no clue i assumed it would be there because i always see unity associated with ''3d''

---

### Post by krustenBrot on 2012-07-06
Another thought: try using Chromium, and/or monitor the memory usage (*Dash or windows key -> System monitor*) while testing. As far as i know Firefox was/is memory intensive, maybe that is causing the unity freeze.
However, that's just an idea ;)

---

### Post by krustenBrot on 2012-07-06
Unity = equivalent of Unity 3D
[I](edit: Unity without 2D is at least using compiz and graphic acceleration to enable the effects ) 
[/I]

What graphics card & driver are you using?

---

### Post by motoclaw on 2012-07-06
true. i have 8gb of ram along with 3gb of video ram. 1tb harddrive that literally only has ubuntu on it. idk if it was memory, but it could have been. im pretty sure it was unity related because changing it to 2d completely fixed it.

---

### Post by motoclaw on 2012-07-06
gtx 580 and i went into the system settings and updated a graphics driver ''post release update'' thats all i did with drivers. ill check and see if it asks me to update any more

---

### Post by motoclaw on 2012-07-06
AHHH i see there was something wrong with the driver. had the newest version i just need to re-install. afterwards ill try to launch unity3d and see if its any better. ill keep posted brb

---

### Post by krustenBrot on 2012-07-06
The Firefox thing was just an idea based on problems i had before. Just think of an obviously simply issue like a [Fork Bomb.]("https://en.wikipedia.org/wiki/Fork_bomb") My conclusion was a bug in Firefox spamming until the memory is full nevertheless how much memory there is. 

Good luck with the driver!
[]("https://en.wikipedia.org/wiki/Fork_bomb")

---

### Post by motoclaw on 2012-07-06
in the additional drivers page there are 2 choices of drivers:
 nvidia (version current) [recommended]
nvidia (post release updates) (version curent-updates)

by clicking activate driver on one i disable the other.. odd. ill try both and see what works

---

