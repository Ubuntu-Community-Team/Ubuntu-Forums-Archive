---
title: "Ubuntu wont shut down"
date: 2010-03-11
forum: General Help
---

### Post by Bloemetjesgordijn on 2010-03-11
Hi,

My current setup KUbuntu 9.10 and wont shut down (Shut Down button in the menu). As soon as I hit the button, the menu closes and nothing happens.

The only way is to shut down is in terminal: sudo shutdown now. Even then only the graphical layer stops, I get a command prompt.

Any advise?

thx.
Bloemetjesgordijn

---

### Post by garvinrick4 on 2010-03-11
try sudo shutdown -h now

---

### Post by Bloemetjesgordijn on 2010-03-11
> **garvinrick4 said:**
> try sudo shutdown -h now

Thx

but i would like to shut down via the UI and not via command prompt

---

### Post by Bloemetjesgordijn on 2010-03-11
Found the solution.

It seemed that also I had no audio when playing mp3 with Dragon Player and Amarok.

Removing "catalog.cache" in .xine folder solved the MP3 issue and I also could shut down via the GUI.

It doesnt seem related but worked for me

---

