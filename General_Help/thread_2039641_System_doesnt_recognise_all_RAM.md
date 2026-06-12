---
title: "System doesnt recognise all RAM"
date: 2012-08-09
forum: General Help
---

### Post by typos1 on 2012-08-09
Just installed another 1 Gb of RAM, but the total is now "3.2 Gb", not 4 Gb according to ubuntu. 

I have an Asus graphics card, so its not being used for video (although "system settings-details says the graphics are "unkown", even though Nvidia drivers are installed and my last ubuntu install on another pc recognised it as an Asus card). 

Previously 3 Gb of RAM was recognised as 2.9 Gb.

Do I have change something in the Bios ?

---

### Post by Kalanac on 2012-08-09
Are the ram chips of the same size, speed and type on your mobo?  If not, that can cause problems.  Also, does your mobo support the amount and type you've put in?

The other thing to try is a memtest to check if the ram works OK

---

### Post by typos1 on 2012-08-09
Yes, all 4 are pc3200, 400Mhz, cl3, non eec ram.

This :

[http://forum-en.msi.com/index.php?topic=146358.0](http://forum-en.msi.com/index.php?topic=146358.0)

seems to suggest its a common problem, at least on 32 bit systems, but I mm running 64 bit ubuntu.

---

### Post by Cheesemill on 2012-08-09
Run memtest and see how much memory it reports.

Can you also post the outputs of:
```
free -m
uname -a
sudo lshw -C memory
```

---

### Post by typos1 on 2012-08-09
Just went into the BIOS and changed it to allow memory remapping for 64 bit systems and now it shows 3.9 Gb !!

Spose I should have done that before I posted !

I also disabled onboard video, still have "unkown" shown for graphics though.

---

### Post by Cheesemill on 2012-08-09
> **typos1 said:**
> I also disabled onboard video, still have "unkown" shown for graphics though.

That's a known bug, I've never had it show anything but unknown on all the systems I've used, no matter what video card and drivers I've been using.

---

### Post by typos1 on 2012-08-09
Hmm, thats interesting, cos it was shown as an "Asus EN8400S" on my last pc with 12.04 on it.

In fact, I simply took the HD out of my old pc and stuck it in my new one (along with the graphics card) and it booted fine and everything still worked and it still recognised the card. (the windows partition booted but nothing worked cos it needed drivers !).

---

### Post by Cheesemill on 2012-08-09
I'm not saying that it never works, it just sometimes doesn't work (and I've always been unlucky).

---

