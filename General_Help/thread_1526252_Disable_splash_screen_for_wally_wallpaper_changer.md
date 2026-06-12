---
title: "Disable splash screen for wally wallpaper changer?"
date: 2010-07-07
forum: General Help
---

### Post by alem189 on 2010-07-07
Hi - I want to start wally on login, but I don't want to show the splash screen, because it's annoying when you log in and your first view is blocked by a big rectangle. There doesn't seem to be an option for disabling this in the settings, though. Can it be done through some kind of command line option or something? Just a thought.

---

### Post by alem189 on 2010-07-09
*bump*

---

### Post by vktRus on 2010-07-12
Message from author:

there's no option about that. Anyway, if you'd like to build Wally from sources, you can comment this line in main.cpp file:

        ```
splash->show();
```(it should be line 97, but I'm not so sure, I've a modified source code, compared to the official one).
Tony.

---

### Post by vktRus on 2010-07-12
For Ubuntu 10.04 32 bit binary
[COLOR=Blue][U]
[wally without splash screen]("http://depositfiles.com/files/vq4aostad")
[/U][/COLOR]

---

### Post by alem189 on 2010-07-12
Thanks, I compiled from source since mine's 64 bit, Thanks for the info!

---

### Post by abh83 on 2010-08-12
> **vktRus said:**
> For Ubuntu 10.04 32 bit binary
[COLOR=Blue][U]
[wally without splash screen]("http://depositfiles.com/files/vq4aostad")
[/U][/COLOR]

Thx for this! But what to do when i'v already installed wally?

---

### Post by vktRus on 2010-08-13
Install wally.
Download fix.
Replace [B]/usr/bin/wally
[/B]Go to Synaptic. Find **wally** and block version.

---

### Post by alem189 on 2011-05-20
UPDATE: as of version 2.4.1 of Wally, the splash screen can now be disable. It's not in the repositories yet though.

---

