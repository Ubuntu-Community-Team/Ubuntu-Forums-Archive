---
title: "A simple shell script for Uncut L4D2"
date: 2011-08-15
forum: General Help
---

### Post by KirmesBude on 2011-08-15
Hey forumers :),

I recently installed left4dead2 and its working fairly good. One thing that bothered me though is that i have the cut version :/

I found Left4Uncut a memory patcher for left4dead and left4dead2. Its working great and I want to simplify the process. I created a script that starts left4uncut and then starts left4dead2. That script is .... not working.

```
#!/bin/sh

env WINEPREFIX="/home/bude/.wine-steam" wine left4update.exe

pause 5

env WINEPREFIX="/home/bude/.wine-steam" wine C:\\windows\\command\\start.exe /Unix /home/bude/.wine-steam/dosdevices/c:/users/Public/Desktop/Steam.lnk -applaunch 550
```

It starts left4uncut, but it does not proceed further. If i close left4uncut left4dead2 is started.
(If i start this in the terminal - the terminal window closes when i close left4uncut and thats it)

Hope someone can fix my script.

---

### Post by blind2314 on 2011-08-15
> **KirmesBude said:**
> Hey forumers :),

I recently installed left4dead2 and its working fairly good. One thing that bothered me though is that i have the cut version :/

I found Left4Uncut a memory patcher for left4dead and left4dead2. Its working great and I want to simplify the process. I created a script that starts left4uncut and then starts left4dead2. That script is .... not working.

```
#!/bin/sh

env WINEPREFIX="/home/bude/.wine-steam" wine left4update.exe

pause 5

env WINEPREFIX="/home/bude/.wine-steam" wine C:\\windows\\command\\start.exe /Unix /home/bude/.wine-steam/dosdevices/c:/users/Public/Desktop/Steam.lnk -applaunch 550
```It starts left4uncut, but it does not proceed further. If i close left4uncut left4dead2 is started.
(If i start this in the terminal - the terminal window closes when i close left4uncut and thats it)

Hope someone can fix my script.

Try backgrounding the first process to allow the second one to execute (without having to quit the first). You do this by putting a '&' after the command you're trying to run.

```
env WINEPREFIX="/home/bude/.wine-steam" wine left4update.exe &
env WINEPREFIX="/home/bude/.wine-steam" wine  C:\\windows\\command\\start.exe /Unix  /home/bude/.wine-steam/dosdevices/c:/users/Public/Desktop/Steam.lnk  -applaunch 550 &
```

---

### Post by KirmesBude on 2011-08-16
thx that worked

---

