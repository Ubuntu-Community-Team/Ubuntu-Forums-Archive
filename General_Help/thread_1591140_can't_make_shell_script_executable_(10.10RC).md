---
title: "can't make shell script executable (10.10RC)"
date: 2010-10-08
forum: General Help
---

### Post by tacticalbread on 2010-10-08
I'm trying to make a simple autorun script, for my Micro SD Card, the script works fine, but I simply cannot make it executable.

When I check the "Allow executing file as program" check box, it just automatically unchecks itself immediately. Chmod'ing it does nothing (I assume is resets behind the scenes as well). Nothing is different as a super user either.

The script runs fine when run locally (not on my SD card), and when run like
```
bash ./autorun
```
but
```
./autorun
```
yells at me. (bash: ./autorun: Permission denied)

It refuses to become executable.

Am I doing something wrong here? This is driving me completely and utterly mad.

---

### Post by mc4man on 2010-10-08
Probably related to this (though there is another possibility.
To resolve a bug in udisks this patch was added - applies to vfat filesystems on removable media

 > Add 00git-vfat-showexec.patch: Enable the "showexec" vfat mount option, to
    avoid data files being executable (which causes confusing question dialogs
    in nautilus which only have one sensible answer). Patch taken from
    upstream git head. (LP: #14335)

The patch can be reverted in a custom udisk build - if this is your issue

---

### Post by tacticalbread on 2010-10-09
That sounds like it would do it.

So I'd have to edit, and compile it from source then?

I'm not much of a programmer. :/

---

### Post by meadhikari on 2010-12-01
Exactly the same problem here.
Could not understand the above solution.
Please can anybody help me on this.

---

