---
title: "My Ubuntu 12.04 floppy drive problem~"
date: 2012-09-19
forum: General Help
---

### Post by cousinlucky on 2012-09-19
My computer's floppy drive works with other distros but not Ubuntu 12.04.
I put in the floppy and detect it; but it will not mount. Can anyone help me with this please?

---

### Post by oldfred on 2012-09-19
Some suggest manually mounting it in command line.

[http://ubuntuforums.org/showthread.php?t=1877488](http://ubuntuforums.org/showthread.php?t=1877488)
[http://ubuntuforums.org/showthread.php?p=11244050#post11244050](http://ubuntuforums.org/showthread.php?p=11244050#post11244050) post #2 coffeecat
Mount floppy from command line - Nautilus often does not work
udisks --mount /dev/fd0
ls /dev/fd*
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

---

### Post by cousinlucky on 2012-09-19
Thank You Oldfred!

---

