---
title: "Change Terminal Font"
date: 2010-06-16
forum: General Help
---

### Post by Thomas B. on 2010-06-16
I've been playing around with Conky, and what I want to do is temporarily change the font the terminal outputs in. I know I can go to Profile Preferences and change it there, but I was wondering if there was a command to change it, just so it remains that font for the duration of the next command.

---

### Post by KeyserSoze93 on 2010-06-16
Not sure if you can do it in GNOME Terminal, but it's simple in URXVT:

```

echo -n "\033]710;xft:Kochi Gothic:antialias=false:size=12\007\033]711;xft:Kochi Gothic:antialias=false:size=12\007"

ls

echo -n "\033]710;7x14\007\033]711;7x14\007"

```

---

### Post by WorMzy on 2010-06-16
> **Thomas B. said:**
> I've been playing around with Conky, and what I want to do is temporarily change the font the terminal outputs in. I know I can go to Profile Preferences and change it there, but I was wondering if there was a command to change it, just so it remains that font for the duration of the next command.

Not sure what conky has to do with anything here. If you want to change the font in conky use a font tag; e.g. ```
${font Liberation Sans:style=Bold:size=8}TEXT GOES HERE${font}
```

If you want to change the gnome-terminal font, right click on a gnome-terminal window -> Profile -> Profile Properties, uncheck "use the system fixed width font", click the font button, and choose the font you want from the font window. I don't think you can do a per line font change.

---

