---
title: "Need help with terminal."
date: 2011-05-01
forum: General Help
---

### Post by TrickStyle on 2011-05-01
nvm

---

### Post by TrickStyle on 2011-05-01
nvm

---

### Post by Jonny87 on 2011-05-01
So can you access the terminal in the same screen as you chrome?

---

### Post by TrickStyle on 2011-05-01
nvm

---

### Post by megahost on 2011-05-01
First try...

```
unity --reset
```

This will make the Unity bar appear again with all the other essentials to 11.04

Next, through the the "Ubuntu Software Center," remove Compiz config.

Tell me what happens

---

### Post by TrickStyle on 2011-05-01
nvm

---

### Post by kaldor on 2011-05-01
GNOME is already there. Log out of your session, and when you select your username select "Ubuntu Classic" in the menu on the bottom of the screen :)

---

### Post by Jonny87 on 2011-05-01
In the same screen the you can see Google Chrome, do you have any folders on the desktop?

---

### Post by TrickStyle on 2011-05-01
nvm

---

### Post by Jonny87 on 2011-05-01
I have had a similar experience. Here are two options if you get it again.

Fist:
Try Open a terminal with out dropping out of the GUI. Ctrl+Alt+T often works. 
If you can get the Terminal open. Try the command 
```
unity
```or even;
```
compiz
```if you have it installed by then.

Second:
Failing that, try getting a folder open ether by any on your desktop or by right click -> Create Folder.
Open the Folder then browse to the root dir, then to /usr/bin.
From there you can double click the command to run ether one you want, compiz, unity, x-terminal-emulator (or xterm).

If these work try adding one to your "Startup Applications".

Also try renaming .config (in your home dir) to something like .config-old then logout and log back in. A new .config will be created with defaults. By renaming it you will still have the original settings just in case you need them. This worked for me and I didn't need to have it in startup application, there must have been something in my .config that was conflicting.

---

### Post by TrickStyle on 2011-05-01
nvm

---

### Post by TrickStyle on 2011-05-01
Never mind. -.-

I'll download Maverick and make a fresh installation, as 11.04 looks like a complete disaster to me.

---

