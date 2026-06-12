---
title: "Finding mystery command I didn't put in!"
date: 2012-02-26
forum: General Help
---

### Post by crazybear on 2012-02-26
I'm rather new to Linux and Ubuntu - like it very much, but still don't understand how to do [or undo] many things - very steep learning curve! I had a friend who was a lifelong expert - too much of an expert - when he came over and did things he did them so quickly, I couldn't follow and he didn't much explain. I once asked him to make a second drive recognized by my main drive as the 'backup' [we named it Ubuntucopy]. I now want to do backups another way. When that second drive is not in the computer at boot I'm asked to skip mounting it or manually mount it. Also, when hunting around, I found that he had created a folder in my first drive called Ubuntucopy, which contains a copy [?] of my other set of Ubuntu files. Try as I might, I can't locate the command he put in - let alone know how to undo all this. Thanks for any pointers. While it is possible to bypass both, the first takes time and is annoying; the second is taking up huge amount of disk space - I back up elsewhere. :confused:

NB - apparently, my friend has died or moved away or changed his email. I can not locate him now for many months.

---

### Post by WorMzy on 2012-02-26
Could be a mount, so check /etc/fstab for any references to that folder

or

it could just be a symlink, in which case check with ```
ls -l /path/to/folder
```

---

### Post by crazybear on 2012-02-26
> **WorMzy said:**
> Could be a mount, so check /etc/fstab for any references to that folder

or

it could just be a symlink, in which case check with ```
ls -l /path/to/folder
```

Thanks, but no...first folder doesn't exist and second pulls up nothing. I remember him trying to think of some 'interesting' folder to put it in - out of the ordinary.... I can scan for all references to 'ubuntucopy' but that brings up tens of thousands of entries. How do I limit the search for instructions and NOT files?! I can't even delete the folder by that name. It simple deletes and then is rebuilt. :confused:

---

### Post by dragonfly41 on 2012-02-26
**[COLOR=DarkGreen]$ sudo history[/COLOR]**

this should give a history of terminal commands used.

---

### Post by crazybear on 2012-02-27
> **dragonfly41 said:**
> **[COLOR=DarkGreen]$ sudo history[/COLOR]**

this should give a history of terminal commands used.


**sudo: history: command not found**
 
I also tried history ubuntucopy 
history !ubuntocopy 
and other varients
- nothing

????????:confused: The man history command gives a HUGE array of ? commands/comments/explanations that are Greek to me!

---

### Post by dragonfly41 on 2012-02-27
> sudo: history: command not found

Sorry .. it should simply be "history" .. no "sudo" in front.

---

