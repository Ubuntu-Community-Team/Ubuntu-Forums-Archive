---
title: "Remote suspend via ssh"
date: 2009-11-23
forum: General Help
---

### Post by allanlewis on 2009-11-23
I'd like to be able to remotely suspend a server, to which I have ssh access with root privileges, but if I run "pm-suspend", the process runs (and the server does go into suspend) but the ssh session hangs, presumably because it's lost connection and it doesn't know what to do. How can I make it run the process and disconnect, regardless of whether the process executes successfully or not?

---

### Post by fargle on 2009-11-23
Perhaps run the suspend command from an "at" job you submit for, say, five minutes from now?  You could submit it and then disconnect.

You could also probably just run a shell script that does "sleep 30" as its first command, run it in the background and disconnect.

---

