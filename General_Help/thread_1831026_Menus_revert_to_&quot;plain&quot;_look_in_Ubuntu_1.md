---
title: "Menus revert to &quot;plain&quot; look in Ubuntu 11.04 with Virtualbox"
date: 2011-08-22
forum: General Help
---

### Post by joshma on 2011-08-22
Hi all, I recently installed Ubuntu 11.04 in Virtualbox, and now when I sign in the menus look "normal" (i.e. not Unity but still the dark gradient theme.)

They then flash and change to this gray flat look that resembles Windows classic:
[IMG]http://i.imgur.com/OFHuz.png[/IMG]

I've tried enabling 3D acceleration - that gets me Unity, but then it still shows the gray menus.

Any help with this would be much appreciated!

---

### Post by joshma on 2011-08-22
Bump :(

---

### Post by apacketofsweets on 2011-08-22
The only thing I can think of is for you to fiddle around with Ubuntu's appearance settings. What's happened is, somehow something has triggered Ubuntu's minimal graphical settings, it could possibly be a reaction to a certain piece of hardware which Ubuntu thinks it needs to run minimal settings for. Although as you're using Virtual Box, it's probably a reaction to VB's virtual hardware settings.

---

### Post by drewsus on 2011-08-22
And this is consistent even after rebooting the virtual machine?

---

### Post by apacketofsweets on 2011-08-23
I assume so, otherwise he wouldn't have a problem.

---

### Post by chindichor on 2011-09-22
I am suffering from the same issue. Any help appreciated.

---

### Post by chindichor on 2011-09-22
Running this 

```
killall -9 gnome-settings-daemon && gnome-settings-daemon
```

gives the trendy look back, but I have to run it every time I start the machine. [See here for the discussion]("http://forums.virtualbox.org/viewtopic.php?f=7&t=41548").

---

