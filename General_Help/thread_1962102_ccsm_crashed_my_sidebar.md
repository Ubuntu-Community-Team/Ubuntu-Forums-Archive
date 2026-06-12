---
title: "ccsm crashed my sidebar"
date: 2012-04-20
forum: General Help
---

### Post by Gamemaker7 on 2012-04-20
[SIZE=3]I read that deleting the .gconf & rebooting would fix it, but will it delete any data? I also read that typing into the Terminal '**unity --reset-icons**' would also fix it, but I don't want to accidentally delete any data...[/SIZE]

---

### Post by dino99 on 2012-04-20
.gconf is where the "settings" are stored, so if you delete it, on next reboot ( or log out/in ) it will be cleanly recreated but with the default ubuntu settings, meaning that your custom settings are lost, then you need to set back your preferences. But "data" are not removed, only "settings".

first into a terminal, try : compiz --reset or compiz --replace , then log out/in

---

### Post by Gremlinzzz on 2012-04-20
you can open .gconf maybe pick and choose what too delete:popcorn:
would help you choose but i'm useing Xubuntu

---

### Post by Gamemaker7 on 2012-04-20
> **dino99 said:**
> .gconf is where the "settings" are stored, so if you delete it, on next reboot ( or log out/in ) it will be cleanly recreated but with the default ubuntu settings, meaning that your custom settings are lost, then you need to set back your preferences. But "data" are not removed, only "settings".

first into a terminal, try : compiz --reset or compiz --replace , then log out/in
Thank you, I don't believe I have any important settings saved

---

### Post by Mark Phelps on 2012-04-21
Don't know if the details in the link will work -- but they did for me when I messed with ccsm and my stuff disappeared:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html")

---

