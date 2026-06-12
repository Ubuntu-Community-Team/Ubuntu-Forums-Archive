---
title: "Wipe your pc hard drive with ubuntu live disk."
date: 2010-08-02
forum: General Help
---

### Post by erikkwonke2 on 2010-08-02
I thoght this can help with any one who want to sell there computer with important information. For more information go to the link [http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)

---

### Post by giddyup306 on 2010-08-02
> **erikkwonke2 said:**
> I thoght this can help with any one who want to sell there computer with important information. For more information go to the link [http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/](http://www.howtogeek.com/howto/15037/use-an-ubuntu-live-cd-to-securely-wipe-your-pcs-hard-drive/)

  Using the shred function will take forever.  You're better off using DBAN.    I made my own tutorial a couple days ago.  [http://www.ricehatersclub.com/vbulletin/showthread.php?t=31072](http://www.ricehatersclub.com/vbulletin/showthread.php?t=31072)

---

### Post by erikkwonke2 on 2010-08-02
ok Thanks for the info

---

### Post by linux18 on 2010-08-02
from a live disk:

format the hdd then run
dd if=/dev/urandom of=/dev/sda bs=1M

when the hard disk runs out of space your done

---

### Post by yetiman64 on 2010-08-02
> **giddyup306 said:**
> Using the shred function will take forever....

Shred used to do 25 passes by default, however now in Lucid the default is only 3 passes.

From ```
man shred
```,> -n, --iterations=N
              overwrite N times instead of the default (3), doesn't take too long now. I even use iterations=1 (or if in a real hurry 0) and use the "zero" switch, --zero, to reset all bits on the drive to 0 (very quick).
Good thing is that a whole drive or an individual partition can be reset easily just with using the live cd.

Obviously, the more sensitive your data the higher you can set iterations to.

dd is also a very handy tool to use off a live cd.

---

