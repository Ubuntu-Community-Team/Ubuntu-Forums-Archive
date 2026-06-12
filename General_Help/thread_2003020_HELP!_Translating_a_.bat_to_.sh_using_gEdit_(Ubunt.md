---
title: "HELP! Translating a .bat to .sh using gEdit (Ubuntu12.04)"
date: 2012-06-13
forum: General Help
---

### Post by FenrirXIII on 2012-06-13
I am trying to run a file using LOVE 2D (64-bit) without compressing the file and renaming it to .love.

in WINDOWS, I was able to do this by using .bat:
```

@ECHO OFF
START  ""  "%PROGRAMFILES(x86)%\LOVE\love" .

```I was wondering if anybody could help me translate a .bat file to run in Ubuntu 12.04. A .sh seems to be a choice.

Also, where can I locate installed apps in Ubuntu? "/usr/share/bin"?

---

### Post by Vaphell on 2012-06-13
[https://love2d.org/](https://love2d.org/) is this it?
how did you install it? using deb or ppa? you should go with ppa as it will autoupdate your installed packages.

most likely *love file.name* should be enough (try in terminal)

love.sh
```
#!/bin/sh

love file.name
```
make it executable
```
chmod +x love.sh
```
executables are usually in /usr/bin but typing that usually is not required as that directory is listed in PATH variable. /usr/share is for various assets like audio and graphics

Scripts may have .sh extension but it's not required, any filename will do. Executable bit is what matters and the first line which defines what should interpret the script.

---

### Post by FenrirXIII on 2012-06-13
@Vaphell

I PPA it.

Thanks for the input! I wasn't trying to open the actual application but rather a FILENAME.lua to run on LOVE application without compressing FILENAME.lua into a FOLDER.love (former .zip). Like a shortcut folder opened in FOLDER.love .  Sorry for not clarifying. It was difficult to put in worded details.

Anyways, you actually did help though, that trigger me to think "hey, maybe I can OPEN WITH the entire folder to LOVE" and viola that's what I was hoping for.

So, to clarify a bit.

In Ubuntu, I don't need a .bat file to open uncompressed folder in LOVE 2D. Which could be a hassle if I couldn't. It would mean I would work on kept renaming .love to .zip every time i make changes in the project then renaming it back to .love. I was trying to avoid that step and found it in OPEN WITH

---

