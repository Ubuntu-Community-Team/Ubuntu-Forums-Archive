---
title: "How can you edit the menu.lst file?"
date: 2010-04-23
forum: General Help
---

### Post by ucjb on 2010-04-23
I have a bad menu.lst file. When booting grub responds "Error 15: File not found". I am running a software raid 5. I believe I must mount the raid from a live CD as to be able to edit the file or manaully enter the parameters in the grub cli so I can boot and edit the file. Ths original menu.lst was rename to menu.lst.old

I'm running 9.10 just upgraded from 9.04

Do any of you gurus know how I can do this?](*,)

---

### Post by sunk8 on 2010-04-23
This is the best tutorial for grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

did you try to restore grub using a live cd?
open nautilus as root; rename *menu.lst* to *menu.lst.try* and *menu.lst.old* to *menu.lst*
?

---

### Post by ucjb on 2010-04-23
Wouldn't the raid or at least the /boot have to be mounted first?

---

### Post by ucjb on 2010-04-23
Thanks for the help. I got the /boot mounted with the live cd then renamed the files... all is well:popcorn:

TGIF!

---

### Post by sunk8 on 2010-04-23
Well, if your problem's solved, Plz mark this thread as [Solved]...
:guitar:

---

