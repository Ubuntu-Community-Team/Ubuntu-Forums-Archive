---
title: "cursor icon keeps changing"
date: 2011-11-03
forum: General Help
---

### Post by Disabled20240622 on 2011-11-03
I changed my desktop theme a couple of times yesterday, returning to the original. Now my cursor icon is flipping between a dark and light theme depending on what it is hovering over.

The desktop and window frames have the light theme, firefox has the dark one, eclipse has both seemingly randomly.

Anyone know what causes this?


Ubuntu 11.10, using shell.

---

### Post by Disabled20240622 on 2011-11-03
Got it.

The problem is that when you select a window manager theme in Ubuntu's appearance dialog it sets the cursor theme to the same string name, even if there is no such cursor icon theme.

The fix is to use the advanced settings "extension" in shell to force the cursor icon theme back to "DMZ-white", or set it in gconf editor: desktop -> gnome -> peripherals -> mouse -> cursor_theme.

---

### Post by Disabled20240622 on 2011-11-03
Does anyone know what package the appearance dialog is in?

It's not in the menu editor, I can't find it in the system-monitor, I can't tally up a PID from xprop... But ubuntu-bug mandates that I know what the package is or the PID is.

Is there a way to initiate a bug without using ubuntu?

---

