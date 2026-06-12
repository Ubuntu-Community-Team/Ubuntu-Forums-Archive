---
title: "Pidgin conversation windows lack window decoration"
date: 2009-08-06
forum: General Help
---

### Post by King_Critter on 2009-08-06
After trying out the window manager Ion3, I switched back to Gnome -- only to find my Pidgin conversation windows fullscreen and un-resizable, due to a lack of window decoration.

I have no idea how to fix this, so here I am. Any ideas?

---

### Post by Mike_IronFist on 2009-08-06
> **King_Critter said:**
> After trying out the window manager Ion3, I switched back to Gnome -- only to find my Pidgin conversation windows fullscreen and un-resizable, due to a lack of window decoration.

I have no idea how to fix this, so here I am. Any ideas?

Sounds to me like you need to reset Gnome. Here's what you do.

You're gonna have to switch to command prompt and enter in the following code. Write it down first VERY CAREFULLY. Then once you've gotten it written down, press Ctrl+Alt+F1 to switch to command prompt and enter in this command.

Remember that the command prompt will require you to log in. When entering your password it won't show that you're typing letters, but it recognises that you are.

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

This removes all settings for Gnome, turning everything back to default. To get back to your desktop, you have to press Ctrl+Alt+F7 while in the command prompt. You might have to restart you computer to see the changes take effect.

---

### Post by King_Critter on 2009-08-06
Excellent! Thanks for that -- it worked perfect. ^_^

---

