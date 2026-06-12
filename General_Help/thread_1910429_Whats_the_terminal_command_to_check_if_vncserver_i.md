---
title: "Whats the terminal command to check if vncserver is running?"
date: 2012-01-17
forum: General Help
---

### Post by davegurn on 2012-01-17
Could someone please help me.

It brings up a list of running connections including vncsevers but i cant remember what it is.

Thanks

---

### Post by Idyll on 2012-01-17
Well, you could start by looking through your running processes like this:

ps -e

or search for some specific text in the output like this:

ps -e | grep sometext

I just noticed that on my machine running Ubuntu that Vino is the default VNC server and 

ps -e | grep vino

will find the process running on my machine listening for connections.

---

### Post by davegurn on 2012-01-17
thank you reminded me what it was

its

ps aux

---

