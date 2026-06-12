---
title: "Folder icons won't change..."
date: 2011-07-17
forum: General Help
---

### Post by Timbothecat on 2011-07-17
Hi Guys.
I'm using Ubuntu Studio 10.10 and I was installing some programs the other night. After I had finished installing the programs, the folder icons (and their respective windows) changed to this god-awful beige colour. I'm using the "UbuntuStudio" theme which has these nice glossy blue folders by default, but they've changed as I said to this ugly colour that, quite frankly, sickens me. 
I've gone into the *Appearance Preferences* and tried to work it out there, but no matter what I do, the folders never change.
If any of you know how I can fix this, I'd appreciate your help.
Have a good one,
Tim.

---

### Post by CatKiller on 2011-07-17
> **Timbothecat said:**
> If any of you know how I can fix this, I'd appreciate your help.

*gnome-settings-daemon* has crashed. Logging out and logging back in again should restart it.

---

### Post by Timbothecat on 2011-07-17
Thanks Catkiller, I'll give that a shot.

---

### Post by Timbothecat on 2011-07-17
Worked a treat mate. The really sad thing is that I had the IT Crowd going through my head last night as I was stressing over it... "Hello, welcome to IT. Have you tried turning it off and on again?"

---

### Post by CatKiller on 2011-07-18
> **Timbothecat said:**
> "Have you tried turning it off and on again?"

Quite. You wouldn't need to for most things, you'd just restart which ever program it was. In this case, running gnome-settings-daemon makes every other themed element come back except for the folders - I'm pretty sure because of some weirdness of the interaction between g-s-d and Nautilus.

Glad it worked for you.

---

