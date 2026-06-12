---
title: "How work grub???"
date: 2009-07-28
forum: General Help
---

### Post by miros84 on 2009-07-28
Hello
When I type 

title Windows XP (Loader)
root (hd1,4)
chainloader +1

in menu.lst
what file is looking grub? Is looking for boot.ini or is looking for ntloader? I just want to know the funcction of grub and booting windows.

---

### Post by bernied on 2009-07-28
I think it works something like this:

When grub uses the chainloader command, it loads the first sector (the boot sector) of the partition you've pointed it to. So it's the contents of this sector that determines which file is then loaded to continue the boot sequence. It's not up to grub.

[http://www.gnu.org/software/grub/manual/grub.html#chainloader](http://www.gnu.org/software/grub/manual/grub.html#chainloader)

---

