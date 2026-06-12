---
title: "is this normal? (boot.log) ureadahead..."
date: 2010-09-10
forum: General Help
---

### Post by dek8 on 2010-09-10
i had a couple of things popping up during bootup and checked my boot.log and found this

```
[COLOR="Red"][COLOR="Red"][COLOR="Black"]
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2

udevd[416]: can not read '/etc/udev/rules.d/z80_user.rules'

fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2

File_System: clean, 86937/1128288 files, 451132/4505856 blocks

init: ureadahead-other main process (759) terminated with status 4
init: ureadahead-other main process (802) terminated with status 4
init: ureadahead-other main process (888) terminated with status 4

 * Starting AppArmor profiles [80G Skipping profile in
/etc/apparmor.d/disable: usr.bin.firefox

[74G[ OK ]
[/COLOR][/COLOR][/COLOR]
```



is this normal? Anyone knows what its about?

10.04 Server 32bit

---

### Post by andrewthomas on 2010-09-10
What is in the file?

```
cat /etc/udev/rules.d/z80_user.rules
```

---

### Post by dek8 on 2010-09-10
nothing... empty file

---

### Post by ranch hand on 2010-09-10
You might be interested in this from the Lucid testing forum;

[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

---

