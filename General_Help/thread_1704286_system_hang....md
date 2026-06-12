---
title: "system hang..."
date: 2011-03-10
forum: General Help
---

### Post by Sina_RJ on 2011-03-10
when i move mouse even on top panel or on dock ( dock application ) my system hangs,and i have no choice but shut down with pulling out my laptop battery!
what should i do???
I'm using ubuntu 10.10

---

### Post by Diametric on 2011-03-10
Could you reply with your laptop specs?  Let us know what you have so we can help Identify the issue.

Good luck.

---

### Post by Sina_RJ on 2011-03-10
I have a DEll inspiron 1545
1 GB of RAM
250 GB of hard disk
2 GHZ of intel core 2 duo
and i'm using desktop edition of ubuntu
this is the first time i face hanging on linux
and i'm brand new in terminal

by the way,i have 200 GB free on hard disk

---

### Post by Sina_RJ on 2011-03-10
and all the applications i have is wine,axel,gimp,chromium,compiz and some games and plotters
I'm really confused and tired of pulling out my battery  repeatedly...
please help...

---

### Post by Sina_RJ on 2011-03-10
Isn't There anyone who can help me??
please
I'm really getting anxious about reinstalling ubuntu...
just give me some advice if you know anything,i'll try on my own risk

---

### Post by Krytarik on 2011-03-10
It may be the window manager. If you have desktop effects enabled, thus Compiz running, try replacing it with Metacity:
- press Alt+F2
- enter```

metacity --replace
```

---

### Post by Sina_RJ on 2011-03-10
thanks a million it just fixed :)

---

### Post by Sina_RJ on 2011-03-10
> **Krytarik said:**
> It may be the window manager. If you have desktop effects enabled, thus Compiz running, try replacing it with Metacity:
- press Alt+F2
- enter```

metacity --replace
```


i did and it just worked
but there is another thing happened after this :(
bottom of my desktop is black...
what i have to do?
do i have to change any setting?

---

### Post by Krytarik on 2011-03-10
> **Sina_RJ said:**
> 
bottom of my desktop is black...
what i have to do?
do i have to change any setting?
Meaning that you see the upper part of your wallpaper and a black stripe at the lower end?

Try ugrading the video driver to those provided by Ubuntu-X-Swat, maybe it also fixes the Compiz issue:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Sina_RJ on 2011-03-10
i did this but when i run docky that black part will appear again
and i don't have any effects any more... :(
i removed compiz...shouldn't i? :(

---

### Post by Sina_RJ on 2011-03-10
i did this but when i run docky that black part will appear again
and i don't have any effects any more... :(
i removed compiz...shouldn't i? :(

---

### Post by Krytarik on 2011-03-10
> **Sina_RJ said:**
> 
and i don't have any effects any more... :(
i removed compiz...shouldn't i? :(
That would explain why you don't have desktop effects anymore! LOL ;-)

I don't like Docky at all, try AWN instead:
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Sina_RJ on 2011-03-10
I hope it does work :(
and this does fix my effects?
i really can't live without them :D

i think it does,thx ;)

---

### Post by Krytarik on 2011-03-10
> **Sina_RJ said:**
> 
and this does fix my effects?

Of course you have to re-install Compiz if you removed it.

---

### Post by Sina_RJ on 2011-03-11
i know that i'm really a starter :)
but can you solve this problem to?
i reinstall it,but there are no effects,even the effect that i had before with extra effect of linux
i don't know what to do any more :(
is there any library for that?

---

### Post by Krytarik on 2011-03-11
First, did you re-enable it via "System -> Preferences -> Appearance -> Visual Effects"!?

If you get an error message that it "cannot be enabled", run *Forlong's* Compiz-Check and post its output, follow the instructions at his website:
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

---

### Post by Sina_RJ on 2011-03-11
yes i did but when click on extra effect the additional driver application starts and then screen flashes and ask me if i want to keep settings,but they aren't any effects!
now i solve the problem with the point you just said before!
i re-install the compiz...
i was wrong in doing it.... :(
thanks a lot,it just like the fresh ubuntu i got from the very first day :)

---

