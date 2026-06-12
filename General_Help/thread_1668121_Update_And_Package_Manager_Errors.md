---
title: "Update And Package Manager Errors"
date: 2011-01-15
forum: General Help
---

### Post by Jdarl on 2011-01-15
Okay so I'm totally new to ubuntu and i have a major problem with updating ubuntu, i was looking around for some linux based gaming and came across the online game called "Regnum Online" i installed it and all goes fine untill i restart my computer next day, the top panel that usually has daily updates is missing and in its place is a red circle with an x through it i hover over it with my mouse and it reads:

"an error occurred please run package manager from the right-click menu or apt-get in a terminal to see what is wrong."

Which i then right-click and open package manager and it gives the following response:

"E: Type '<!DOCTYPE' is not known on line 2 in source list /etc/apt/sources.list.d/onemyndseye-regnum.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report."

at the bottom of this message reads:
"this usually means that your installed packages have unmet dependencies."

What does this all mean? Can anyone help me i have no idea how to fix this and dont want to lose my personal files by wiping and reinstalling ubuntu.

Help Please! :confused:

---

### Post by Pollox on 2011-01-16
I suspect that you left out the part where you found some special instructions somewhere on how to install regnum online from someone's ppa. It looks like whatever instructions you got were wrong/outdated, because, as you said there's an error on line 2 in the file /etc/apt/sources.list.d/onemyndseye-regnum.list . The best way to handle this is to go find the instructions you followed and undo what you did. Or you can open the software sources from your package manager and remove the regnum source. Or perhaps someone else will post something about editing your sources.list file by hand. Anyway, may I recommend installing the game using the installer provided by the official website: [http://www.regnumonlinegame.com/index.php?l=1&sec=6](http://www.regnumonlinegame.com/index.php?l=1&sec=6)

---

