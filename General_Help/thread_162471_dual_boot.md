---
title: "dual boot"
date: 2006-04-19
forum: General Help
---

### Post by frizzl on 2006-04-19
well im running ubuntu and windows xp (both 64 bit) and its all fine.

i edited the mbr or grub menu (not sure what correct name is) to display just the two (doesnt include all the other ubuntu options, like memtest etc)

but how do i make windows the DEFAULT boot?

thanks :D

---

### Post by Sutekh on 2006-04-19
Look for the line in the GRUB menu **/boot/grub/menu.lst** that looks like this
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
**default         0**

```
Start counting up from 0 everytime you see a line that contains **title**. 

Some examples are
```
title       Ubuntu, etc
```
```
title       Other operating systems:
```
```
title       Windows XP
```

When you reach Windows then change the default line to the number you counted too.

---

