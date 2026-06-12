---
title: "Keyboard Shortcut Doesn't Work"
date: 2011-02-28
forum: General Help
---

### Post by steevven1 on 2011-02-28
I created a bunch of keyboard shortcuts via "System > Preferences  Keyboard Shortcuts," and they all work flawlessly except one: Nautilus. I just set it to run the command "nautilus" and it doesn't do anything. My GNOME panel launcher runs the same command just fine. Any ideas? Thanks in advance!

---

### Post by stinkeye on 2011-02-28
Give nautilus a directory to start in.

eg```
nautilus /home/steevven
```

---

### Post by steevven1 on 2011-02-28
> **stinkeye said:**
> Give nautilus a directory to start in.

eg```
nautilus /home/steevven
```


PERFECT, thank you, but here is another mystery for you: My keyboard shortcut for gnome-terminal starts me out at / and my GNOME panel launcher (with the exact same command) starts me out at ~ (in the terminal). What's the deal with that (and how can I fix it)?

Thank you so much!

---

### Post by stinkeye on 2011-02-28
I don't know the reason for this but there is an existing shortcut 
for the gnome-terminal.
ctrl+alt+t


or use
```
gnome-terminal --working-directory=/home/steevven
```

---

