---
title: "Ubuntu desktop effects"
date: 2010-10-03
forum: General Help
---

### Post by Noorani on 2010-10-03
Hi there,
I just started having a problem with my ubuntu jaunty desktop effects. I don't remember what I was doing exactly, I think I was changing the wallpaper and at the same time doing something else when all of a sudden the monitor flickered and I no longer had the advanced desktop effects with compiz. They had been working perfectly before and now all of a sudden I cannot use them.
When I click on 'Extra' in the 'Visual Efects' I get the message 'Could not enable desktop effects'. I've tried 'compiz --replace' in the terminal and the windoww  borders go away. I don't know what could be the cause of this problem. please help because I really like those effects.
Thanks in advance!

---

### Post by nlsthzn on 2010-10-03
> **Noorani said:**
> Hi there,
I just started having a problem with my ubuntu jaunty desktop effects. I don't remember what I was doing exactly, I think I was changing the wallpaper and at the same time doing something else when all of a sudden the monitor flickered and I no longer had the advanced desktop effects with compiz. They had been working perfectly before and now all of a sudden I cannot use them.
When I click on 'Extra' in the 'Visual Efects' I get the message 'Could not enable desktop effects'. I've tried 'compiz --replace' in the terminal and the windoww  borders go away. I don't know what could be the cause of this problem. please help because I really like those effects.
Thanks in advance!

What graphics card do you use? Does it need restricted drivers?  Maybe check "System -> Administration -> Hardware Drivers" and re-apply your graphics drivers if applicable.

---

### Post by utnubuuser on 2010-10-03
doing something else?

---

### Post by andrewthomas on 2010-10-03
Jaunty is just about EOL.  I would upgrade

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Noorani on 2010-10-03
yeah i checked hardware drivers. i was told no propietry divers are in use in this system

---

### Post by nlsthzn on 2010-10-04
> **Noorani said:**
> yeah i checked hardware drivers. i was told no propietry divers are in use in this system

Do you need proprietary drivers?  (Are you using a nvidia or AMD/ATI graphics card etc?)

---

### Post by Noorani on 2010-10-04
I dont know the graphics card that i have. How do I check

---

### Post by andrewthomas on 2010-10-04
```
lspci |grep VGA
```

---

