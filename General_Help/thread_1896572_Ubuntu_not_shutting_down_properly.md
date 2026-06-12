---
title: "Ubuntu not shutting down properly"
date: 2011-12-17
forum: General Help
---

### Post by tears of the river on 2011-12-17
I dont know why but ever since i installed ubuntu about a month ago sometimes it does not shut down properly it just shuts the cpu but the main power supply is not shut. and my dad has really been screaming at me coz of that.

What happens exactly is that i shut it down and the top and bottom panels both dissapear after a few seconds of shutting. but conky remains there then the wallpaper starts to get weirdly pixellated so im not sure whats the problem

there does not seem to be any particular pattern to this it seems to be random

Could someone please give me a solution.

---

### Post by 2F4U on 2011-12-17
You don't provide much information to work with. What are the hardware specs? What does the log file say?

---

### Post by dino99 on 2011-12-17
seems your config have been tweaked a little: try without conky enabled on startup

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it before it ended itself)

---

### Post by tears of the river on 2011-12-17
> **2F4U said:**
> You don't provide much information to work with. What are the hardware specs? What does the log file say?

well i have ubuntu 10.04 and im not really sure what a log file is :confused:

my hardware specs are p4 2.4 ghz processor and 512 mb ram
no graphics card

---

### Post by tears of the river on 2011-12-17
> **dino99 said:**
> seems your config have been tweaked a little: try without conky enabled on startup

sudo dpkg-reconfigure -phigh -a
(can take a while, dont stop it before it ended itself)

i dont stop it 
i let it end itself
and this has been happening ever since i installed ubuntu so i dont really think the configuration has been tweaked and it was happening before i had conky

---

