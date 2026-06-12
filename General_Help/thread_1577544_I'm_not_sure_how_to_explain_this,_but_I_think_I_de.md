---
title: "I'm not sure how to explain this, but I think I deleted the &quot;Me menu&quot;"
date: 2010-09-19
forum: General Help
---

### Post by Artemis Fowl on 2010-09-19
Or atleast I think that's what it is called. I'm referring to the little username thing in the top right corner. I have attached a screenshot to help explain.

More information:When I logged on a little while ago, a message said something about something not working and asked me if I wanted to delete it, so I clicked delete, and this happened. Yeah, PEBKAC error, and I'm probably what you would consider a "dumb" user, but I can assure you I won't do this again.

---

### Post by Artemis Fowl on 2010-09-19
Fixed it myself with a command, here it is if anyone finds this thread by googling:
[SIZE=3]gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel[/SIZE]

---

