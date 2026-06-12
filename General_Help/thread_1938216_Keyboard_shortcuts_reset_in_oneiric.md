---
title: "Keyboard shortcuts reset in oneiric"
date: 2012-03-09
forum: General Help
---

### Post by johnitsa on 2012-03-09
Hey guys,

I'm facing a rather weird issue in the past few days after doing a clean install of Ubuntu Oneiric (w/ gnome-shell) on my recently-bought Asus U36SD.

I set up my keyboard shortcuts using System Settings > Keyboard > Shortcuts, and some of them get randomly reset.

Most of my shortcuts include the win key (otherwise listed in the keyboard shortcuts as Mod4), but those containing only Mod4 + <letter> get reset every two-three reboots.

For instance, Mod4 + T (for terminal), gets reset to the standard Ctrl + Alt + T, while Shift + Mod4 + W (for browser) doesn't (I've set up the latter with the Shift key, because it seems that Mod4 + W didn't get intercepted at all. Something similar goes for Mod4 + E *for gedit*, which only worked once or twice).

I have no idea if this is a Ubuntu specific issue, or it's related to gnome-shell or even with my current hardware.

Has this happened to any of you? If so, did you manage to fix it?

---

### Post by forrestcupp on 2012-03-09
Yeah. I ended up giving up on using the Super key for shortcuts. It was pretty sporadic, and sometimes didn't work at all. It's not what I wanted, but I ended up mapping what I wanted to Ctrl+F# keys, and it worked perfectly, causing a lot less headaches. I also found that when some things just didn't want to work at all, it worked just fine when I created a custom shortcut directly to that program's binary, like with the terminal and nautilus. That's how I got Print Screen working again when it randomly just stopped working.

I'd be interested to see if there's any fix for Super key shortcuts, too.

---

### Post by johnitsa on 2012-03-09
It does seem pretty sporadic.

[quote=forrestcupp]It's not what I wanted, but I ended up mapping what I wanted to Ctrl+F# keys, and it worked perfectly, causing a lot less headaches.[/quote]

I can see your point there, and I did see that using any other key as a base for the shortcut works just fine, but I'm trying to keep this as simple and safe as possible. For the sake of speed I'd rather not use more than two keys per shortcut, while trying not to overlap with any existing global or per-app shortcuts.

[quote=forrestcupp]I also found that when some things just didn't want to work at all, it worked just fine when I created a custom shortcut directly to that program's binary, like with the terminal and nautilus. That's how I got Print Screen working again when it randomly just stopped working.[/quote]

I did the custom shortcut to the program's binary in the case of gedit. Again, it seemed to work once or twice, but then no dice.

Then again, even after searching for a few hours now, I still don't know which of oneiric/gnome-shell/my hardware is responsible for this issue.

Guess I'm going to have to wait and see of Precise will fix this when it goes stable. For the moment I'm not really keen on going beta on my main workhorse.

---

