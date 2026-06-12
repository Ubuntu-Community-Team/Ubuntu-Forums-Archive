---
title: "Minecraft in Ubuntu?"
date: 2011-07-26
forum: General Help
---

### Post by QuantumMonkey on 2011-07-26
Aha I've been posing a lot in this forum, but I'm such a noob at using Linux :P

I installed Java a few hours ago, and I've finally gotten minecraft to run. Is it normal for it to lag A LOT, i literally get about 3 fps average. I'm not an avid gamer, just Minecraft is a game that I play a little when I'm bored or have some free time at work/college. 

I'm not really good with my computer specs, but I do know that it has:

An Intel Pentium processor T4400
An ATI Mobility Radeon HD(it's a laptop)
4gb of ram and I think it's 2.2GHz.

I only installed Ubuntu yesterday, so do I need to download anything special for my computer like driver updates or anything?
If Ubuntu simply isn't made for gaming, that's fine, as I said, I don't play games at all except minecraft :P

---

### Post by dino99 on 2011-07-26
[http://timashley.me/node/596](http://timashley.me/node/596)

---

### Post by QuantumMonkey on 2011-07-26
> **dino99 said:**
> [http://timashley.me/node/596](http://timashley.me/node/596)

I have got Minecraft, I just don't know whether it's meant to lag as bad as it does :s :P

---

### Post by dino99 on 2011-07-26
then look at graphic driver: activation, errors into log (/var/log/) & .xsession-errors (ctrl+h to unhide it into /home)

---

### Post by QuantumMonkey on 2011-07-26
> **dino99 said:**
> then look at graphic driver: activation, errors into log (/var/log/) & .xsession-errors (ctrl+h to unhide it into /home)

Sorry, I sound like such a noob, but I have no idea what any of that means :P

---

### Post by Theredbaron1834 on 2011-07-26
First off, yeah, it should run fast on your system. I have an old Eeepc with a 900mhz cpu, and intel vid that they don't even have win7 drivers for it is so old, but I can run it "OK" on it.

I am not sure really, but to resay what dino said in an easier to read way:
So, start the game and then exit. After that click system, admin, Log File Viewer, and check for errors.
Also check places, Home Folder. Once it loads up press ctrl and H to unhide all files. Then open up the files  .xsession-errors.

It should help you out, I think.

Also since you just installed, you might not be using the best drivers for you vid card. So you could check out system, admin, Additional Drivers, and install what is there. They won't be open, like the built in ones, but they will do better 3d most likely, although ATI is better then nvidia with it's open-source drivers I do believe.

Also, I had trouble with OpenJava, so what version are you using? The only way I could get it running well was with Sun Java.

---

### Post by SlugSlug on 2011-07-26
it should run fine, check drivers in settings menu make sure its activated & maybe version of java matters?

if you get it running here's a multiplayer server i host to get you going ;)

itpro.co.cc and forum on [www.itpro.co.cc](www.itpro.co.cc)

---

### Post by QuantumMonkey on 2011-07-26
Thanks a heap to everyone, I guess I'll try this tomorrow since it's 1:30am here, Ubuntus keeping me up :D I did install the sun java thing from the terminal, it was the first thing I ever did in the terminal but yeah, I figured it out :P and I'm guessing that most 'old' users of ubuntu like the previous layout thing, since you said to go to 'system' so I'll make sure to start up in classic or whatever it's called :P :)

---

### Post by Theredbaron1834 on 2011-07-26
O, right, yeah, sorry, I HATE unity. In unity just type the last the program's name in the unity search bar thingy.

And I am not really an "old" user, I only used it for the past 2 years or soo. Honestly, I think I would like kde better, then the old gnome interface, but my lappy is slow as sin, and gnome 2 is my fav of the things I can run well.

---

### Post by QuantumMonkey on 2011-07-27
Thanks so much! I just finished installing the proprietary drivers and it works perfectly!:) :) :)

---

### Post by Theredbaron1834 on 2011-07-27
Cool, glad it is working. Minecraft really is a cool game. There are even some opensource lookalikes being made. :)

---

