---
title: "Ctrl+Alt+F* virtual terminals not working?"
date: 2010-02-06
forum: General Help
---

### Post by Gforce20 on 2010-02-06
Usually I get a login prompt on Ctrl+Alt+F[1-6], but now I just see a blinking cursor in all of them, along with some boot messages in the first virtual terminal.

```
fsck from util-linux-ng 2.6
init: bootchart main process (462) terminated with status 2
init: bootchart post-stop process (474) terminated with status 127
/dev/sda2: clean, (integer)/(integer) files, (integer)/(integer) blocks
init: ureadahead-other main process (870) terminated with status 4
```
What's even weirder about this is that I uninstalled bootchart a few months ago. Whether that's related or not is beyond me, but the virtual terminals did stop working somewhere around that time.

Any help, anyone?

**EDIT: I solved this by reverting to my original /etc/network/interfaces file. Without the loopback "lo" device, the runlevel was never set, and virtual terminals never loaded.**
This should be somewhere in the interfaces file:
```
auto lo
iface lo inet loopback
```

---

### Post by Gforce20 on 2010-02-07
Bump, I thought of checking the runlevel because this might be a sign of being in single-user mode, but it returned "unknown".

---

