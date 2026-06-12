---
title: "ubuntu wont start after update"
date: 2010-12-03
forum: General Help
---

### Post by JackRussel on 2010-12-03
I have ubuntu 10.04 lucid with the kde desktop.  While using ubuntu I received a message stating that the system needed to be restarted.  I restarted and when I selected ubunto from the boot menu the computer restarted.  Ubuntu will not load, the computer just keeps restarting.  Everything was working fine until the update asked me to restart the system.  Any one know how to resolve this issue?

I have Windows XP sp3, ubuntu 10.04, 32bit system

---

### Post by Verbeck on 2010-12-03
is it a wubi install or a partitioned dualboot?

try choosing the older kernel version from the boot menu if its there

---

### Post by bcbc on 2010-12-03
Check this link out: [http://ubuntuforums.org/showpost.php?p=10183394&postcount=87](http://ubuntuforums.org/showpost.php?p=10183394&postcount=87)

Basically 10.04 Wubi installs will fail if you upgrade the grub-pc and grub-common packages. The link describes the issue, workaround and manual fix.

---

### Post by JackRussel on 2010-12-03
It is Wubi install.
I noticed that a message is displayed for a brief moment stating that the system can not find a file.  The message does display long enough for me to read the file name.

---

