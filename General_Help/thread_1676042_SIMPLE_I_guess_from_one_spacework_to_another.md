---
title: "SIMPLE I guess: from one spacework to another"
date: 2011-01-26
forum: General Help
---

### Post by &gt;hankim&lt; on 2011-01-26
Hello, 
I'm getting addicted to this ubuntu and loving it! :D But it's got to many secrets for a craftsman like me...
Anyway, does anybody know how the hell do I get my windows to swift from one spacework to another? I mean by just by dragging it to the end of the screen and not manually by 'move to that spacework' and so. It used to happen before but not anymore :s
thx

---

### Post by wojox on 2011-01-26
I think it's Windows Key + A

---

### Post by Vaphell on 2011-01-26
i assume you use compiz effects?
make sure you have compizconfig-settings-manager package installed
run compiz config (should be somewhere in menu or **ccsm** in terminal)

depending on which toy is used to switch workspaces (cube rotate, wall), dig into the preferences of that toy and look for options responsible for flipping, they should be on the last tab
there are 3: cursor, move, drag-and-drop - select move

sorry i am not too precise, but i have no idea how these things are named in english.
also, may i point you to the Expo plugin? [win]+[e] shows all workspaces at once and you can drag and drop there.

---

### Post by &gt;hankim&lt; on 2011-01-26
ohh, wonderfull, that's just it! thank you so much, and I like you call it toy! xD

---

### Post by Vaphell on 2011-01-26
edit: glad it worked :)

---

### Post by mc4man on 2011-01-26
You can drag a window from one workspace to another with either the wall plugin (edge flipping - edge flip  move) or rotate plugin
I can't stand wall nor expo - rotate works well for me (and also has unfold  - Ctrl+Alt+arrow down - arrow left or right and scroll on desktop

---

### Post by &gt;hankim&lt; on 2011-01-26
Edit: Done it! one last thing, can you set a determinate workspace to be predeterminated? I mean for example say, that you have a 3x3 square wall, and you want the middle square to be the workspace nº1 and the one it comes to you first when you initiate ubuntu, is it possible? or just crazy? hahaha no... seriously xD

---

### Post by Vaphell on 2011-01-26
not that it is guaranteed to work:
- go to the compiz config and in desktop switcher set a trigger for viewport #5 (i assume #5 is the central one in 3x3 grid), it should be some obscure combination of keys unlikely conflict with anything, let's say WIN+5
- install xdotool
- test your magic combination with xdotool, e.g. xdotool Super+5
- in the autostart programs create an entry for **xdotool Super+5**, if it doesn't work for some reason (too early and system is not ready yet?) try adding sleep <seconds>, e.g. **sh -c 'sleep 10 && xdotool Super+5'**

i actually tested emitting key combinations but didn't play with the startup apps so you got to do it yourself.

---

