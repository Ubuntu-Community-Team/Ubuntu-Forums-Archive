---
title: "Help finding pidgin plugin"
date: 2009-08-20
forum: General Help
---

### Post by SpitfireSMS on 2009-08-20
Ok so I installed pidgin 2.6.1 on jaunty, and now it wont notify using the jaunty notification system.
Its because the plugin for pidgin isnt installed, and I cannot seem to find it.
It doesnt seem like it would be elusive, but I cant find it anywhere.

---

### Post by SpitfireSMS on 2009-08-20
Ok so I solved it, sorry for taking your time if you read this.
Ill post the solution for it in case someone else searches this:

Make sure pidgin is not running first. Then open up a terminal and type
sudo apt-get install libnotify1 pidgin-libnotify

The only thing left now is to turn it on.
1. Open up Pidgin and goto the buddy list
2. Choose menu item Tools -> Plugins
3. Enable the plugin "Libnotify Popups"

---

### Post by GavCity on 2009-08-21
Thank you, that is handy information.

---

