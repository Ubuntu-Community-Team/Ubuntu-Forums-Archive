---
title: "Ubuntu 12.04 Routing keys with xmodmap help"
date: 2012-06-13
forum: General Help
---

### Post by CoNinja on 2012-06-13
I have a couple of questions. I am trying to map keys via xmodmap. I created .xmodmaprc in my home folder and upon restart, nothing changes. The only thing written in it is "keycode 180 = w" when I press key 180 firefox sends me to home page versus typing a w. I'm new and wondering what I am doing wrong.

Second question is, my numpad is built in with other keys IE: Home, Pg Up, Pg Dn, etc. Then when numlock is pressed the numbers should work. They retain the original keys instead is there a way to route the keys post numlock press? The only current answer I have come up with is setting it in xmodmap(if I get it to work) as a shift press key and I would have to hold shift down and press them :S

---

### Post by CoNinja on 2012-06-13
Ok, I figured out the first problem. I thought xmodmap would automatically call on .xmotmaprc on startup/login. I had to manually load it through terminal, but will find a way to automate this with startup in a few. 

My question still stands on how to make the Num lock key alternate functions of the numpad.

---

