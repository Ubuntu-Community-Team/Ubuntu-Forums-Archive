---
title: "metacity setup?"
date: 2010-09-20
forum: General Help
---

### Post by soryu on 2010-09-20
how do i set up metacity?
my borders don't show up at start up.
i removed compiz and nvidia drivers.adding metacity --replace& command at start up works. but  know that it's not the correct way.

the  metacity --replace& command works but i still lose the borders after closing the terminal and cannot open the terminal again.(weird)
 using ALT&F2  works but not after restarting.
i reinstalled metacity thru synaptic samething.
there are still some compiz items installed should i remove those too?

---

### Post by sikander3786 on 2010-09-20
I use fusion-icon for that.

```

sudo apt-get install fusion-icon

```

Then add it to your startup by using the same command. It will sit in the system tray and allow you to switch between windows managers and decorators and also reload one if it runs unstable. It actually sorted out my compiz problems also.

Hope it works for you too.

---

### Post by soryu on 2010-09-20
that works to. but don't want to install more things.
 is there some command i can use to reconfigure metacity settings?

just did gksudo gconf-editor enabled metacity compositing.

hope it works.

restarting.

---

### Post by soryu on 2010-09-20
did'nt

---

### Post by sikander3786 on 2010-09-20
I did a bit of Google and it was revealed that the package compiz-core might be the one needed. See here.

[http://ubuntuforums.org/showthread.php?t=677337](http://ubuntuforums.org/showthread.php?t=677337)

Also see this one if problem persists.

[http://ubuntuforums.org/showthread.php?t=701583](http://ubuntuforums.org/showthread.php?t=701583)

---

