---
title: "Can't run shutdown-dialog with cron?"
date: 2009-10-07
forum: General Help
---

### Post by floborg on 2009-10-07
So, I setup up the following script to run using gnome-schedule:

```
#!/bin/sh

cd /home/****/Music/DM

icecream --name dm%Y%m%d --stop 310min http://wrif.com/wriflive.pls

gnome-session-save --shutdown-dialog
```

The icecream command clearly ran since the MP3 file was generated, but the machine never shutdown, and there was no sign of the shutdown-dialog.  When the script is run manually, rather than through cron, the shutdown-dialog opens up.  Why didn't this work with cron?  Thanks.

---

### Post by wojox on 2009-10-08
Try:

```
shutdown -h 0
```

---

### Post by alphaniner on 2009-10-08
If I'm not mistaken, you have to add some extra information if you want cron to interact with the GUI at all.  And wojox's suggestion won't work because shutdown requires you to be root, so you'd have to use sudo, so you would be promoted for a password.

The best suggestion I can come up with is to add the script to root's crontab, and use **shutdown -h** rather than **gnome-session-save --shutdown-dialog**

---

### Post by floborg on 2009-10-08
I guess the normal user can't run this command either:

```
gconftool -s -t int /apps/gnome-power-manager/timeout/sleep_computer_ac 1500
```

I added that to my script, and the setting didn't get changed.  Now, I noticed that my icecream recording didn't go for the full 320 minutes, so maybe the script halted.  The machine, though, was up and running when I returned to it.

---

