---
title: "Fullscreen out of range"
date: 2010-05-09
forum: General Help
---

### Post by akvilio on 2010-05-09
Hi, 
I'm a new user and I know that this topic has been brought few times but i can't find an answer for this:
I'm using ubuntu 10 and i tried, just for fun, installing Rise Of The  Triad and Free Doom, but i get the 'Out Of Range' error when the fullscreen mode  kicks in.
I recall that i had the same thing on Windows XP. 
The solution was to get into the files of the game (It was Quake 2 or 1)
and set the game so it will start in windowed mode, then of course it  can be changed to fullscreen with lower resolution.
I wonder if there's a method here too.

---

### Post by dino99 on 2010-05-09
i dont think you can find a way, its a programming design issue or your graphic card cant do the job

---

### Post by akvilio on 2010-05-10
I don't think i'ts my graphic card because i played games that require much more than doom 1 or ROTT (for that matter). although those games were played with windows xp.

---

### Post by maverick77_uk on 2010-05-10
Hi,

If its an on-board GPU, try increasing the amount of RAM dedicated to it in BIOS, that helped me when I had the exact same issue.  It may only be set to 16 or 32MB by default, and with hgher resolutions, can't handle it.

---

### Post by sedawk on 2010-05-10
If your monitor says out of sync (or range) then you
might check if you can start the different programs
from the command line with some special command line
switches (that depend on the programs).
Old CRT monitors have been much more flexible than
the new LCD stuff that only allows 60/70 Hz.
I know of LCD monitors that fail to show the BIOS
startup text screens during boot procedure.
"Broken by design".

When running windows games with Wine you can run
"winecfg" and define a virtual screen with a smaller
resolution than your real desktop.
I like to use that a lot for old games because
that way I still see if something important is happening
on the desktop (1. clock, 2. mail, 3. whatever).

---

### Post by akvilio on 2010-05-10
This specific game (ROTT) is an ubuntu version.
Actually i found a way myself (not the best option but at least i can play...).
What i did is this:
I searched for the game folder and a file called rott, there i saw the next line:

command="/usr/games/rott -fullscreen -resolution 800x600"\

copied this part to the terminal:
/usr/games/rott -fullscreen -resolution 800x600

and changed the "-fullscreen" to "-windowed"
and that's it!
The game works fine, although it's not in fullscreen mode... but oh well...

and THANK YOU for your help.

---

