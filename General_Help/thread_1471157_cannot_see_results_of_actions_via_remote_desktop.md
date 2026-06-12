---
title: "cannot see results of actions via remote desktop"
date: 2010-05-03
forum: General Help
---

### Post by wordsmithereens on 2010-05-03
Hi All;

I have Tight VNC installed on a Win 7 machine, and Remote Desktop enabled on an Ubuntu 10.04 machine.

I can connect to the Ubuntu machine using the VNC viewer, but the results of mouse click, typing, etc. are not visible on the Win7 machine, though I can see the screen and the cursor movements. If I look at the screen of the Ubuntu machine, all the actions are shown, e.g. drop-down menus show, apps start, typing is visible. 

What did I miss in configuring either the server side on the Ubuntu machine or the viewer side on the Win 7 machine?

Thanks!

---

### Post by Maheriano on 2010-05-03
It's about sessions. If you are creating a new session on the machine then each computer is only going to show actions inside its respective session. If you're able to grab the current running session (which I believe VNC can do), then you'll see it on both machines as they're running the same session.

---

### Post by wordsmithereens on 2010-05-03
> **Maheriano said:**
> I If you're able to grab the current running session (which I believe VNC can do), then you'll see it on both machines as they're running the same session.

I don't see anything regarding sessions other than: 

[IMG]http://timster.net/1260df166b0321cecd673f256402a2de.png[/IMG] in the Connection Options.

---

### Post by wordsmithereens on 2010-05-03
System, Preferences, Appearances, on the Visual Effects tab, select NONE.

---

### Post by strebor71 on 2010-05-03
> **wordsmithereens said:**
> System, Preferences, Appearances, on the Visual Effects tab, select NONE.

perfect! thank you for posting this. i was having a hell of a time finding a reason for this not working. :D

---

### Post by wordsmithereens on 2010-05-05
I found it here under a different thread that hadn't shown up in previous searches. Glad it worked for you. It was driving me around the bend too!

---

