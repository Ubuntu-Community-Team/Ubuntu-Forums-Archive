---
title: "permissions help??"
date: 2010-03-21
forum: General Help
---

### Post by melinda on 2010-03-21
original user (administrator) named green had some issues with Places Menu.  Just decided to create a new user w/ administrator rights (lets call it white).  then created a third user also administrator (lets call it blue).  Under blue I opened terminal, sudo nautilus, and copied the green home folder contents (music/pictures/etc) over to user white.  
**Problem:**  When log out blue user login white user, the permissions are locked as owner and group is root (since I created under sudo nautilus). Logged out white, logged in blue and again opened terminal, sudo nautilus, file system/home/white...  I right clicked on the various folders (desktop, music, pictures, etc/et all), then properties, and under permissions tab changed owner and group to white, then clicked to apply permissions to enclosed files.  Logged out blue, login white. **Problem: ** when I open the sub folders/files under white home foler they are still locked as not the owner- no permission.  If I go back and do it all over but clicking on every single individual file and set permissions as white then it works.  WTF?  isn't there a way under sudo nautilus (superuser) that you can set permissions for ALL sub folders and files under white as permissions for white **without** having to change every file by file?  (the green user from which the files were copied into white have a LOT of pics and music)??

Please help asap. 

Thanks
Mel's sister Heather

---

### Post by phen0m on 2010-03-21
It should work through Nautilus, but this should do what you want.  

Removed for inaccuracy.

---

### Post by melinda on 2010-03-21
phen0m:  Thanks but here's what I got back

blue@White:~$ chown -R white:\ /home/white
chown: missing operand after 'white: /home/white'
Try 'chown --help' for more information.
blue@White:~$

---

### Post by melinda on 2010-03-21
oh ps..

i did put a space between the \ /

---

### Post by melinda on 2010-03-21
btw:

When I use code: sudo nautilus and enter password..I get this after. 
**What does it mean?**
 (nautilus:4390): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
**What does it mean?**

---

### Post by phen0m on 2010-03-21
Sorry, usually the tab key fills that in for me.  Not used to typing it ;)

```
sudo chown -R white\: /home/white/
```

---

### Post by melinda on 2010-03-21
I LOVE YOU **phen0m**!

Thanks a million!

---

