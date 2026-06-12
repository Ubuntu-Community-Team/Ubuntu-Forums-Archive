---
title: "Can I ask a program to stop, rather then kill."
date: 2010-03-25
forum: General Help
---

### Post by Amof on 2010-03-25
I have a quick little question.

Does anyone know the CLI command to ask a process to end? I don't want to just outright kill it because it is a process that does keep logs and save files. I am hoping there is a command that I can use to ask it "politely" to end.

Again, I am no asking for:

kill
pkill
killall



Anyone know?

---

### Post by UCSBGauchosRock on 2010-03-25
I don't think there are any commands to "stop" a program but opening system monitor-->processes-->Right click on program-->stop process is one way to do it.

:)

---

### Post by lykwydchykyn on 2010-03-25
> **Amof said:**
> I have a quick little question.

Does anyone know the CLI command to ask a process to end? I don't want to just outright kill it because it is a process that does keep logs and save files. I am hoping there is a command that I can use to ask it "politely" to end.

Again, I am no asking for:

kill
pkill
killall



Anyone know?

kill isn't necessarily "impolite"; it sends a TERM signal by default.  maybe sending a SIGHUP might be more polite, though I'm not entirely clear on that.  check out "man signal".

If it's a GUI app that takes dbus commands, you might be able to send a "close" command via dbus, but I don't know of a quick, universal way to do it.

---

### Post by Amof on 2010-03-25
> **lykwydchykyn said:**
> kill isn't necessarily "impolite"; it sends a TERM signal by default.  maybe sending a SIGHUP might be more polite, though I'm not entirely clear on that.  check out "man signal".

If it's a GUI app that takes dbus commands, you might be able to send a "close" command via dbus, but I don't know of a quick, universal way to do it.

Thanks! Thats what I was looking for.

---

