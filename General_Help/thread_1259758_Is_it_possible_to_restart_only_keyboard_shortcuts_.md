---
title: "Is it possible to restart only keyboard shortcuts and not Gnome?"
date: 2009-09-06
forum: General Help
---

### Post by ruipedroca on 2009-09-06
Hi,

Is it possible to restart only keyboard shortcuts and not Gnome?

I ask this because, from time to time, I'm surfing the web and the usual keyboard shortcuts stop working, like : ALT-F4 or ALT-TAB.
 
Thus, if I restart Gnome, I'll have to open again all the Firefox windows and tabs: sometimes several dozens! :o

---

### Post by CatKiller on 2009-09-07
It's possible that restarting *gnome-settings-daemon* will do it. Otherwise, you can use Edit &#8594; Preferences &#8594; Main &#8594; Show my windows and tabs from last time in Firefox to make the process of logging out and logging back in less painful.

---

### Post by ruipedroca on 2009-09-07
> **CatKiller said:**
> It's possible that restarting *gnome-settings-daemon* will do it..

When y run this command at the terminal I get this error:

kkou@edrf:~$ gnome-settings-daemon

** (gnome-settings-daemon:7780): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:7780): WARNING **: Could not acquire name
kkou@edrf:~$


If've googled around, but I couldn't find anyone who had successfully solved this problem; most guys just restart the computer wich is my current undesired solution :confused:

---

