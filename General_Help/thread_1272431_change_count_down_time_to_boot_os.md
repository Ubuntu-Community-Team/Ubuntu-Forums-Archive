---
title: "change count down time to boot os"
date: 2009-09-22
forum: General Help
---

### Post by missmoondog on 2009-09-22
how do i change that amount of time before the operating system loads?

default is 30 seconds!! i want to use the computer today, not tomorrow!!

what's the command and the whole nine yards?

thank you

not a very good search engine on this forum. been looking for an answer all morning already and have found almost everything else i need except this!!

---

### Post by zwanzig on 2009-09-22
in the file /boot/grub/menu.lst
change:
```
timeout         30
```
to whatever time you whish.

---

### Post by ajgreeny on 2009-09-22
> Not a very good search engine on this forum. been looking for an answer all morning already and have found almost everything else i need except this!!
I agree with your comment, but it's a problem with most forum searches, I find.  One way to get better results is to just use google, but limit the search to this forum with ```
grub boot time site:ubuntuforums.org
```as you search terms.  Much better way to find entries in here, as far as I can see.

---

### Post by missmoondog on 2009-09-22
> **zwanzig said:**
> in the file /boot/grub/menu.lst
change:
```
timeout         30
```
to whatever time you whish.


i was able to find that info searching, but now that leads me to my real question.

i do not have 30 in my list. it's a 3. i changed it to 1 once already, and then got stuck in a loop rebooting xubuntu.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		6

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3



added so i don't forget:
sudo gedit /boot/grub/menu.lst

---

### Post by missmoondog on 2009-09-22
duh!!

in windows,
right click my computer, properties, advanced, start up & recovery!! that didn't use to work that way, did it?

that must've been a benefit of using wubi?

---

