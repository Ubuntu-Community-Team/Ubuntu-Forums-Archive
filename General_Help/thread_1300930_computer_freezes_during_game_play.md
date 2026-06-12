---
title: "computer freezes during game play"
date: 2009-10-25
forum: General Help
---

### Post by kaboyish on 2009-10-25
hi. i recently installed a game called sauerbraten on my ubuntu system. its a 3d action game i used to play on my other linux system, sabayon. it used to work perfectly with sabayon. i'd play the game for hours without any gliches and freezes. i don't know why it keeps on freezing on ubuntu. i'm using ubuntu jaunty jackalope. any help would be appreciated

---

### Post by collinp on 2009-10-25
It's probably because your system might be overheating or you are drawing too much on your PSU. Have you tried monitoring your GPU temp while playing?

P.S. I play Sauerbraten, fun game :D.

---

### Post by kaboyish on 2009-10-25
> **Hellow said:**
> It's probably because your system might be overheating or you are drawing too much on your PSU. Have you tried monitoring your GPU temp while playing?

P.S. I play Sauerbraten, fun game :D.

thanks for the quick reply. i've been playing so many games on this computer, i highly doubt that its overheating. and besides, i played it well on sabayon for some time and i never had this issue. but just in case the computer is overheating, what temperature is critical?

btw, sauerbraten is a cool game. the makers should also make more games like that

---

### Post by collinp on 2009-10-25
Well, once it gets above 60C artifacting and random lockups can occur.

---

### Post by manoriax on 2009-10-25
Have you tried for example another CPU-stressing application and did the computer freeze then, too?

---

### Post by P4man on 2009-10-25
as mentioned above, it would help if you can determine if its only in sauerbrauten, or if in other games aswell and more importantly, does it happen randomly while **not** playing any games.

Also check your logfiles at the time of freezing, they might give a clue.

As for potential hardware problems, overheating could be an issue, but not likely at 60 degrees. Most cpu's work fine at 70-80 degree (though such high temps may reduce their life expectancy) and gpu's typically can handle 90 degrees celcius. 

If you cant monitor temps easily try opening your case and point a big desk fan it, see if it helps (assuming its a desktop). Running a ram test is a good idea too.

---

### Post by kaboyish on 2009-10-25
thanks guys. i read some threads and i got the solution. i switched off my screen saver, and i've been playing ever since. 
but the main question is, why should i (and others like me) be inconvenienced by switching the screen saver off? this is a major bug that needs to be reported. wish i new how to report though:P

p.s, the ubuntu community really helps. this is an utopia for newbies like me

---

### Post by P4man on 2009-10-25
Good job finding that solution yourself. Now that you mention it, I recall. I believe it is due to the game monopolizing the mouse and keyboard, and therefore, gnome doesnt see any mouse or keyboard input and therefore decides you are idle. I guess you could still call it a bug, but not an easy one to fix.

---

### Post by kaboyish on 2009-10-25
> **P4man said:**
> Good job finding that solution yourself. Now that you mention it, I recall. I believe it is due to the game monopolizing the mouse and keyboard, and therefore, gnome doesnt see any mouse or keyboard input and therefore decides you are idle. I guess you could still call it a bug, but not an easy one to fix.

by the way, i think that this problem only arises in gnome cause i was using sabayon 4.0 kde version, and it didn't have any issues. i think i might install the new kde desktop on my ubuntu and see how that works out. thanks

---

### Post by P4man on 2009-10-25
Possibly KDE has a more intelligent algorithm to determine if you're idle or not (checking cpu load? detecting a 3d app?), or maybe you didnt have a 3d screensaver set :)

BTW, here is bug report on the issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/30378](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/30378)

It also has a (crude) workaround by changing the launcher so it inhibits the screensaver before starting the game.

---

