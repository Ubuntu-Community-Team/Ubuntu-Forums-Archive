---
title: "Change Name of Menu item"
date: 2009-08-31
forum: General Help
---

### Post by Vishnu V on 2009-08-31
Hai 
Is there any option to change name of menu item ??
for example i added ```
xwinwrap -g -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -wid WID -quiet 
``` in open with tab of video files  and it has the name xwinwrap in open with menu 
i want to rename it to Set Desktop 

Is it possible ?
If yes please help

---

### Post by mc4man on 2009-08-31
Go to ~/.local/share/applications ( .local is a hidden file in home folder

You should see a blue icon with the name of xwinwrap

Right click on it -> properties and give it a new 'display' name and icon if desired

( the actual name is userapp-xwinwrap-XXXXXX.desktop where XXXXXX is a series of letters and numbers. That can't be changed but not important for what you wish to do

---

