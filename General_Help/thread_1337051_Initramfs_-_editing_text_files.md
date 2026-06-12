---
title: "Initramfs - editing text files?"
date: 2009-11-25
forum: General Help
---

### Post by sdaau on 2009-11-25
Hi all, 

Sometimes I have a problem, where 9.10 Karmic drops me to a initramfs shell, and I need to edit /boot/grub/menu.lst to fix this problem. I can mount the disk manually without a problem, and navigate to this file - however, I get ```
command not found
``` for **nano**, **pico** or **vi**. 

I guess I should have tried calling "/usr/bin/nano" from the same drive where /boot/grub/menu.lst is (once it is mounted) - but apart from this, is there a text editor "built in" in initramfs?

Thanks, 
Cheers!

---

### Post by syuzh on 2010-07-05
Busybox / initramfs
I would like to know too. There doesn't seem to be anything available. This is really annoying.

---

