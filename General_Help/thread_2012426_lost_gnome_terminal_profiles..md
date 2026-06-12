---
title: "lost gnome terminal profiles."
date: 2012-06-29
forum: General Help
---

### Post by F.G. on 2012-06-29
Hi everyone,

i had about eight gnome terminal profiles setup, and attached to hotkeys. these profile are something i use all the time, with distinct colours and commands, ssh-ing them to different machines.

yesterday i added a another monitor (by that i mean display/lcd screen) to my setup, restarted my computer and now none of my profiles are there?

if anyone has any idea why this might be i'd be very gratefull to get them back/not have this happen again (particularly as some of the commands are quite long, chained, ssh commands with specific options).

thanks for all and any help.

---

### Post by Habitual on 2012-06-29
anything at ~/.gconf/apps/gnome-terminal/profiles/ ?

Try terminal > 
```
ls -ld .gconf/apps/gnome-terminal/profiles/*
```

and show us the output please.

---

### Post by F.G. on 2012-06-29
hi Habitual, 

thanks for the quick reply, yes, they are there (i think). though i have reset my profile now, some most of them are overwritten, there are definitely some of the old ones.
still wondering why they disappeared in the first place, but if it happens again, i'll know where to look.

---

### Post by F.G. on 2012-07-12
bounce...

so, this just happened again, and is really annoying. last time the profile entries in the global config file were missing. this time two of the .gconf/apps/gnome-terminal/profiles/*
files are completely empty and one is corrupted, and only has three lines in.

done know if this is some kind of hardware faliure, maybe. though if not id really like to sort it out. another xml config file also got wiped , the VirtualBox config one , twice. thankfully it automatically saves a '-prev' version, so i just copied that each time. anyway, i'm rapidly losing losing faith in my home directory and a local configs. so if anyone can shed any light on this i'd be most grateful.

thanks for all and any replies.

ps. i forgot to give the output of that command last time,so here are the first few, the rest are the same (i don't feel that i can post usernames and owners etc, so they are 'x'ed out):

```
drwx------ 2 xxxxx xxxxx 4096 2012-07-11 14:49 .gconf/apps/gnome-terminal/profiles/Default
-rw------- 1 xxxxx xxxxx    0 2011-12-22 12:39 .gconf/apps/gnome-terminal/profiles/%gconf.xml
drwx------ 2 xxxxx xxxxx 4096 2012-07-12 10:22 .gconf/apps/gnome-terminal/profiles/Profile0

```

---

