---
title: "CMD line works but launcher does not"
date: 2010-03-06
forum: General Help
---

### Post by skooter1121 on 2010-03-06
I want the gnome screenshot program to open after a 3 sec wait in select area mode.

command line $ sleep 3s; gnome-screenshot --area
works

When I create a launcher for panel with the same commands it does nothing.

I know there are many other ways to do this, GIMP, ImageMagick ....
(excellent tutorial) 
[http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux]("http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux")

But, I need to understand why this will not work, and why I must use a script (which I can easily create)instead.

-S

---

### Post by patchwork on 2010-03-06
your launcher needs xterm -e "command && command" or gnome-terminal -e "command && command"

---

### Post by asmoore82 on 2010-03-06
or you need to save your command as a full BASH script and call it from the launcher..

```
#!/bin/bash

sleep 3
gnome-screenshot --area

#End of File
```

Make it executable and I would place it in "$HOME/.local/bin/"

---

### Post by asmoore82 on 2010-03-06
I just did this on a whim...

You can go to "System -> Preferences -> Keyboard Shortcuts" and make sure sure
"Take a screenshot of a window" is set to something, mine is "Alt+Printscreen"

Now open the config editor: ```
gconf-editor
```

In the left pane, navigate down to "/apps/metacity/keybinding_commands"
In the right pane, change "command_window_screenshot" to "gnome-screenshot --area"

Now, the "Take a screenshot of a window" keyboard shortcut will start the area capture.

---

### Post by asmoore82 on 2010-03-06
> **skooter1121 said:**
> But, I need to understand why this will not work, and why I must use a script (which I can easily create)instead.

The launcher function is not/does not have a full command interpreter.
In other words, it can only launch executable files on the filesystem,
but it will search your $PATH for you to find them.

The simplest and probably most efficient way to force a command interpreter into the launcher, would be to use `sh` :
```
sh -c "sleep 3; gnome-screenshot --area"
```

---

### Post by skooter1121 on 2010-03-06
Thanx asmoore82,

Your succinct reply has answered my question. I have always wondered why some commands work and others do not.

Again my thanks,

-S

---

### Post by Simstud on 2012-03-16
> **asmoore82 said:**
> The launcher function is not/does not have a full command interpreter.
In other words, it can only launch executable files on the filesystem,
but it will search your $PATH for you to find them.

The simplest and probably most efficient way to force a command interpreter into the launcher, would be to use `sh` :
```
sh -c "sleep 3; gnome-screenshot --area"
```

Thanks! I used this to make a launcher for 

```
sh -c "totem --enqueue /home/simstud/Downloads/*.mp3"
```

Which is very useful and allows me to treat my Downloads folder like a dynamic playlist.

---

