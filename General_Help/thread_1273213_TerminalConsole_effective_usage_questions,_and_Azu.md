---
title: "Terminal/Console effective usage questions, and Azureus nogui questions."
date: 2009-09-23
forum: General Help
---

### Post by proxess on 2009-09-23
A few questions regarding consoles/terminals:

-If I've got an application running on a remote terminal, how do I "minimize" it? Like Pause/Break=>fg, but without stopping it.

-If I have the application running on the remote terminal, how do I disassociate it from the remote terminal, so I can close the terminal and keep the application running?

-I've got Azureus with GUI running at home. How do I use it's console remotely without having to kill the process with the GUI and run a new one with ui=nogui? How about other remote applications with console support?

-Is it possible to pass audio through Putty and/or XMing, if I use an application like Orpheus or Audacious or VLC (Locally or Remotely)?

---

### Post by proxess on 2009-09-24
*Bump* Unfortunately these get lost as new posts come really fast.

---

### Post by nothingspecial on 2009-09-24
> **proxess said:**
> A few questions regarding consoles/terminals:

-If I've got an application running on a remote terminal, how do I "minimize" it? Like Pause/Break=>fg, but without stopping it.

-If I have the application running on the remote terminal, how do I disassociate it from the remote terminal, so I can close the terminal and keep the application running?

-I've got Azureus with GUI running at home. How do I use it's console remotely without having to kill the process with the GUI and run a new one with ui=nogui? How about other remote applications with console support?

-Is it possible to pass audio through Putty and/or XMing, if I use an application like Orpheus or Audacious or VLC (Locally or Remotely)?

You need screen

```
sudo apt-get install screen
```

```
screen
```

Use the F1 F2 F3 etc buttons to switch between screens/terminals

To detach a session but keep the process running press Ctrl+A then D

To reatach it, type ```
screen -r
```

This works remotely also.

```
man screen
```

---

### Post by proxess on 2009-09-24
Life saver! Thank you very much! I also saw that I can steam music using EsounD and XMing. 

Is a detached screen hooked onto our current login? For example: I'm at work, and run Orpheus. If I detach it, log off, will I be able to re-attach it when I get home?

---

### Post by nothingspecial on 2009-09-24
Yep, or from any else in the world if you have ssh set up correctly and a dynamic or static ip adress for your router.

---

### Post by proxess on 2009-09-24
Definitely what I wanted! Thank you very very much!!!

---

