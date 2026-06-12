---
title: "dual boot timer question"
date: 2009-08-05
forum: General Help
---

### Post by isee on 2009-08-05
Can I eliminate the 10 second timer on a dual boot desktop?  I would like to be able to turn my computer on and leave it for a few minutes without it booting into the latest kernel automatically after 10 seconds.

Thanks a bunch!

---

### Post by realzippy on 2009-08-05
In a terminal type:

**sudo gedit /boot/grub/menu.lst**

watch out for the line

timeout		10

..here you go;save the file after changing..

..if you set a "#" at the beginning of that line it will be ignored..

---

### Post by Marlonsm on 2009-08-05
There are many ways to do this, this one is the easiest I know:

Open the terminal (Applications > Accesories)
Run this:
```
sudo gedit /boot/grub/menu.lst
```
And put the root password
It will open the grub configuration file, its the first part should look like this:
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		1

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**timeout		10**

```

The part you need to change is the "timeout" line
The default is 10 (seconds), just change it to the value you want, for example, if you want 5 minutes, change the value to 300.
Save, and it's done

---

### Post by Hobgoblin on 2009-08-05
By far the easiest way is to install startup manager which gives you a graphical front end to all those settings.

---

### Post by isee on 2009-08-14
Thanks everyone for taking the time to inform me of both methods!  Explained everything.

:P

---

