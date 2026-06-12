---
title: "lost all top panels on desktop"
date: 2011-12-19
forum: General Help
---

### Post by kwalters on 2011-12-19
I am on Ubuntu 10.10 on a dual core AMD processor.  I use both Chrome and Firefox as my web browsers.

Something happened the other day whereby I lost my top menu when using Firefox.  Thus I had no access to Applications, Places or System and none of the usual icons were at the right hand edge of that top panel.

That made it difficult to shut down; to the extent that I had to turn the power off to do so.  When I restarted, and went to Chrome as my browser, everything was back to normal; but another visit to Firefox left me with no top panel again.

Somhow, whilst fiddling with panel settings, i have managed to lose ALL the top panels. That means I cannot get a terminal window to do the manual reset of panel default settings.

Help!!

---

### Post by dino99 on 2011-12-19
open a terminal: ctrl+F2, then run: 

gnome-panel --replace &

and you will get the config back

---

### Post by kwalters on 2011-12-19
Thanks for that.  Unfortunately, pressing Ctrl and F2 did not give me a terminal

However, I got one by rebooting into recovery mode and using the last option.
 
But when I entered your suggested text  I just got an error message and something about "could not open display"

I then tried some lines I had noted down earlier about how to get back to default display.

I entered:

gconftool -2 --shutdown (but that gave an error saying it did not recognise the -2.  Tried -Z in case of a transcription error, but no joy.

just entering gconftool --shutdown did not give an error message

so I went on with the other lines:

rm -rf .gconf/apps/panel
pkill gnome-panel

I dont think I got any error messages; but the desktop remained bare when I started up again.

I also tried 

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

but I still have a totally bare desktop; just the background colour

Any further suggestions?

thanks

KW

---

### Post by LinuxFan999 on 2011-12-19
Try pressing Ctrl-Alt-F2 next time you need to get into the terminal. When you are in the terminal, try typing in this:
```
sudo apt-get update
sudo apt-get install gnome-panel
```

---

### Post by kwalters on 2011-12-21
Eureka!!  Solved.  But not without a moderately long saga

Ctrl_Alt-F2 still would not give me a terminal, so I went the recovery mode route again.

When I got to apt-get install gnome-panel, it informed be that the latest version was already there so it was not going to change anything.  My desktop remained bare of panels when I restarted.

However, after this restart, and for no apparent reason, Ctrl-Alt-F2 DID give me a terminal AND asked me to log in with username and password (had not happened on the previous attempts via recovery mode.)

I then went straight to my earlier "all purpose panel reset" script and typed:

sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity

After the next reboot my panel was back and Ubuntu became usable again

I am extremely grateful for your help.  I was on the verge of updating to version 11 as the only option left to me.  And I could do without trying to work out how to do that with no panel showing!!

Thanks again

KW

---

