---
title: "Power Management: Custom time for display shutdown"
date: 2012-02-29
forum: General Help
---

### Post by tylersontag on 2012-02-29
Hey all,

I have an Ubuntu media center and i've been having problems with people leaving it idle.  For obvious reason i have the display set to always on and no screen saver, but enough occurances of people leaving the TV on overnight are starting to show on the TV (screen-burn-in)

So i want to set the screen to shut off after a certain time, but the longest interval is an hour in 11.04.  The average movie is 1.5-2 hourse so i was wanting to set it up somewhere around there.

Any idea where the config file is that stores this information and if i can manually edit it?

---

### Post by Krytarik on 2012-02-29
You can run a command like this, or use GConf-Editor, to set that setting to a custom value; but notice that if you set any value not offered by the Power Management GUI, it won't show anything :P :
```
gconftool-2 --set --type int /apps/gnome-power-manager/timeout/sleep_display_ac SECONDS
```Regards.

---

### Post by raja.genupula on 2012-03-01
Look at this 
[http://blog.sudobits.com/2011/07/13/automatic-shutdown-in-ubuntu/](http://blog.sudobits.com/2011/07/13/automatic-shutdown-in-ubuntu/)

EDIT: this too
[http://www.addictivetips.com/ubuntu-linux-tips/set-automatic-system-shutdown-in-ubuntu-with-easyshutdown/](http://www.addictivetips.com/ubuntu-linux-tips/set-automatic-system-shutdown-in-ubuntu-with-easyshutdown/)

---

### Post by tylersontag on 2012-03-01
thanks for the tip about gconf-editor, i think that should work!

I had seen some of those pages about utilizing the shutdown command, but i didn't actually want to shut down my media center... its also my primary server and runs alot of other toys (IRC chat server, Subsonic media server, torrents, print spooler, etc) Plus it houses a RAID array thats a pain to bring up or down.

But the 2 hour timeout on the display should have my Sharp some pixels :-D

---

