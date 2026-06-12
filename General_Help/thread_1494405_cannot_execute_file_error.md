---
title: "cannot execute file error"
date: 2010-05-26
forum: General Help
---

### Post by pwnjangles on 2010-05-26
I cannot execute  "untrusted" files/programs on xubuntu but I could on ubuntu? I'm admin but cannot edit permissions. I tried opening it with wine but still get the execute error and looked everywhere for a solution and can't find one.

---

### Post by AdotB on 2010-05-26
I'm afraid you haven't provided enough information to help.

What are you trying to execute?
How are you trying to execute it?
And what error message are you getting?

---

### Post by pwnjangles on 2010-05-26
Trying to open/install a exe program for windows with wine and it worked on ubuntu when I set permissions to execute but for some reason I can't edit the permissions in xubuntu.

I keep getting this error: The file '/home/****/Desktop/PalaceChat-WINDOWS.exe' is not marked as executable.  If this was downloaded or copied form an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by WorMzy on 2010-05-26
What happens if you run "chmod +x /home/****/Desktop/PalaceChat-WINDOWS.exe" and then try to run the file again?

---

### Post by pwnjangles on 2010-05-26
> **WorMzy said:**
> What happens if you run "chmod +x /home/****/Desktop/PalaceChat-WINDOWS.exe" and then try to run the file again?

It worked thank you so much <3 I'm new to linux and don't know too many commands.

---

