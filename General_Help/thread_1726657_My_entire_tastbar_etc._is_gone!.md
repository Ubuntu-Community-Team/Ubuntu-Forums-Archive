---
title: "My entire tastbar etc. is gone!"
date: 2011-04-11
forum: General Help
---

### Post by senca on 2011-04-11
Hey everyone,

I tried to put my logoff button back by entering a command into the terminal. Unfortunately I shut down the terminal during the proces and now my whole taskbar is gone. The only thing in my screen are the folders on the desktop. How can I fix this? I'm afraid to shut the laptop down because I could lose chrome as wel as this was stil open when it happened :)

greetz

---

### Post by matt_symes on 2011-04-11
Hi

Open a terminal by pressing Ctrl + Atl + t and type

```
killall gnome-panel
```

to respawn your panels. Does that fix it ?

Kind regards

---

### Post by senca on 2011-04-11
OK I tried gnome-panel --replace
This was the first command I tried. But it keeps running and when ctrl-c 'in it again, the menu's are gone again :s

---

### Post by senca on 2011-04-11
> **matt_symes said:**
> Hi

Open a terminal by pressing Ctrl + Atl + t and type

```
killall gnome-panel
```

to respawn your panels. Does that fix it ?

Kind regards

it sais:

gnome-panel: no process found

---

### Post by senca on 2011-04-11
Fixed it! Did the replace again and rebooted.
Everything is back!

---

