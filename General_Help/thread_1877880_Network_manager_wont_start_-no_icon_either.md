---
title: "Network manager wont start -no icon either"
date: 2011-11-08
forum: General Help
---

### Post by FLCL on 2011-11-08
Right so, clean install..1 day later. **11.04**

My wireless was set to autoconnect, but now the icon is gone and it won't connect. Reading up I found out this is due to nm-applet crashing. 
Restarting does not fix the issue, no IP, iwconfig shows no AP association 

I ran:
```
nm-applet
```
and received the following:

```
Error: (9) Connection ":1.423" is not allowed to own the service "org.freedesktop.NetworkManagerUserSettings" due to security policies in the configuration file'

```

Also, my laptop battery icon is missing as well once this started. How do I get wireless back?

**Edit:** removing and re-adding notification area, and running 
```
 sudo nm-applet
```
brings back the icon, however unusable, prints the following while command runs:
```
** (nm-applet:25939): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:25939): DEBUG: old state indicates that this was not a disconnect 0
```
and just has a blinking cursor

**Edit2:**
Resolved by attempting to uninstall nm-applet 
```
 sudo apt-get purge network-manager
```
and received an error saying I had to run a string to fix some error, ran it.
Turns out it didnt finish updating, applied updates, restarted and it was all working.

---

