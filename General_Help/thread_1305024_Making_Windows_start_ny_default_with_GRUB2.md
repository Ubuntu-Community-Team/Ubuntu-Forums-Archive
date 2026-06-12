---
title: "Making Windows start ny default with GRUB2"
date: 2009-10-29
forum: General Help
---

### Post by UnBr34KaBl3 on 2009-10-29
Ok so I installed Ubuntu 9.10 as my secondary OS (gaming+ubuntu = no) and I want windows to start first but this new GRUB2 is killing me. I've read some posts about it and I can't understand this script generated new menu.lst thing. What should I do to make windows start first? Thats the only thing I want to know so please don't link to those guides going over overything about GRUB2 unless there is a special section för how to fix this.

Thank you!

---

### Post by Brandon Williams on 2009-10-30
You can find some information about this specific question [here](http://ubuntuforums.org/showthread.php?p=8192085) and [here](https://answers.launchpad.net/ubuntu/+source/grub/+question/81959).

If windows is showing up correctly in your boot menu, you will modify a value in /etc/default/grub and then run update-grub. If windows is not in your boot menu, it will be more involved.

---

