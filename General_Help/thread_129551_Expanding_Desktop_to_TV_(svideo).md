---
title: "Expanding Desktop to TV (svideo)"
date: 2006-02-14
forum: General Help
---

### Post by kenetik on 2006-02-14
I have S-Video out, how would I go about expanding my desktop to the TV? Thanks..

---

### Post by nanotube on 2006-02-14
try this:
[https://wiki.ubuntu.com/NvidiaTVOut](https://wiki.ubuntu.com/NvidiaTVOut)

---

### Post by kenetik on 2006-02-14
What if its not nVidia? got no idea if it is or not, and that says to do it simultaniosuly.. i want it so i can like use it as a 2nd desktop, so like drag the mouse from the laptop lcd to the monitor, (2x the realestate)

---

### Post by nanotube on 2006-02-14
to check what hardware you have, go to System>Administration>Device manager and look what you have for your video card.
also, if you read further down, you will see that it gives you a second screen, not just a copy of your first screen - so seems to do what you want. (but i have not done that myself, so cant say for sure).

---

### Post by kenetik on 2006-02-14
Ok so I changed those settings, how do I configure to turn it on.off?

---

### Post by nanotube on 2006-02-14
well, just plug your svideo cable to your tv, and restart X. (to restart X, just log out, and then hit ctrl-alt-backspace)
if that doest work, try rebooting. if rebooting doesnt work either... well then i guess you are out of luck, at least until someone else who knows more about making svideo tvout work comes along. :)
btw, what is your video card, anyway?

---

### Post by kenetik on 2006-02-14
Its on a laptop, its some sort of intel onboard video.. ;) And no it didnt work.. Bummer

---

### Post by nanotube on 2006-02-14
hey
does it say which intel onboard video?
because there is a package in synaptic called i855-crt that, according to its description, "i855-crt is a small utility to enable or disable the TV Out function of
many i855-based laptops."
so if its an i855 based card, maybe that will work for you.

---

### Post by kenetik on 2006-02-14
Yah says 82852/855GM

---

### Post by nanotube on 2006-02-14
well then... restore your xorg.conf to previous state (before you fiddled around with all that stuff from the nvidia howto - you did make a backup, right? :) )
and then install that package, and play with it.

---

### Post by kenetik on 2006-02-14
I dont see it in synaptic, i did a search for i855 and got nothing

---

### Post by nanotube on 2006-02-14
strange, it should be in the default repositories... try hitting reload in synaptic to refresh your package info, and then search for it again.
if that still fails... well, you could always try from the commandline:
```
sudo apt-get install i855-crt
```

---

### Post by kenetik on 2006-02-14
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package i855-crt

```

---

### Post by nanotube on 2006-02-14
are you running ubuntu breezy?
do you have the right sources.list file?
(see this link for reference: [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Ubuntu_Repositories_and_sources.list) )

---

### Post by featherking on 2007-02-20
I wrote up an actual 'How To' for this and it is posted [[COLOR="Red"]here[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=361124"). The howto was written for the 945 chipset (based on what you posted earlier you are running the 855) but most intel chipsets all use the same driver (i810) so you could give it a shot, it will probably work due to the same driver being used, it explains svideo and also how to have a dual monitor setup

---

