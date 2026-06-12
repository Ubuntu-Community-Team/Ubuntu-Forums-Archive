---
title: "Accidentally toggled Click to Move... i think?"
date: 2010-05-06
forum: General Help
---

### Post by ig88s57chevy on 2010-05-06
I did something stupid and i don't know what i did or how to fix it...  

For some reason every time i click within the contents (not the title bar) of a window (for example; firefox, transmission, nautilus, terminal, basically any running application) and drag the mouse while holding the left mouse button down the entire window moves instead of the expected behavior (selecting text in firefox, moving a file in nautilus, selecting a torrent in transmission, clicking checkbox in system preferences, etc).  

This is the expected behavior you would get from clicking on the title bar but not the contents of the window.

Right before this happened, i had installed Xephyr and Sugar emulator (for XO OLPC).  In the title bar of the Sugar emulator it said to push "ctrl + shift" in order to grab/release the mouse - I had issues getting the mouse successfully grabbed and released - this is around the time all of the problems started.  

I have since removed Sugar and Xephyr yet this problem remains.

It appears that i have somehow toggled a setting to make moving windows the default behavior when clicking....

Any ideas of what i did to cause this to happen and what i can do to fix it?  I don't want to have to reinstall.

p.s. its not a stuck key - i have rebooted multiple times and the problem remains passed reboots.

p.p.s at the login screen the behavior is not present, you must hold ALT while clicking on the login window in order to exhibit the behavior.  However. once Gnome is loaded you no longer need to hold ALT to window the move, it just defaults to that behavior.

Thanks in advance and sorry for being such a noob!

---

### Post by WorMzy on 2010-05-06
Open gconf-editor and browse to /apps/compiz/plugins/move/allscreens/options/initiate_button, what is the value of that key? It should be '<Alt>Button1' (no quotes).

---

### Post by ig88s57chevy on 2010-05-06
> **WorMzy said:**
> Open gconf-editor and browse to /apps/compiz/plugins/move/allscreens/options/initiate_button, what is the value of that key? It should be '<Alt>Button1' (no quotes).
Thanks for the suggestion; i will check that as soon as i get back home.

---

### Post by ig88s57chevy on 2010-05-06
> **WorMzy said:**
> Open gconf-editor and browse to /apps/compiz/plugins/move/allscreens/options/initiate_button, what is the value of that key? It should be '<Alt>Button1' (no quotes).
Hi WorMzy,

I checked that setting and it is still set to '<Alt>Button1' (no quotes)... 

[[IMG]http://s1.postimage.org/abuRA.jpg[/IMG]]("http://www.postimage.org/image.php?v=gxabuRA")

whats strange though is that even though that is the setting in gconf-editor, holding alt and left-click-dragging is what i am doing right now as a workaround to select text or position my mouse in firefox (meaning this setting is obviously not working for me).

Thanks for the suggestion though. 

Is there anything else that could cause this behavior?

---

### Post by ig88s57chevy on 2010-05-06
I did a search in gconf-editor for Button1 and the only item listed without a modifier is: "/apps/compiz/plugins/expo/allscreens/options/dnd_button" which appears to be the key used to move windows when in expo mode.  

I verified that i could move windows with this key while in expo mode then changed it to <Alt>Button1 and confirmed the setting changed in Expo mode; however this behavior i am experiencing (in regular mode?) still persists.

Everything else in gconf-editor that references Button1 has a modifier key.

Is there any other explanation as to why Button1 would act as the "move window" initiate_button without the need of using the <Alt> modifier even though the setting in gconf-editor says to use the <alt> modifier?

Again, this is not a stuck key; it persists through reboots, and simple shortcuts like <Alt>F4 only work when i am actually holding <Alt>...

---

### Post by ig88s57chevy on 2010-05-06
Update:

This only affects the current user (me) in the current window manager (gnome).

If i switch window managers to KDE, IceWM, or FluxBox the normal behavior of Button1 returns.

If i create a new user and log into gnome the normal behavior of Button1 returns.

However, i dont want to switch window managers (i like gnome) and i also dont want to migrate my settings and data to a new user account (that just seems drastic for this problem; almost as drastic as reinstalling the OS).

---

### Post by WorMzy on 2010-05-06
What happens if you open ccsm and disable the "Move Window" plugin?

---

### Post by ig88s57chevy on 2010-05-06
> **WorMzy said:**
> What happens if you open ccsm and disable the "Move Window" plugin?
WorMzy you rock!  you made me look inside of ccsm, which did not match the settings found within gconf-editor...

[[img]http://s3.postimage.org/BgCzA.jpg[/img]](http://www.postimage.org/image.php?v=PqBgCzA)

As you can see in the pic above, ccsm showed the initiate-button as Button1 while gconf-editor showed it as <Alt>Button1 (bug?)

upon changing it within ccsm to <Alt>Button1 everything is back to normal.

Thank you so much!

---

### Post by WorMzy on 2010-05-06
o.O

That's pretty weird. You might want to check other plugins too, just in case.

I've seen one other case where gconf didn't match up to what settings were, but that involved gnome-panel.

In any case, I'm glad you got it sorted. :)

---

### Post by WorMzy on 2010-05-06
Doublepost

---

