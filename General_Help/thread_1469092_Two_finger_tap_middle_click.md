---
title: "Two finger tap middle click"
date: 2010-05-01
forum: General Help
---

### Post by Newto-rah on 2010-05-01
Hi, I'm newish to the forum, but have been using ubuntu for the past few months.

I recently upgraded from eeebuntu (a 9.04 derivative) to 10.04, and found that two finger tapping my touchpad has gone from middle click to right click, (and 3 fingers is now middle instead of right).

From what I've seen, this has been changed since 9.10, but I haven't been able to find a permanent solution yet. Most fixes have been from before and use hal, or other things that don't exist anymore. The one thing I've found does work is using xinput and the command 
```
xinput set-prop "ETPS/2 Elantech Touchpad" "Synaptics Tap Action" 2, 3, 0, 0, 1, 2, 3
```But that has to be run every time I start up, and it occasionally reverts while I'm using the computer. I've tried making a script that runs at startup, but neither adding it to the list of startup programs, or autostart folder has worked, but running the script file manually does work.

I'm a bit at wits end with this, it's the only issue I've had with 10.04, and I've spent many many hours trying to get it to work (I've also tried gsynaptics and the newer version whose name escapes me right now). Hopefully there's a permanent fix out there.

---

### Post by Newto-rah on 2010-05-02
Just as an update of more stuff I've tried, I've put that command and also "synclient TapButton2=2 TapButton3=3" into rc.local and xinitrc, but neither has happened at startup

---

### Post by shoegoo on 2010-05-02
I need to know how to change this as well.  I think I had the same issue when I upgraded to 9.10, but the fixes I have found did not work this time.

---

### Post by Newto-rah on 2010-05-02
I actually just found a solution that seems permanent. I installed this ppa and changed the appropriate values (as instructed) [https://launchpad.net/~yurivkhan/+archive/ppa]("https://launchpad.net/%7Eyurivkhan/+archive/ppa"). Took me a while to figure out how to use a ppa though :P, also the first 2 times the key failed to download, but it worked after trying repeatedly.

---

### Post by itix on 2010-05-03
Adding a PPA is not hard, just run [COLOR="Navy"]sudo add-apt-repository ppa:yurivkhan/ppa[/COLOR] to add the PPA above.

Thanx for the tip BTW. I'm checking it out

---

### Post by itix on 2010-05-04
I can confirm that it works.

If it does'nt work for you, run [COLOR="DarkSlateBlue"]sudo apt-get update && sudo apt-get upgrade[/COLOR] before starting gconf-editor.

---

### Post by jojohippo on 2010-05-13
I've got the same problem. I couldn't get the synclient fix to run automatically at start up. I've added the ppa and run update/upgrade but nothing is upgraded. When I try to install gnome-settings-daemon it says it's already the newest version. I don't see the mouse options in gconf-editor

---

