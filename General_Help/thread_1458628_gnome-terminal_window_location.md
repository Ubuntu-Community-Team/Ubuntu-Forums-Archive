---
title: "gnome-terminal window location"
date: 2010-04-20
forum: General Help
---

### Post by idlehands on 2010-04-20
is there a way to have gnome open in the upper right or left corner instead of the lower left corner when i start it?

thanks

---

### Post by nothingspecial on 2010-04-20
Set the geometry eg

```
gnome-terminal --geometry=?x?+0+0
```

Change the ?s for the horizontal and vertical size you like (in characters)

The 0s will open it top left.

Then change the method you use to launch it (launcher, menu, keybinding) to that command.

Thinking about it, I can`t remember weather gnome terminal uses ?x?x0x0 instead, experiment first.

---

### Post by mcduck on 2010-04-20
Sure, you can define the exact location and size for the terminal when it starts.

1. Open a terminal, move it where you want it and resize it to desired size.

2. Run "xwininfo" and click the terminal window. Note the "geometry" output in the last line. (in my case it was "-geometry 120x36-43+65")

3. Go to System/Preferences/Preferred Applications, and on the "System" tab change the terminal to "Custom". Set the command to "gnome-terminal --geometry 120x36-43+65" (use the geometry from your xwininfo output), and the "Execute flag" to "-x".

---

### Post by idlehands on 2010-04-20
awesome thanks!

---

