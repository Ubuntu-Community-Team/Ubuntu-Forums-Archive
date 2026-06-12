---
title: "Blank Background in Gnome: Cannot Do Anything in GUI!"
date: 2011-02-04
forum: General Help
---

### Post by alexp91k on 2011-02-04
I was changing a few options in Compiz-Fusion today. When I saved one of the options, the X Server restarted and then suddenly, I had no taskbars or anything. I could run F2 to get a GUI Run dialog box to come up, but I can't run any GUI programs. I try GEdit, Google-chrome but nothing comes up. There's no taskbar, no AWG Dock, nothing. Just my wallpaper and I can't do anything with it.

I'm kind of annoyed that one little change can cause the whole X Server to crash and not start up. I tried booting into "Recovery Mode" but Linux doesn't automatically detect my drivers in this mode so I can't boot up into it. I've tried rebooting and I still get the wallpaper.

In TTY1 terminal, is there anything I can do to revert these changes?

As in, can I:
- Revert the changes of Compiz by somehow reaching a Compiz GUI (even though I can't open any GUI windows in GNOME)?
- Uninstall Compiz? (I tried this and it said it supported gnome-desktop..I decided not to get rid of it, any ideas? If I uninstall Compiz, will it revert and restore all the changes Compiz made?)
- Uninstall and reinstall GNOME? (if so, how can I do this?)
- Access the Compiz config through the terminal so I can perhaps find the option I set and revert it?

This is pretty urgent because I can't use my machine at all, so any help would be really really appreciated. Thank you! Any ideas will help.

EDIT:
I'm still able to use the Cube and switch between workspaces (CTRL+ALT+<left/right>) which leads me to believe Compiz is working. I can also open the GUI run dialog, but just no other windows. I think Compiz must have an error and I'll have to restore to Metacity to view windows again.. any ideas?

---

### Post by nathan726 on 2011-02-05
You can switch off compiz/switch on metacity with:

```
metacity --replace &
```

Compiz settings are stored in ~/.gconf/apps/compiz - perhaps you could restore these files from a Live CD?

---

### Post by mcduck on 2011-02-05
> **nathan726 said:**
> You can switch off compiz/switch on metacity with:

```
metacity --replace &
```

Compiz settings are stored in ~/.gconf/apps/compiz - perhaps you could restore these files from a Live CD?

Yep, that would work. Switching to Metacity should allow getting back to CompizConfig and undoing whatever change was made there that caused the problem.

what comes to Compiz settings, if you arr able to tell which setting you changed, then it's rather simple thing to give you a command to change it back to a sensible value. Without knowing which setting it was, the only option we can give you is resetting all your Compiz settings to defaults by deleting it's config files from your home directory (by the way, unistalling Compiz wouldn't do that, as uninstalling a package never touches the config files in user's home directories)

Anyway, it doesn't sound like Compiz error, more like a user error. Perhaps you were tweaking opacity settings and made everything transparent or something like that? Compiz does follow the generic Linux philosophy of giving users enough rope to do whatever they want, including hanging themselves with it... :D

---

### Post by alexp91k on 2011-02-06
> **mcduck said:**
> Yep, that would work. Switching to Metacity should allow getting back to CompizConfig and undoing whatever change was made there that caused the problem.

what comes to Compiz settings, if you arr able to tell which setting you changed, then it's rather simple thing to give you a command to change it back to a sensible value. Without knowing which setting it was, the only option we can give you is resetting all your Compiz settings to defaults by deleting it's config files from your home directory (by the way, unistalling Compiz wouldn't do that, as uninstalling a package never touches the config files in user's home directories)

Anyway, it doesn't sound like Compiz error, more like a user error. Perhaps you were tweaking opacity settings and made everything transparent or something like that? Compiz does follow the generic Linux philosophy of giving users enough rope to do whatever they want, including hanging themselves with it... :D

I did this and the problem didn't seem to go away. Had to throw in an extra 3 hours rebuilding my configurations off my last backup. Guess the moral here is to backup more often when you're not sure what you're doing (or what can crash the system irreparably).

---

### Post by Habitual on 2011-02-06
> **nathan726 said:**
> Compiz settings are stored in ~/.gconf/apps/compiz - perhaps you could restore these files from a Live CD?

why not just remove the directory? :wink:

---

### Post by mcduck on 2011-02-07
> **alexp91k said:**
> I did this and the problem didn't seem to go away. Had to throw in an extra 3 hours rebuilding my configurations off my last backup. Guess the moral here is to backup more often when you're not sure what you're doing (or what can crash the system irreparably).

Any misconfiguration you could possibly do in Compiz settings sure isn't irreparable. :D

You didn't say exactly what you did and how it didn't work so I can't say why you didn't get the problem solved, but switching to Metacity definitely will give you a working window manager, no matter what your Compiz settings are, and after that it sure shouldn't be any problem to change the Compiz settings back to sensible ones (or reset them completely).

---

