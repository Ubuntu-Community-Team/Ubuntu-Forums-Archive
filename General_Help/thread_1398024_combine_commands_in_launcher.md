---
title: "combine commands in launcher"
date: 2010-02-04
forum: General Help
---

### Post by chaopoch on 2010-02-04
I would like to create a launcher that will open a terminal to execute the following three commands, and after that the terminal will close automatically, so how to combine these commands to make it? thanks for help

gksu
cd /usr/share/xxx
svn update


PS: I have tried the following methods, but none works,

1. gksu cd /usr/share/xxx && svn update
2. cd /usr/share/xxx && gksu svn update
3. I create a script s.sh like this

#! /bin/sh
cd /usr/share/xxx
svn update

and put command 'gksu sh /usr/share/xxx/s.sh' (without quotes) in launcher

---

### Post by Leppie on 2010-02-04
it should be possible to use the script for the launcher, however:
- gksu is used to launch graphical applications (it's the graphical counterpart of su like gksudo is the graphical counterpart of sudo), so i would use sudo as you aren't launching anything graphical.
- gksu, gksudo, su and sudo usually all require a password to be entered unless you create an entry in the sudoers file for the to be executed command/script

hope this helps

---

### Post by chaopoch on 2010-02-04
> **Leppie said:**
> it should be possible to use the script for the launcher, however:
- gksu is used to launch graphical applications (it's the graphical counterpart of su like gksudo is the graphical counterpart of sudo), so i would use sudo as you aren't launching anything graphical.
- gksu, gksudo, su and sudo usually all require a password to be entered unless you create an entry in the sudoers file for the to be executed command/script

hope this helps

Thanks for the detailed explanation.

If I use the script for the launcher, so what is the combine command for the launcher to open a terminal to execute the script?

---

### Post by Leppie on 2010-02-04
> **chaopoch said:**
> Thanks for the detailed explanation.

If I use the script for the launcher, so what is the combine command for the launcher to open a terminal to execute the script?
i think i would use something like this:
```
/usr/share/xxx/s.sh
```

and use sudo for the svn update, not the whole script.

---

