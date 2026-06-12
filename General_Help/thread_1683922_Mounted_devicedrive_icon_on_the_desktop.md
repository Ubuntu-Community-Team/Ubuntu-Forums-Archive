---
title: "Mounted device/drive icon on the desktop"
date: 2011-02-08
forum: General Help
---

### Post by wiktor00 on 2011-02-08
Hello,

I've some icons of mounted devices on my desktop. I want to display only some of them which I need. All drives are mounted automatically while booting or by scripts while logging in.

For example:
I've 4 mounted devices and 4 icons on my desktop and I want to have 4 mounted devices but only 2 icons.

There is possibility of hiding all of icons in gconf, but I want to hide only some of them.
Is it possible?

---

### Post by ajgreeny on 2011-02-08
The only way I know of is to mount the ones you want to show in **/media** and those you want to be invisible in **/mnt** (or anywhere else).  The disadvantage of that is that they will not show in Places either, but that may be quite acceptable to you.

I think I have read of other ways to do it at some time in the past, but suspect that it will be a lot more complicated.

---

### Post by vanadium on 2011-02-08
You could also mount everything under /mnt, then create shortcuts on the desktops to those you want to see on the desktop. Also for the places menu, it is simply a matter of adding shortcuts yourself.

---

### Post by BHEJU on 2011-02-08
I remember seeing configuration parameter in Ubuntu Tweak software. It might be of help.

Cheers :>

---

### Post by wiktor00 on 2011-02-08
Mounting in /mnt
The simplest solution is the best one.
I've not even think about this, I searched something about scripts etc.

Thanks a lot.

P.S. @BHEJU Ubuntu Tweak don't have option like this it has only hiding **all** devices and drives. And Ubuntu Tweak set this in gconf.

---

