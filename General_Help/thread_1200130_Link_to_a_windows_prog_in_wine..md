---
title: "Link to a windows prog in wine."
date: 2009-06-29
forum: General Help
---

### Post by celticbhoy on 2009-06-29
I would like to know how to have a desktop launcher run a windows app under wine. The app is located on a separate partition that is auto mounted. I tried making a link and copying it to the desktop, but that doesn't work.

---

### Post by themusicalduck on 2009-06-29
Right click on the desktop and select Create Launcher.

In the command field you need to enter wine /path/to/exefile

Remember if there are spaces in any folder you need to use a blackslash before the space. Like /Program Files/ would need to be /Program\ Files/. Otherwise putting the whole path in quotation marks "" works too.

---

### Post by celticbhoy on 2009-06-29
I tried that and it seems to do nothing. I even setup a simple bash script to run it like so :-

#!/bin/bash
clear
cd /media/Games/Games/Star\ Wars/SWPR
wine RACER.EXE

But all I get is :-

wine: could not load L"Z:\\media\\Games\\Games\\Star Wars\\SWPR\\RACER.EXE": Bad EXE format for 

Yet when I double click the RACER.EXE file from nautilus it works fine.

---

### Post by themusicalduck on 2009-06-30
If you just type wine /media/Games/Games/Star\ Wars/SWPR/RACER.EXE into a terminal, does that give the same error message? or does it work?

---

