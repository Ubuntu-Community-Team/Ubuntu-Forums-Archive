---
title: "Regaining the GUI"
date: 2012-08-10
forum: General Help
---

### Post by Ubun2to on 2012-08-10
When my computer locks up, and I can get to the CLI from CTRL + ALT + F2 usually.
So, is there a way to relaunch Unity from the command line? I tried to do it via this command, which I've used before when Unity completely locked up:
```
unity restart
```
But, it says the display is set to 0 or something like that, and it won't launch.
So, is there a way to restart the GUI from the command line? Or should I just restart the computer every time I have to get to there? (Which isn't too annoying when you have a SSD-really fast boot times.)

---

### Post by Moif_Murphy on 2012-08-10
What happens if you type 'init 5'?

---

### Post by Cheesemill on 2012-08-10
You can always do:
```
sudo service lightdm restart
```

---

### Post by Ubun2to on 2012-08-10
> **Cheesemill said:**
> You can always do:
```
sudo service lightdm restart
```

Thanks! I hate having to reboot when the system locks up.

---

