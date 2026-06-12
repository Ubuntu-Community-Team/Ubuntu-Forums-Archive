---
title: "Screensaver Locks Up Machine"
date: 2009-11-19
forum: General Help
---

### Post by zdunham on 2009-11-19
Hi all.

I just installed Xubuntu 9.10 on another machine, a rather old machine, and I went to change the screen saver and clicked on the Ant Spotlight one and the machine locked up. Now anytime I try to go back in and change it, the machine freezes since it is already on that screen saver. Anytime it goes to sleep now it freezes as well. I've looked all over for an answer to this problem, even on these forums, and the only solution I found was to use gconf-editor, although they were older posts. gconf-editor was not installed by default so I installed it and tried to follow directions given in these threads that I found but there was no applications section in gconf-editor.

Does anyone know a way to change the screen saver through command line? I just want to change it back to the blank screen one. Thanks a lot for any help.

---

### Post by Aubergines on 2009-11-19
gconf-editor is the gnome config editor so I doubt that would work with xfce. Other than that I'm not much use, I don't have xubuntu installed. But the screensaver settings would be held in some config file somewhere in you home dir.

---

### Post by zdunham on 2009-11-19
> **Aubergines said:**
> gconf-editor is the gnome config editor so I doubt that would work with xfce. Other than that I'm not much use, I don't have xubuntu installed. But the screensaver settings would be held in some config file somewhere in you home dir.

Sometimes I amaze myself with how stupid I can be. Obviously gconf-editor means gnome config editor and I didn't even realize it when I was doing it. I'll see if there is some way for Xfce and post back if I find one.

If anyone knows how to change the screen saver from command line in Xfce4, or in some way that doesn't involve opening the settings from the Applications menu because it will freeze, please help, thanks a lot.

---

### Post by zdunham on 2009-11-19
It would also help to know what program Xfce4 in Xubuntu uses for screensavers by default. I was going to reinstall xscreensaver but when I do that it says it is not installed yet. That also goes for gnome-screensaver. Does anyone know that either? Maybe I am just missing something.

---

### Post by Aubergines on 2009-11-19
No, actually I was wrong. I grabbed the iso. Xubuntu actually uses the gnome screensaver so gconf-editor does work. Type:

```
gconf-editor /apps/gnome-screensaver
```

In it there's an entry called "themes" and beside the entry is "[screensavers-antspotlight]". Double click that, "edit" the key and delete the entry. Click Ok. The entry beside "themes" should now say "[]".

---

### Post by zdunham on 2009-11-19
> **Aubergines said:**
> No, actually I was wrong. I grabbed the iso. Xubuntu actually uses the gnome screensaver so gconf-editor does work. Type:

```
gconf-editor /apps/gnome-screensaver
```

In it there's an entry called "themes" and beside the entry is "[screensavers-antspotlight]". Double click that, "edit" the key and delete the entry. Click Ok. The entry beside "themes" should now say "[]".

OK, gconf-editor was not installed by default so I installed it. I ran the command you showed and I get a LOAD of errors; all of them some kind of "GConf Error: Failed to contact configuration server;" and some stuff after that.

---

### Post by zdunham on 2009-11-19
Well I got it to work. I was already logged in as the super user but after I put sudo in front of it, everything worked. I didn't think I would need sudo if I was already logged in as root but it made the difference. Thanks for the help.

---

### Post by zdunham on 2009-11-19
Now the weird thing is, even though my screensaver is clearly ant-spotlight, there is nothing next to themes to begin with, just the empty brackets. When I double click it everything is grayed out except for "Add".


On my netbook, which is the other machine I have Xubuntu 9.10 on, I have ant-spotlight as my screensaver and it doesn't freeze the machine. I have a keyboard shortcut set up to turn the screensaver on and lock the machine, the command that runs is /usr/bin/xflock4, if I just let my computer sit and idle, the screen saver never comes on at all. I made sure the power manager is set to ten minutes to turn the screen off and the screensaver is set to 5 minutes idle before it comes on. It just never comes on after five minutes and never locks the screen unless I hit the keyboard shortcut. Something is weird about how the screensaver works on this Xubuntu.

---

### Post by Bigneil on 2009-11-19
i used to have issues on my old computer with the screensavers locking up the machine,  after the sceensaver had been running for a few minutes the screen would go black and not come back unless i switched my box off and on again. The problem was my crappy old graphics card, i just set the screen saver to blank screen until i bought a new card.

---

### Post by zdunham on 2009-11-19
> **Bigneil said:**
> i used to have issues on my old computer with the screensavers locking up the machine,  after the sceensaver had been running for a few minutes the screen would go black and not come back unless i switched my box off and on again. The problem was my crappy old graphics card, i just set the screen saver to blank screen until i bought a new card.

This is essentially what is happening to me except that it freezes even when I go to the screensaver settings. Since it is currently set to ant-spotlight, that automatically loads up in the demo screen and instantly freezes the computer before I can change it back to blank or anything else.

---

### Post by Bigneil on 2009-11-20
> **zdunham said:**
> This is essentially what is happening to me except that it freezes even when I go to the screensaver settings. Since it is currently set to ant-spotlight, that automatically loads up in the demo screen and instantly freezes the computer before I can change it back to blank or anything else.

oh dear, there must be some way of disabling the screen saver or changing it using the terminal...much googling may be required.

---

### Post by Bigneil on 2009-11-20
yes, i have been googling and found a few threads n stuff. it seems to be possible to do it from the terminal, but there was different methods for different versions of ubuntu/xubuntu etc . Perhaps a more experienced ubuntu member can talk you through the correct method for you particular system.

---

