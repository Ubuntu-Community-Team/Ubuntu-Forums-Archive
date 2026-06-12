---
title: "Gnome-do fails to autostart, enters in text mode?"
date: 2009-08-23
forum: General Help
---

### Post by maxclimber1w on 2009-08-23
Hi,

I have two problems with Gnome-do, which is a great app and makes life easier!

First, sometimes Gnome-do fails to autostart... I guess this is about 2/3rds of the time. I have an entry in startup programs and also the checkbox in Gnome-do prefs in checked.

Second, when Gnome-do is running and I press the hotkeys, it reads them as raw text and does not bring up the associated commands. This happens about 1/2 the time.

Any ideas? I really would appreciate some help!

---

### Post by maxclimber1w on 2009-08-24
Help me!

---

### Post by tmurph on 2009-08-25
I'm also having some trouble with this, mainly the latter issue. Gonna give this a bump, any helpers out there?

---

### Post by maxclimber1w on 2009-08-28
I was able to help the raw text issue by changing the hotkey to something else.

The other problem is persistent, however. Any ideas?

---

### Post by mhpathfinder on 2009-11-13
Gnome do starts up okay in Ubuntu Netbook Remix on Acer Aspire One D250-1026 netbook, alas in RAW TEXT mode.  I changed the hot key, but it continues to start in Raw Text mode.  Oddly enough, when I close Gnome Do, then reopen it, it is in application search mode.  But, when I restart ubuntu 9.10 Gnome Do opens at startup in...RAW TEXT mode.  Definitely a bug that many are experiencing.  Still looking for fix.  I'll stay tuned and try a few other settings, like maybe changing the app search mode hotkey?

---

### Post by mhpathfinder on 2009-11-13
This fix worked.  I unchecked "Start Gnome Do at Login" under the General Tab on Preferences.   I then went to System, Preference, Startup Applications and added Gnome Do from /user/bin/gnome do.  I restarted the system and Gnome do opened up in app search mode.

I hope this helps others.

Amen.
MH

---

### Post by Captain_Glen on 2009-11-19
I think you mean:

```
/usr/bin/gnome-do
```

But even with the correct spelling and a reboot, this still does not work for me. :(

---

