---
title: "I can's see desktop icons and Nautilus option &quot;show desktop&quot; is not writable?"
date: 2010-05-25
forum: General Help
---

### Post by ZequeZ on 2010-05-25
Well, as described in the title, I can't see the desktop icons, and the "show desktop" option under "gconf-editor >apps>nautilus>preferences" says it's not writable... What? oO

I tried deleting the nautilus configuration folder, and the gnome configuration folder... Nothing happens =(

---

### Post by mgol on 2010-05-25
> **ZequeZ said:**
> Well, as described in the title, I can't see the desktop icons, and the "show desktop" option under "gconf-editor >apps>nautilus>preferences" says it's not writable... What? oO

I tried deleting the nautilus configuration folder, and the gnome configuration folder... Nothing happens =(

Do You even have nautilus process started? Check it:
```
ps -e | grep nautilus
```
If not (and if rebooting doesn't help) You can add nautilus manually to Startup Applications in System -> Preferences.

I had to do sth like that myself as my nautilus process also chose not to run automatically at some point... The same happened with Compiz, I had to add "compiz --replace" to Startup Apps...

---

### Post by lookitseman on 2010-05-25
> **ZequeZ said:**
> Well, as described in the title, I can't see the desktop icons, and the "show desktop" option under "gconf-editor >apps>nautilus>preferences" says it's not writable... What? oO

I tried deleting the nautilus configuration folder, and the gnome configuration folder... Nothing happens =(


To add to what was said before me, I occasionally lose my desktop icons for no apparent reason, and it's because the nautilus process was killed somehow.  If that's what happened...

Press ALT+F2, and run nautilus that way.

---

### Post by ZequeZ on 2010-05-25
> **mgol said:**
> Do You even have nautilus process started? Check it:
```
ps -e | grep nautilus
```If not (and if rebooting doesn't help) You can add nautilus manually to Startup Applications" in System -> Preferences.

I had to do sth like that myself as my nautilus process also chose not to run automatically at some point... The same happened with Compiz, I had to add "compiz --replace" to Startup Apps...

Yes, I have it, but I don't think I'm understanding, when I run Nautilus by the command line, it opens a new window in my home directory... So, how do I start Nautilus to show the desktop? oO

(Anyway, when I close all the Nautilus windows, the process is still running)

---

### Post by mgol on 2010-05-25
> **ZequeZ said:**
> Yes, I have it, but I don't think I'm understanding, when I run Nautilus by the command line, it opens a new window in my home directory... So, how do I start Nautilus to show the desktop? oO

It doesn't matter. It displays home directory, but at the same time it shows desktop contents if they were not present. But that would be it if You really had nautilus process killed.

> **ZequeZ said:**
> 

(Anyway, when I close all the Nautilus windows, the process is still running)

Hmm... So maybe try restarting it? In a console:
```
killall nautilus; killall -9 nautilus
ps -e | grep nautilus
```
If nautilus is really killed now, press Alt+F2 and write just:
```
nautilus
```

BTW, did You try rebooting? Is it reproducible?

---

### Post by ZequeZ on 2010-05-25
> **mgol said:**
> It doesn't matter. It displays home directory, but at the same time it shows desktop contents if they were not present. But that would be it if You really had nautilus process killed.



Hmm... So maybe try restarting it? In a console:
```
killall nautilus; killall -9 nautilus
ps -e | grep nautilus
```If nautilus is really killed now, press Alt+F2 and write just:
```
nautilus
```BTW, did You try rebooting? Is it reproducible?


Yes, this has been like this since a couple of weeks, I really didn't pay too much attention, I mean, is not critical :P.

I tried killing the process with, and without sudo, and then, when I restarted nautilus it trowed only 2 things to the console:

```
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension
```

Any clue? =/

---

### Post by ZequeZ on 2010-05-25
I SOLVED IT!!! ^^
I logged out, then I logged in console mode (Alt+Ctrl+F5), then I used the gconftool to change the value =D.

```

gconftool --type bool --set /apps/nautilus/preferences/show_desktop true
```

[COLOR=#000000]I hope to be useful  to someone ^^[/COLOR]

---

