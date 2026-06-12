---
title: "GRUB BLUES: New Lunux image whacks menu.lst"
date: 2006-03-29
forum: General Help
---

### Post by TmP on 2006-03-29
Hi!

I run a dual boot desktop with Ubuntu as the serious system and Windows as a tv. Every time a new linux core image gets updated, the menu.lst gets deleted and reverts to default. It's annoying to add the TV setting into the menu.lst every time an update occurs. 

Do you know a workaround for this problem? Thanx!

And on a side note:
I keep using winblows, because I can't set up my tvcard in Ubuntu.
Oh, it's supported all right. By MythTV. The only problem is that for some unnown reason, MySQL won't work on my system. I tried to fix it for a few weeks and than gave up. The Wiki wasn't any help at all and nothing suggested on the forums worked. Ill be reinstalling my Ubuntu. Do you think it'll fix the problem?

---

### Post by dcstar on 2006-03-29
[QUOTE=TmP]Hi!

I run a dual boot desktop with Ubuntu as the serious system and Windows as a tv. Every time a new linux core image gets updated, the menu.lst gets deleted and reverts to default. It's annoying to add the TV setting into the menu.lst every time an update occurs. 
.......[/QUOTE]
Assuming you are talking about your Windows boot setting, simply place them after the lines that say:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
```
Then they are not touched by kernel upgrades.

---

### Post by TmP on 2006-03-29
[QUOTE=dcstar]Assuming you are talking about your Windows boot setting, simply place them after the lines that say:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
```
Then they are not touched by kernel upgrades.[/QUOTE]

Thanx, but will it be possible to place it in front of the Ubuntu as the first startup choice? (Please don't ban me- my girlfriend is edgy about linux)
I still want the images to be updated in the menu.lst, but my TV , ehem Windows, needs to start automaically unless i choose otherwise. ( I will , I promise!)

---

### Post by Gustav on 2006-03-29
Just change the default entry (it should be somewere in the beginning of the menu.lst file) to the number of your windows partition. There is probably an explaining text in the file, but in case there isn't I'll paste my test here :)
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
```

---

