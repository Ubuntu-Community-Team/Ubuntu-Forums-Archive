---
title: "Opening a *graphical session* with the terminal ?"
date: 2012-02-16
forum: General Help
---

### Post by appreciation on 2012-02-16
Hi,

I'm experiencing an issue with the remote control.

My distant "graphical" linux session is currently closed.

From a SSH Terminal, with lets me control my computer by "commands", how could I open the "graphical session" in order to control it by "vinagre" (VNC) ?

Thank you very much for your help

---

### Post by Leppie on 2012-02-16
To use graphical applications during an SSH session:
```
ssh -X <user>@<host>
```
note that you will not be able to actually launch an application in an X session on the destination machine if the user used to log on with through SSH is not logged in on the destination machine.

---

### Post by appreciation on 2012-02-16
Thank you for your answer, but that doesn't seem open a graphical session : vinagre is still not working.

---

### Post by Leppie on 2012-02-16
> **appreciation said:**
> Thank you for your answer, but that doesn't seem open a graphical session : vinagre is still not working.
Vinagre is not a graphical session, but a desktop sharing utility. 
Like I said before: 
If there's not user logged in on the destination machine, you will not be able to start an X session on that machine remotely. Nor run graphical frontends on that machine.

---

### Post by appreciation on 2012-02-16
Thank you for your answer.

Starting a X session remotely, it's what I wanted to do.

---

