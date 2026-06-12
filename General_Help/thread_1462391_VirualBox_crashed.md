---
title: "VirualBox crashed"
date: 2010-04-25
forum: General Help
---

### Post by Flexico on 2010-04-25
OK, yesterday I was using VBox and a couple other applications at the same time, when SOMETHING happened. I don't know what it was, but suddenly the running apps stopped working. Firefox lost all my bookmarks and couldn't remember cookies long enough to even let me log in, aMSN kept sending me weird error messages, CompizConfig settings all disappeared, and my Windows XP in VBox shut down and then said that the WinXP machine was "inaccessable". I rebooted a couple of times and everything else somehow managed to restore themselves, except VBox. Now when I try to run it I just get the error box in the attached image. Really, I just want to get some lost data off of the virtual HD and then be done with VBox, is there a way to mount the "VDI" file?

---

### Post by garyedwardjohnston on 2010-04-25
looks complicated but there are ways posted in the vbox forums

also try:

[http://linux.softpedia.com/get/System/System-Administration/mount-vdi-47415.shtml](http://linux.softpedia.com/get/System/System-Administration/mount-vdi-47415.shtml)

---

### Post by geirha on 2010-04-25
Sounds like you might have run out of diskspace on /home.

Does this happen to show near 100% disk-usage?
```
df -h ~
```

It could also be some of the config-files for several applications were removed while the applications were running. Odd things may happen then.

---

