---
title: "^s makes xterm hang"
date: 2012-06-29
forum: General Help
---

### Post by michaeljmcd on 2012-06-29
When playing Angband in an xterm (I prefer the ASCII only interfaces for both Angband and Nethack), if I hit Control-s to save the game, the terminal becomes unresponsive. The screen does not refresh and no commands have any effect (including ^z to background the process). Additionally, I am unable to close the window and have to terminate the process manually by opening another terminal and using kill -9. 

Is there some workaround for this issue?

---

### Post by diesch on 2012-06-29
Ctrl-S sends "XOFF, Pause transmission" which makes the terminal to stop updating. Hit Ctrl-Q "XON, Resume transmission" to resume normal operation.

As far as I know there is no way to change this behaviour.

---

### Post by tjwilli on 2012-06-29
Maybe try gnome-terminal instead?

---

### Post by itcotbtoemik on 2012-06-29
> **diesch said:**
> Ctrl-S sends "XOFF, Pause transmission" which makes the terminal to stop updating. Hit Ctrl-Q "XON, Resume transmission" to resume normal operation.

As far as I know there is no way to change this behaviour.

A place to start reading:
```
man stty
```

---

### Post by itcotbtoemik on 2012-06-29
> **tjwilli said:**
> Maybe try gnone-terminal instead?

In this instance, the choice of terminal emulator is irrelevant.

---

### Post by itcotbtoemik on 2012-06-29
For instance, in the stty manpage, you might notice
>        [-]ixon 
              enable XON/XOFF flow control


---

### Post by michaeljmcd on 2012-06-29
Ah. That makes sense.

[FONT=Courier New]stty -ixon[/FONT]

solves the problem  perfectly. I guess it's one more line for my .zshrc

Oddly enough, gnome-terminal doesn't seem to have the same issue out of the box. While on xterm I can turn the feature on and off with stty, gnome-terminal never seems to recognise it. It looks like they just completely ignore the signal.

---

### Post by itcotbtoemik on 2012-06-30
> **michaeljmcd said:**
> 
Oddly enough, gnome-terminal doesn't seem to have the same issue out of the box. While on xterm I can turn the feature on and off with stty, gnome-terminal never seems to recognise it. It looks like they just completely ignore the signal.

That's odd - since the feature is (from xterm's point of view) implemented
in the operating system's terminal drivers.  Whether XON is initially enabled
is a design choice (with some history of course) but it's easily customized
by users.  Not supporting XON/XOFF would be a bug.

---

