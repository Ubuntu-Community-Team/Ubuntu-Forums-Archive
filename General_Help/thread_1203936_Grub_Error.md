---
title: "Grub Error"
date: 2009-07-04
forum: General Help
---

### Post by dave collin on 2009-07-04
Hi,
Just shutdown and then restarted. Didn't load - showed a very colourful ASUS splash screen (never seen before?) and said:
GRUB HARD DISC ERROR
This is not good.
Whilst sweating profusely, I held power switch down 'till rebooted and then loaded OK. (I'm using it right now).
Is this indicative of anything?
Is there a disc check program out there that I can use to check for disc errors?

---

### Post by QIII on 2009-07-04
Give us a peek at the results of 

fdisk -l

and the menu.lst

---

### Post by mamali on 2009-07-04
you can install your grub again like this:
put ubuntu live cd and boot from that then open a terminal and enter :
```
sudo grub
```
```
find /boot/grub/stage1
```
This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)
```
root (hd?,?)
```
and finally :
```
setup (hd0)
```
to quit the grub enter :
```
quit 
```
then restart your computer

---

### Post by synapsys on 2009-07-04
```
badblocks
```

To check for disk errors

```
fsck
```

To check for filesystem errors

I suggest reading the man pages before using either.

---

