---
title: "Trying to install game from .bin file..."
date: 2011-04-24
forum: General Help
---

### Post by tinker1980 on 2011-04-24
I really just need to know what stupid thing I'm doing to cause this. I've extracted the files, and when I try to run the setup program, if I click on it from a file browser window in GNOME it just doesn't do anything. If I attempt to run the file (it's a .sh file, if that makes any difference)  in the terminal, it says "command not found", even though I'm in the directory, and can clearly see the file when running ls. 

If I try to run it in the file browser, and click on "Run in Terminal" then the terminal pops up, and goes away instantly, which isn't much help. 

I'm new at this of course, but it's driving me crazy.

---

### Post by r-senior on 2011-04-24
If you have a one-off script to run in the current directory, you have to specify it like this:

```
./myscript.sh
```

This is to stop rogue scripts and programs being run from the current directory accidentally.

---

### Post by KegHead on 2011-04-24
Hi!

any chance your file is available in a .deb file?

KegHead

---

### Post by tinker1980 on 2011-04-24
> **KegHead said:**
> Hi!

any chance your file is available in a .deb file?

KegHead

I'll look for it. It's certainly not in the software center. That would make it much easier. 

I tried to run it as r-senior mentioned, and it says none of the files it is looking for are present. I've tried re-downloading it, and nothing seems to be missing, but it sure thinks it is.

---

### Post by KegHead on 2011-04-24
Hi!

Name of game?

KegHead

---

