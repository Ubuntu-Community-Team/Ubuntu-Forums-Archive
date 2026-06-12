---
title: "metacity has gone"
date: 2010-06-01
forum: General Help
---

### Post by kolo-01 on 2010-06-01
hi,

the top bar of all of my windows is gone, which i think is due to metacity no longer starting up, im pretty sure it should be in the system moniter but its not, i can teporarily get it going by restoring it in the terminal, but that only lasts as long as the terminal is open, can anyone tell me how to permanantly restore it to run normally, help much appreciated

---

### Post by fooman on 2010-06-01
press the alt + f2 keys

type the following into the space and click "run":

```
metacity --replace
```

to keep it like that,  turn off the visual effects....go to system > preferences > appearance > visual effects ~set to none.

---

### Post by kolo-01 on 2010-06-01
> **fooman said:**
> press the alt + f2 keys

type the following into the space and click "run":

```
metacity --replace
```

to keep it like that,  turn off the visual effects....go to system > preferences > appearance > visual effects ~set to none.


Thanks a lot for the reply, your solution worked, but I am trying to find a way which would allow me to keep my visual effects on, as my docking program doesnt work well with it off, is there any way of going back to having both at the same time?

---

### Post by fragos on 2010-06-01
Compiz runs on top of Metacity so you should try the above without turning visual effects off. Just as a mater of note Metacity has some nice effects which you can turn on. I particularly like the shadow effect which makes windows seem to pop off the screen. I don't bother with Compiz any more. Most of the Compiz effects are IMO more theatrical than useful.

---

### Post by kolo-01 on 2010-06-02
> **fragos said:**
> Compiz runs on top of Metacity so you should try the above without turning visual effects off. Just as a mater of note Metacity has some nice effects which you can turn on. I particularly like the shadow effect which makes windows seem to pop off the screen. I don't bother with Compiz any more. Most of the Compiz effects are IMO more theatrical than useful.


hi george thanks for the reply, but when i switch on compiz effects, the bar disappears, bit of a nightmare and im not sure what ubuntu wants me to do to get both of them working at the same time normally? or am i getting this all wrong and not understanding that metacity is an alternative to compiz? all i really want is the top bar of the windows back, but thanks for the reply

---

### Post by fragos on 2010-06-02
I may be mistaken but I believe that metacity is layer below compiz. Metacity gives you a desktop and compiz adds features on top of that. They both run at the same time. Metacity does have some compositing features but even those can be enabled and run compiz on top. If you menu disapears when you enable compiz, that is where the issue is. You may find your answer using the Configuration Manager /apps/compiz but there are a huge number of parameters under those. You can control Metacity compositing with a single parameter /apps/metacity/general/compositing_manager.

---

### Post by kolo-01 on 2010-06-03
hi fragos

i have managed to fix the problem by going into compiz and editing the comand bar under window dressing, but thank you for your input.

i was just wondering about your first post in the thread where you said about metacity having some nice effects and that you have got rid of compiz, if you like could you tell me how you have replaced- might not be the right word, compiz with metacity, and how do you get metacity to perform the functions of compiz?

thanks

---

### Post by fragos on 2010-06-03
Use the Configuration Manager to enable Metacity compositing with a single parameter /apps/metacity/general/compositing_manager. Special effects are turned off to disable Compiz. What I like about Metacity compositing is the shadow effect around windows that makes them visually stand out. It also provides visual confirmation when starting aps from the applet bar. There are no spinning cubes and wobbly windows theatrics. Less CPU is used and on a laptop less battery is used.

---

### Post by TheDesertDragon on 2010-06-03
I was firmly under the impression that compiz replaced Metacity rather than building on top of it, but using the metacity configurations?

In any case, turning on visual effects is as easy as typing "compiz" in a terminal. Typing "metacity --replace" and then "compiz" will of course work also.

As for why it isn't running on startup (so you have to type it) well... once you get it started up, look in the configuration on the menus in the upper left corner by default. There should be a setting called "Startup applications"
Try putting metacity and compiz in that. Should fix it.

---

