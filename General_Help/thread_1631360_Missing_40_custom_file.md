---
title: "Missing 40_custom file"
date: 2010-11-26
forum: General Help
---

### Post by elMaVacano on 2010-11-26
I have a dual boot system with Windows 7 and Ubuntu 10.04 and have been been playing around with GRUB2 in order to customize the boot menu (background image, less menu item, etc). I've been successful in doing some things but  my 40_custom file in my grub.d folder is missing! Here is what happens when I try to update my grub:

euri@euri-HP-6730b-FN021UT-ABA:~$ sudo update-grub
[sudo] password for euri: 
Generating grub.cfg ...
using custom appearance settings
/etc/grub.d/40_custom: 2: menuentry: not found
/etc/grub.d/40_custom: 3: recordfail: not found
insmod: can't read 'part_msdos': No such file or directory
insmod: can't read 'ext2': No such file or directory
/etc/grub.d/40_custom: 7: search: not found
/etc/grub.d/40_custom: 8: linux: not found
/etc/grub.d/40_custom: 9: initrd: not found
/etc/grub.d/40_custom: 10: Syntax error: "}" unexpected

---

### Post by oldfred on 2010-11-26
Welcome to the forums.

It does not look like it is missing but has an invalid boot stanza.

My 40_custom before any editing:

```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

```

Copy & post your 40_custom

gksudo gedit /etc/grub.d/40_custom

---

### Post by elMaVacano on 2010-11-26
Thank you, it's always the simple fixes that take me the most time before I give up and ask someone for help! :)

---

