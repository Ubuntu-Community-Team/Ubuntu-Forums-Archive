---
title: "Xfce will NOT manage Desktop"
date: 2009-08-15
forum: General Help
---

### Post by Bruce M. on 2009-08-15
I have tried everything, nothing seems to work. After a fresh install today, the check box remains empty. so I click on it.

[ ] Allow Xfce to manage the Desktop

Next I click on the desktop, no left mouse button so I look again and see it is UN-CHECKED!

Of course I want Xfce to manage my desktop, that's why I use Xubuntu.

Anyone got a fix?

Thanks
Bruce

[CENTER][SIZE="6"][COLOR="Green"]**SOLVED:**[/COLOR][/SIZE][/CENTER]

Don't know where I found this, I can't seem to Google it again, however in the two directories: **~/.cache** and **~/.config**: delete everything related to xfce4, leave other files alone.

Do a **"RESTART"** choosing option #1 under Sessions.

**[COLOR="#008000"]BINGO![/COLOR]** However I now need to configure themes and icons etc. But it is working.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-08-16
Actually the "SOLVED" part above only worked for about 10 minutes.  However I think I did find what caused it.

Settings > Xfce Settings Manager > Desktop

I do NOT like icons on my desktop!

Desktop Preferences > **Behavior** > **Desktop Icons**

and I slected **"None"** - bad choice - always loose:

Desktop Preferences > **Behavior** > **Appearance**

[ ] Allow Xfce to manage the desktop.

You can choose: Desktop Preferences > **Behavior**

And blank out "Show icons for: (4 of them)

Other than that, I'll have to continue moving stuff OFF the desktop.

Have a nice day.
Bruce

---

### Post by Brandon Williams on 2009-08-17
Actually, the settings that you want in that panel are:

    [X] Allow Xfce to manage the desktop

and

    Desktop Icons: None

This is how my desktop preferences are configured, and it works exactly as expected ... Xfce manages the desktop and there are no icons on the desktop.

If you say that you do no want Xfce to manage the desktop, then you won't get any Xfce menus with clicks on the desktop, nor will Xfce handle your desktop wallpaper for you.

If you tick or untick the 'Allow Xfce ...' button, the preference may be overridden if you do not also ensure that your session is saved on logout. On my system, changing that setting pops up a dialog informing me of this.

---

### Post by Bruce M. on 2009-08-19
> **Brandon Williams said:**
> Actually, the settings that you want in that panel are:

    [X] Allow Xfce to manage the desktop

and

    Desktop Icons: None

This is how my desktop preferences are configured, and it works exactly as expected ... Xfce manages the desktop and there are no icons on the desktop.

That is exactly what did NOT work for me.  It was driving me nuts.

> **Brandon Williams said:**
> If you say that you do no want Xfce to manage the desktop, then you won't get any Xfce menus with clicks on the desktop, nor will Xfce handle your desktop wallpaper for you.

If you tick or untick the 'Allow Xfce ...' button, the preference may be overridden if you do not also ensure that your session is saved on logout. On my system, changing that setting pops up a dialog informing me of this.

However, after I did what I did I see:

[X] Allow Xfce to manage the desktop.
[X] Automatically save session on log out.

And that's working, I have Xfce, but I also have "icons" that I don't want, almost afraid to try "None" again, as that's what started my problems.  :confused:

Have a nice day.
Bruce

---

