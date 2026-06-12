---
title: "How to make grub NOT use UUID?"
date: 2010-06-08
forum: General Help
---

### Post by ansiktsburk on 2010-06-08
Hello.
How can I make grub not use UUID but /dev/sda1 instead?
I seem to have problem finding discs based on uuid after booting and so I have removed uuids from fstab and marked /dev/sda1 as /.

What should I do in the grub config files and what commands to run?

---

### Post by oldfred on 2010-06-08
UUID's are supposed to be more reliable as they will not change unless you delete or greatly modify a partition. sda may change with partition changes. You also can use labels.

This shows how to modify grub's script.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

