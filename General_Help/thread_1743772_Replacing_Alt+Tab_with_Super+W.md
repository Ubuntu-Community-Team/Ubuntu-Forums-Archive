---
title: "Replacing Alt+Tab with Super+W"
date: 2011-04-29
forum: General Help
---

### Post by l8a on 2011-04-29
Hi.

How can I change the standard behaviour of alt+tab to that of super+w ?

I do not find a setting for it withing the "key binder" @system settings.

Anybody know how do it?

Sincerally, l8a

[11.04]

---

### Post by bhatbhai on 2011-04-29
Go to Applications and search for "Keyboard shortcuts."

---

### Post by mc4man on 2011-04-29
In natty super+w is the scale plugin > window picker for all windows
Alt+Tab is in static application switcher

---

### Post by l8a on 2011-04-30
Hi.

Thank you for your answers.

I dont find the super+w combination in the keyboard shortcuts, only the alt+tab.

I'm new to it, so help is welcome.

Cheers l8a

---

### Post by John Crichton on 2011-05-02
Hey OP,

I just figured out how to do this myself, so heres how its done.

Install "CompizConfig Settings Manager"

Once that is done, open 'System Settings' and click on CompizConfig Settings Manager.

When that opens, scroll down to Window Management and uncheck 'Static Application Switcher' and then click on Scale.

The Window should change, click the Bindings tab.

The first 2 list items will both be 'Initiate Window Picker', click on the box to the right of the second one, it should say none or disabled or something.

In the window that pops up, click 'Grab Key Combination', when the thing pops up, press Alt-Tab, then click OK.

And you're done, it will work straight away if you followed the instructions properly.

Please tell me if it worked for you (or if it didn't).

Using CompizConfig Settings Manager can sometimes make your current session a bit buggy, press alt-f2 and then enter compiz --replace to fix the problems.

---

