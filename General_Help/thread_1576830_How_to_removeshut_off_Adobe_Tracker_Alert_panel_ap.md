---
title: "How to remove/shut off Adobe Tracker Alert panel applet??"
date: 2010-09-17
forum: General Help
---

### Post by Matt 6:27 on 2010-09-17
Anybody out there have a tip on how to remove or shut off the Adobe Tracker Alert applet from a panel short of removing acroread altogether??  I'm using the latest version of acroread (ver. 9.3.4-1lucid1) from the repos.  Have run it for a week or so and got a pop-up re an update.  I (stupidly) approved the upgrade and the tracker immediately appeared.  There is no intuitive way in which to shut it off.  Any guidance would be appreciated.

---

### Post by jimstar79 on 2010-12-03
Have exactly the same problem. removed adobe reader but the stupid little yellow thing remains in the panel!!

really annoying - still cant find a way to kill it!

edit: gone after restart but haven't fired up any adobe apps yet

---

### Post by mariaro on 2011-02-02
I have the same problem here. Even if I removed and purged acroread the tracker icon is still there... any idea about how to remove it?
It's really annoying...

---

### Post by protargol on 2011-02-04
So I couldn't find the process using pgrep, but I did a ps -ef and found ```
/lib/ld-linux.so.2 /opt/Adobe/Re
```.  The rest was cut off up I'm guessing it was Reader something.  Anyways, I killed that process and it disappeared.  No idea what it does so maybe there are repercussions so do at your own risk.  BUT so far it solved my problem.

Also, is there a way to disable it for in the future?

---

### Post by philsalkie on 2011-08-05
I moved the tracker binary to a different name, seemed to solve the problem:

```

$ cd /opt/Adobe/Reader9/Reader/intellinux/bin/
$ sudo mv SynchronizerApp-binary SynchronizerApp-binary-hold
```

Then I found the leftover tracker process and killed it:

```

$ ps axw

...

32458 ?        Sl     0:00 /lib/ld-linux.so.2 /opt/Adobe/Reader9/Reader/intellinux/bin/SynchronizerApp-binary -c

$ kill -9 32458

```

All better - now to remember to do that after each Reader upgrade...

---

### Post by pearl298 on 2012-12-13
I used a skightly different approach to "defang" the binary:

sudo chmod -x Synchronizer*


Now it will update, but not run!

---

### Post by oldos2er on 2012-12-13
Old thread closed.

---

