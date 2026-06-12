---
title: "LXappearance too aggressive?"
date: 2012-09-30
forum: General Help
---

### Post by ohnonot on 2012-09-30
hello everybody,

i have a problem with lxappearance - it makes changes, immediately, very effective. but i like to make my own customizations in ~/.gtkrc-2.0, and they get overwritten all the time. well, long story short, i don't want to use lxappearance anymore, uninstalled it, but it changed my mouse pointer and i can't change it back anymore so obviously it changes sth else besides gtkrc. where and what?

thanks for reading.
grateful for help.


ps: i have noticed this before, with lxde/openbox or xfce4, not quite sure, and now it's happening again in a windowmaker session. changing the mousecursor with update-alternatives works, i can see it when i log out, but as soon as i log in it changes again to what lxappearance made it.

---

### Post by TheFu on 2012-09-30
I don't have an answer, but I do have a method to figure out what is happening.

* Install lxappearance
* Take a backup of everything in your $HOME
* Use lxappearance to modify the mouse cursor.
* Compare all the files in the current HOME to your backup.

Now you know all the files that were touched and what changed inside each.

* remove lxappearance
* manually remove those changes
* logout
* login
If you did everything right, that should be it.  The real world is usually more complicated.  You might need to create a new user account with completely stock settings to do this stuff again. 
Do not manually change anything in those settings before you do the comparison.  OTOH, if you do, just create a new-new account and start over.

---

### Post by ohnonot on 2012-10-01
hm. thanks, i have to keep this in mind as a last resort for troubleshooting.

but before i do so, does anybody know *which files are changed* by lxappearance?

i read somewhere that "all currently running applications are asked to reload their settings" and since lxappearance prouds itself to be a "desktop-independent GTK+ theme switcher" - it's a mistery because window maker is not gtk and afaik i have no session manager running.

---

### Post by TheFu on 2012-10-01
> **ohnonot said:**
> hm. thanks, i have to keep this in mind as a last resort for troubleshooting.

but before i do so, does anybody know *which files are changed* by lxappearance?

i read somewhere that "all currently running applications are asked to reload their settings" and since lxappearance prouds itself to be a "desktop-independent GTK+ theme switcher" - it's a mistery because window maker is not gtk and afaik i have no session manager running.

So your next question is "how do I find a list of changed files?"
```
man find
``` will explain everything.
You'll want something like 
```
$ find ~/ -type f -mtime -1
```
Those steps really aren't very hard.

---

