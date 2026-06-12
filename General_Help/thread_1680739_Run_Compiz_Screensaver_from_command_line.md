---
title: "Run Compiz Screensaver from command line"
date: 2011-02-03
forum: General Help
---

### Post by inverser on 2011-02-03
Anyone know how to do this?

---

### Post by realzippy on 2011-02-03
So how it is solved?

---

### Post by matt_symes on 2011-02-03
Hi

Is this the command ?

```
gnome-screensaver-command -a
```

That kicks of my standard screen saver. Is that a compiz screen saver ?

Kind regards

---

### Post by stinkeye on 2011-02-03
In ccsm set a keyboard shortcut to initiate.
eg ctrl+shift+s


Install xdotool
```
sudo apt-get install xdotool
```



Terminal command
```
xdotool key ctrl+shift+s
```

You'll need to hit ctrl+shift+s to turn off.

---

### Post by inverser on 2011-02-03
> **stinkeye said:**
> In ccsm set a keyboard shortcut to initiate.
eg ctrl+shift+s


Install xdotool
```
sudo apt-get install xdotool
```



Terminal command
```
xdotool key ctrl+shift+s
```

You'll need to hit ctrl+shift+s to turn off.
Thank you! That works a treat. ;D

---

### Post by inverser on 2011-02-03
> **realzippy said:**
> So how it is solved?
Not sure why it was marked as solved before a solution was posted. I didn't mark it as such. 

Using xdotool to enter keybinding from command line works well.

---

