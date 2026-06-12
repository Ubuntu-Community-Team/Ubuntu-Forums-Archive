---
title: "Shutting down in 60 seconds... why?!!!"
date: 2009-10-30
forum: General Help
---

### Post by whitefort on 2009-10-30
Hi.  Since switching to Karmic, I've found that I can no longer right-click the shutdown button to access preferences and turn off that annoying 'shutting down in 60 seconds' delay.  (WHY would anyone want this??)

Anyway, a visit to the indicator-applet site shows that this isn't a bug but a deliberate dumbing down of the app (to simplify use), and that the devs have no intention of fixing it.

So, my question...  Is there anything I can do to change Karmic so that when I click shutdown, the machine just shuts down without the silly delay or a second click?  It was so easy in Jaunty, but seems to be impossible in Karmic.

Thanks!
(and seriously, apologies to anyone who likes and uses/needs the 60 second delay - but it drives me crazy!)

---

### Post by prem1er on 2009-10-30
+1 I noticed this also. It is very annoying.

---

### Post by John Bean on 2009-10-30
I don't have a running Karmic to test but it's possible the setting is still there but not made visible to the user. On Jaunty the setting is accessible with gconftool-2:```
gconftool-2 --type boolean -s /apps/panel/applets/fast_user_switch_screen0/prefs/suppress_logout_restart_shutdown true 
```Despite the name this only suppresses the prompt and delay and is set/reset by the option on the right-click. Perhaps it will still work in Karmic if used from the terminal.

---

### Post by xjb2003x on 2009-10-30
This is highly annoying.  I did find a way around it.  I installed the cairo-dock.  On the dock, there is a quitter applet.  If you shutdown from there, you will not get that annoyance.

---

### Post by todak on 2009-10-30
In a terminal: ```
gconf-editor
``` Go to **apps**> **indicator-session** and check the box next to **suppress_logout_restart_shutdown**. Or if you wish to do it entirely from terminal: ```
gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

---

### Post by DeMus on 2009-10-30
> **whitefort said:**
> Hi.  Since switching to Karmic, I've found that I can no longer right-click the shutdown button to access preferences and turn off that annoying 'shutting down in 60 seconds' delay.  (WHY would anyone want this??)

Anyway, a visit to the indicator-applet site shows that this isn't a bug but a deliberate dumbing down of the app (to simplify use), and that the devs have no intention of fixing it.

So, my question...  Is there anything I can do to change Karmic so that when I click shutdown, the machine just shuts down without the silly delay or a second click?  It was so easy in Jaunty, but seems to be impossible in Karmic.

Thanks!
(and seriously, apologies to anyone who likes and uses/needs the 60 second delay - but it drives me crazy!)

Type
```
alt+f2
```
In the window that opens then type:
```
gconf-editor
```
Choose in the left column
```
apps, indicator-session 
```
In the right column tick the box which says:
```
suppress-logout-restart-shutdown
```

---

### Post by John Bean on 2009-10-30
> **todak said:**
> In a terminal: ```
[code]gconftool-2 -s '/apps/indicator-session/suppress_logout_restart_shutdown' --type bool true
```

Ah, it's still there but in a different place :-)

---

### Post by whitefort on 2009-10-30
Yep!  It's all fixed!

Thanks a million, guys!  I REALLY appreciate this.

---

### Post by yesint on 2009-11-01
> **whitefort said:**
> 
Anyway, a visit to the indicator-applet site shows that this isn't a bug but a deliberate dumbing down of the app (to simplify use), and that the devs have no intention of fixing it.


This is more than dumb! I don't understand this general trend in Gnome to make everything stupid and to remove any remaining flexibility. The KDE is, imho, overloaded with unnecessary customization, but Gnome is going to lack ANY customization! This is silly and very sad in longer perspective...

---

### Post by Cool Surfer on 2009-11-01
Thanks, worked great for me.

---

### Post by Marti68 on 2009-11-04
> **whitefort said:**
> Yep!  It's all fixed!

Thanks a million, guys!  I REALLY appreciate this.
WOT HE SAID ;)

Thank you and appreciate the lack of CLI

---

### Post by asbesto on 2009-11-30
Worked for me also, on 9.10

This is really a stupid thing. This is UNIX, not Vista.

](*,)

---

