---
title: "Sound levels very loud"
date: 2011-04-10
forum: General Help
---

### Post by grayfox444 on 2011-04-10
I'm trying to figure out if I can make my sound level changes less dramatic. If I use the volume controls on my keyboard to increase/decrease the volume by one level the changes are enormous. 
I have to keep it like 1-2 clicks above 0, so the bar is maybe 5% full. Is there any way I can change a setting to make this less dramatic? 
It's just kind of a pain when I something is too loud/quiet and it takes a lot of work to get the levels right because each small change makes a huge difference.

---

### Post by Enigmapond on 2011-04-10
Right-click on the volume icon and go to properties. You can adjust anything in here.

---

### Post by DeMus on 2011-04-11
I think what the OP means is that pressing one time on the volume-up or down button on the keyboard gives a huge change in volume. I experience the same.
In just 16 steps I have reached maximum volume, starting from zero. I also wish I would have to use more steps, meaning pressing more often, so the steps are smaller.
This is not something you can change in the volume properties, this must be something fixed by design.

---

### Post by grayfox444 on 2011-04-11
> **DeMus said:**
> I think what the OP means is that pressing one time on the volume-up or down button on the keyboard gives a huge change in volume. I experience the same.
In just 16 steps I have reached maximum volume, starting from zero. I also wish I would have to use more steps, meaning pressing more often, so the steps are smaller.
This is not something you can change in the volume properties, this must be something fixed by design.

yes this is exactly what i mean.

---

### Post by Thewhistlingwind on 2011-04-11
The volume key on your keyboard is implemented as a shortcut. If you want to change the level of sound it modifies, the correct course of action would be to write a bash script that will change it in a more "reasonable" amount per press. Add it to the bash command line as a command, then implement it as a custom keyboard shortcut for both the volume up and down keys.

Of course, I don't know the script to write that will do that, but I'm confident that this is the solution.

---

