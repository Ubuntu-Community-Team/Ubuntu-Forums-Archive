---
title: "No timer in the restart window"
date: 2010-05-07
forum: General Help
---

### Post by rmcellig on 2010-05-07
I may be wrong but I remember when I would go to restart my computer, a window would appear with a coundown clock starting at I think 60 seconds. I don't see this in Ubuntu 10.04. How can I get this back? Is there a setting in the Configuration editor or something similar?

---

### Post by bumanie on 2010-05-07
alt+F2 - type gconf-editor into the windows and hit enter. apps --> gnome session --> options Check the box next to logout prompt. you may have to reboot for it to take effect.

---

### Post by rmcellig on 2010-05-07
I tried that but I still don't see the countdown timer.

---

### Post by chris_p_b on 2010-05-07
Isn't this the default setting, which in 10.04 gives a box requiring a confirmation rather than the 60 seconds to abort? Is there a way to get it back to the countdown ?

---

### Post by rmcellig on 2010-05-07
Ya that's what I am wondering. How to get it so that I get the countdown display.

---

### Post by bumanie on 2010-05-07
Sorry, I thought you meant the dialogue box had disappeared. I disable mine - I don't remember what it says, just know where to go and enable/disable it.

---

### Post by WorMzy on 2010-05-07
I don't think it's possible to regain the old functionality of the restart/shutdown prompts. However, I have a solution for you. It's not elegant, but it will replicate the behaviour of the old style restart window in a terminal.

Add the following to a textfile, name it "restart.sh" and save it in your home folder:

```
#!/bin/bash
sudo echo "Countdown initiated"
count=60
while [ $count -gt 0 ]; do
  echo $count
  let count-=1
  sleep 1
done
if [ $count = 0 ]; then
  #sudo shutdown -h now 
  sudo reboot
fi
```

Then make it executable:

```
chmod +x ~/restart.sh
```

Finally, make a launcher for it: right-click on a panel and choose "Add to panel", from the list double click on "Custom Application Launcher", give it any name you want, and put in the command box:```
gnome-terminal -e /home/<YOUR USERNAME>/restart.sh
``` Change the icon to something you like.


Put a "#" before "sudo reboot", and remove the one before "sudo shutdown" to make the PC shutdown instead of restart. Change the timer to whatever suits you.

To cancel the timer, press Ctrl+C while it's running.

---

### Post by finlost on 2010-05-07
This is the setting in Karmic.  I am not sure if it is the same in Lucid.

Alt+F2 and type gconf-editor
Under Apps go to indicator-session
Uncheck suppress_logout_restart_shutdown

---

### Post by rmcellig on 2010-05-07
I checked that and it is already unchecked.

---

