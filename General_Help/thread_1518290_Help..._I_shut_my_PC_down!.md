---
title: "Help... I shut my PC down!"
date: 2010-06-26
forum: General Help
---

### Post by oxf on 2010-06-26
Uhm whats going on?
When I click on shout down it takes me to the "are you sure you want to....." as usual. Then when I click "OK"
it takes me to user account log in and my only option is log back in again. There is the Shut down icon in the lower right panel but that doesnt do any thing either. So I keep coming back to the desktop.

I suppose I could crash it but would prefer to sort out properly

Any suggestions?

---

### Post by Dysport on 2010-06-26
Try entering "sudo shutdown -h now" in a terminal

---

### Post by Rubi1200 on 2010-06-26
You could also try and restart the X session, then shut the computer down as you tried before.

```
sudo /etc/init.d/gdm restart
```

---

### Post by Serpher on 2010-06-26
The direct way to turn off your computer is:

```
sudo init 0
```

or to restart

```
sudo init 6
```

---

### Post by Dysport on 2010-06-26
> **Serpher said:**
> The direct way to turn off your computer is:

```
sudo init 0
```

or to restart

```
sudo init 6
```

or more direct: press the power button … or even more direct: pull the plug :P

---

### Post by oxf on 2010-06-26
> **Dysport said:**
> or more direct: press the power button … or even more direct: pull the plug :P
Thanks all.   Sudo shutdown  worked fine. I dont know why this happened but seems fine now. I could have killed the power but didn't want to cause other problems. I had some strange file and other stuff once when everything froze on me and pulled the plug which sent fsck into a panic!

---

### Post by Dysport on 2010-06-26
> **oxf said:**
> Sudo shutdown  worked fine.

sudo shutdown or sudo reboot is usually the way to go. if these don't work you've got other problems :) cheers!

---

### Post by oxf on 2010-06-26
> **Dysport said:**
> sudo shutdown or sudo reboot is usually the way to go. if these don't work you've got other problems :) cheers!

Yep seems fine now
Thanks..

---

### Post by jimestesphl on 2010-06-26
I had the same problem: this fixed it for me.  [http://ubuntuforums.org/showthread.php?t=1462838](http://ubuntuforums.org/showthread.php?t=1462838)

---

