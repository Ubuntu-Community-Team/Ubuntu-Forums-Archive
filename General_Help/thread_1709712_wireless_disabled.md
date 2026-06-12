---
title: "wireless disabled"
date: 2011-03-18
forum: General Help
---

### Post by Slymon95 on 2011-03-18
My brother pressed the wireless button on my laptop that usually toggles the wireless on/off on windows, but on ubuntu, it flashes blue and orange (im guessing if its sending recieving data). Anyways, after he pressed it it turned blue and nw when i click the networking icon on the top right, for wireless networks, it is greyed out and says wireless is disabled. Wired internet still works however.

Please help, i have a. Compaq Presario CQ50-100CA running Ubuntu 10.10.

---

### Post by mikewhatever on 2011-03-18
How about pressing that button again? ;)

---

### Post by Slymon95 on 2011-03-18
> **mikewhatever said:**
> How about pressing that button again? ;)

I wish it was that simple :), no nothing happens when i press it, it stays blue

---

### Post by grahammechanical on 2011-03-18
How about pressing the button with your brother's head!

Have you right clicked the icon and made sure that there are tick marks against the two lines Enable Networking and Enable Wireless? Clicking these lines will act like a switch that will switch the wireless adapter off and on. That might be all you need to do.

There is a command that will also work. sudo ifconfig wlan0 up

If this works, tell your brother to make a donation to charity.

Regards.

---

### Post by Slymon95 on 2011-03-24
> **grahammechanical said:**
> How about pressing the button with your brother's head!

Have you right clicked the icon and made sure that there are tick marks against the two lines Enable Networking and Enable Wireless? Clicking these lines will act like a switch that will switch the wireless adapter off and on. That might be all you need to do.

There is a command that will also work. sudo ifconfig wlan0 up

If this works, tell your brother to make a donation to charity.

Regards.
Sure will ;p

And when i right click the icon, enable networking is checked. But enable wireless is greyed out dark and unclickable, but after pressing the button again, it becomes clickable and i checked it, under wireleess netowkrs it says wireless not ready. Also, when i use that command into terminal it says operation not possible du to rf-kill.

---

### Post by bkratz on 2011-03-24
> **Slymon95 said:**
> Sure will ;p

And when i right click the icon, enable networking is checked. But enable wireless is greyed out dark and unclickable, but after pressing the button again, it becomes clickable and i checked it, under wireleess netowkrs it says wireless not ready. Also, when i use that command into terminal it says operation not possible du to rf-kill.

Probably worth trying

```
sudo rfkill unblock all

```

may work

---

### Post by Slymon95 on 2011-03-24
Thanks for you help everyone! Right after using the rfkill code then the wlan0 up code, i pressed the internet button on mylaptop twice then wireless netowrks appeared! UBUNTU FTW!!!!!!!!!

---

### Post by bkratz on 2011-03-24
does 
rfkill list
show it as hard or soft blocked?

---

### Post by bkratz on 2011-03-24
Didn't update the screen fast enough! But congratulations!!

---

