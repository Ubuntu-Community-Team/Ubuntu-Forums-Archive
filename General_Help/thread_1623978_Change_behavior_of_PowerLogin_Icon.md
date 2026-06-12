---
title: "Change behavior of Power/Login Icon?"
date: 2010-11-17
forum: General Help
---

### Post by Splat_NJ on 2010-11-17
Hello folks. I've been running Ubuntu 10.10 for four days now and love  it. Is there a way to change the default behavior of the power/logoff  icon on the taskbar?(not on Ubuntu now and forget what the bar is  called) Instead of asking me what I want to do (power down,restart, log  off, etc) I would like it to power down the PC. Is this possible and  how? Thank you.

---

### Post by Frogs Hair on 2010-11-17
System > Preferences > Screen Saver > Power Management tab . There is an option to spin down disks when ever possible , but this will not change the options in your session indicator on the Gnome panel . You also find your sleep settings there also. I'm not sure what you mean by power down , but both of these settings reduce power use.

---

### Post by azertyh on 2010-11-17
hello,
found this for 10.04 [http://ubuntuforums.org/showthread.php?t=1496550](http://ubuntuforums.org/showthread.php?t=1496550)

---

### Post by Splat_NJ on 2010-11-17
Thank you Azertyh and Frogs Hair for replying. Azertyh, I will try what you referenced, which is to open a run dialogue window, (press Alt + F2 keys) and type 
gconf-editor, then navigate the Configuration editor to apps >  indicator-session and place a check against  "suppress_logout_restart_shutdown."  I'm converting my XP desktop to Ubuntu 10.10 right now so I'll try it when that's done. Thanks.

---

### Post by Splat_NJ on 2010-11-17
> **Frogs Hair said:**
> System > Preferences > Screen Saver > Power Management tab . There is an option to spin down disks when ever possible , but this will not change the options in your session indicator on the Gnome panel . You also find your sleep settings there also. I'm not sure what you mean by power down , but both of these settings reduce power use.

I meant to power down, shutdown, turn off the PC. I'm going to try Azertyh's suggestion and see how that goes.

---

### Post by Splat_NJ on 2010-11-23
Finally got around to trying the suggestion in the given thread but it doesn't change anything. I still get the options to shut down, logout, restart, etc., when I click the "shut down the computer" icon.

---

### Post by Frogs Hair on 2010-11-23
It seems both the session applet and shutdown applet both offer choices and do not directly shutdown , and the software center offers no choices . You could look into adding a custom launcher by right clicking the desktop and selecting add launcher. I'm sure someone here can help you with the command. Once created you can drag it to the panel.

---

### Post by Splat_NJ on 2010-11-23
Good point, Frog's Hair.  I'm still new to Linux/Ubuntu and I forget how configurable it is! Care of [this]("http://ubuntuforums.org/showthread.php?t=1624021") thread I managed to create a launcher with command "shutdown -P 0" and it does the trick. Sweet Mother of all that's Holy I love Linux! :grin:

---

