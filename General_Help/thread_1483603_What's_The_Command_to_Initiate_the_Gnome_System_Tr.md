---
title: "What's The Command to Initiate the Gnome System Tray for When It Fails to Load?"
date: 2010-05-14
forum: General Help
---

### Post by OzzyFrank on 2010-05-14
I tried Googling this, but couldn't find any mention of what the command is for the System Tray, so thought I'd ask here. Note I am not asking how to put a system tray on the panel - I know I can add a notification area, but when I reboot there will be 2 of them, so this is not what I want.

I just need to be able to initialise it when it fails to load. Since my upgrade to Lucid, this has happened a couple of times, so expect it will happen again soon enough.

Many thanks in advance.

---

### Post by warfacegod on 2010-05-14
I don't know the command you are referring to, however

```
sudo restart gdm
```

will restart your gnome desktop manager. This will be faster than rebooting.

---

### Post by kerry_s on 2010-05-14
you just reload the gnome-panel, check "gnome-panel --help" see if there's a --reload or --restart switch
other wise:
killall gnome-panel
gnome-panel

---

### Post by OzzyFrank on 2010-05-14
Ah, so you reckon just force the whole panel to restart? Makes sense. Still, there must be a command for the system tray itself...

---

### Post by kerry_s on 2010-05-14
> **OzzyFrank said:**
> Ah, so you reckon just force the whole panel to restart? Makes sense. Still, there must be a command for the system tray itself...

the system tray is a applet, loaded by the panel, applets are not command based, there modules, i think just like a file with a set of settings.
anyways reloading the panel should be just as fast.
does gnome-panel have a switch?

for example, i'm using xfce4-panel, i just "xfce4-panel -r" & it's done.

---

### Post by OzzyFrank on 2010-05-14
**[COLOR="DarkRed"]gnome-panel --replace[/COLOR]** ("Replace a currently running panel"). I just tested it and it reloads both panels. **_[COLOR="Red"]EXCEPT[/COLOR]_**... close the terminal and both panels disappear. And I just realised the ***Run Application*** dialogue must be tied in with the panel somehow (I guess it's an *applet*), as when the panels are gone Alt+F2 does nothing. Luckily I had a terminal launcher of the desktop to reinitiate the panel.

I should have used Alt+F2 to begin with I suppose, as the ***Run Application*** box closes with the panels when I exit the terminal.

---

### Post by kerry_s on 2010-05-14
> **OzzyFrank said:**
> **[COLOR="DarkRed"]gnome-panel --replace[/COLOR]** ("Replace a currently running panel"). I just tested it and it reloads both panels. **_[COLOR="Red"]EXCEPT[/COLOR]_**... close the terminal and both panels disappear. And I just realised the ***Run Application*** dialogue must be tied in with the panel somehow (I guess it's an *applet*), as when the panels are gone Alt+F2 does nothing. Luckily I had a terminal launcher of the desktop to reinitiate the panel.

I should have used Alt+F2 to begin with I suppose, as the ***Run Application*** box closes with the panels when I exit the terminal.


maybe just create a launcher to run that command, like on the desktop or the panel itself?

i haven't seen any other posts about that problem, maybe it's something your loading in the system tray crashing the whole tray?

---

### Post by OzzyFrank on 2010-05-14
> **kerry_s said:**
> maybe it's something your loading in the system tray crashing the whole tray?

Well, I haven't added anything since upgrading to 10.04, and this has started since then. Ergo...

Anyway, it's intermittent, and at least is easily fixed.

---

### Post by OzzyFrank on 2010-05-15
Too early to tell, but it might not be so intermittent now, since I rebooted and the system tray never loaded. But this time I got no error message box like the times before - just no system tray. As I said, never touced it or installed a new app that uses it - only thing I did was upgrade Ubuntu.

No big deal... I have found these things often disappear with future updates (Ubuntu so rocks in comparison to Windows in that regard!). For now just a quick **Alt+F2** and **killall gnome-panel** and all is fine again. I'm a glass-half-full kinda guy, hehe.

---

