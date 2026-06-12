---
title: "Startup Application commands"
date: 2011-11-07
forum: General Help
---

### Post by nightwarrior51 on 2011-11-07
I know that I may start up Last.fm by inputting the command: 
```
lastfm
```

How am I able to start Last.fm without the window opening up? I just want it running in the background.

---

### Post by spiky001 on 2011-11-07
Have you tried ```
lastfm &
```

---

### Post by nightwarrior51 on 2011-11-07
No, when I put it into terminal, it spits this back and opens the window:

```
[1] 5639
```

---

### Post by Slim Odds on 2011-11-07
See if lastfm has some command line options. It is a GUI program.

---

### Post by ReptilianShadow on 2011-11-07
How about:
```
lastfm -tray
```
Starts lastfm without opening a window and adds a notification icon to the top GNOME panel, not sure if that's all you want it to do..

---

### Post by nightwarrior51 on 2011-11-07
> **ReptilianShadow said:**
> How about:
```
lastfm -tray
```
Starts lastfm without opening a window and adds a notification icon to the top GNOME panel, not sure if that's all you want it to do..

That is exactly what I wanted it to do! Thank you so much. I'm a little new to Ubuntu, sometimes I can't find my way around. How did you find that? I mean other commands to go with it?

---

### Post by ReptilianShadow on 2011-11-07
A good practice  with the command line is using the man command. I got that command from:
```
man lastfm
```
(use q to exit this)
Almost all commands have a man (manual) entry, with documentation of options and proper use of a command.

Glad to see other newcomers using the command line too.

---

