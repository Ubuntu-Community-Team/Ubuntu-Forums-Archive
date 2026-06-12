---
title: "zenity notification not working 12.04"
date: 2012-09-03
forum: General Help
---

### Post by bashologist on 2012-09-03
```
zenity --notification  --text "System update necessary"
```
results in a popup window opening, instead of the expected icon in the tray using gnome-classic.

after switching from ubuntu 10.04 to 12.04, this changed for some reason.

it should open a little icon thingey in the tray area.

also, note that i have a notification applet active and azureus is in there just fine.

can use gtk2 perl tho so i'll use this...

sudo apt-get install libgtk2-trayicon-perl libgtk2-perl
[http://pastebin.com/raw.php?i=CZLed7Rm](http://pastebin.com/raw.php?i=CZLed7Rm)

---

### Post by sghpunk on 2012-12-12
I have the same trouble.
Someone can help? Or I need to report bug?

---

