---
title: "Help! Can't resume after memory upgrade"
date: 2006-03-29
forum: General Help
---

### Post by kellyschrock on 2006-03-29
Hi,

I'm running Breezy on an HP Pavilion zt3000 notebook, and up until last Friday, it worked great. I take this notebook everywhere, and have it configured to hibernate when I shut the lid. Friday, I upgraded the RAM from 768MB to 1GB. Now, when I try to resume after a hibernate, I get these messages:

resume= option should be used to set suspend device
swsusp: Need to copy (n) pages

where "(n)" is some large-ish number in the 11000 to 19000 range.

At that point, the boot process stops, and I basically have to power it off and reboot. 

Any idea what I need to do to fix this?

---

### Post by play0r on 2006-03-29
you may want to make a post in this forum:
[http://www.x1000forums.com/](http://www.x1000forums.com/)

they are the "unoffical" forum to discuss topics for several types of compaq & hp notebooks, including yours.
sorry that i couldn't do anything more helpful other than linking you to **another** forum. :(  

good luck,
play0r

---

### Post by kellyschrock on 2006-03-29
[QUOTE=play0r]you may want to make a post in this forum:
[http://www.x1000forums.com/](http://www.x1000forums.com/)

they are the "unoffical" forum to discuss topics for several types of compaq & hp notebooks, including yours.
sorry that i couldn't do anything more helpful other than linking you to **another** forum. :(  

good luck,
play0r[/QUOTE]
Not a problem, thanks, I'll check it out.

---

### Post by trent dillman on 2006-03-29
Are you suspending to swap? Your swap might not be big enough...

---

### Post by kellyschrock on 2006-03-29
Dunno... How do I tell what I'm suspending to?

---

### Post by trent dillman on 2006-03-30
```
cat /etc/fstab | grep swap
```

This will tell you what /dev/hd* your swap is on. Then add 

```
resume2=swap:/dev/hd*
``` as an option to your kernel in /boot/grub/menu.lst, replacing /dev/hd* with the device listed in the first command.

---

