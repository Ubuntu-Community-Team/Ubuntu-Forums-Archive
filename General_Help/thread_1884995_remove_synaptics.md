---
title: "remove synaptics???"
date: 2011-11-22
forum: General Help
---

### Post by etyson on 2011-11-22
Hi all,

The missus was sitting at the machine and I told her to launch Synaptic (package manager).  In the menu, she saw the word "synaptics" and selected it.  Nothing happened, so she kept clicking the same menu entry.  Note:  This machine does not have a touchpad of any type.

Now, everytime the machine is powered up, synaptics complains that it can't find the touchpad.  How do we un-install this driver?

Thx.

---

### Post by oldos2er on 2011-11-22
Try ```
sudo apt-get remove kde-config-touchpad
```

---

### Post by etyson on 2011-11-23
Worked like a charm -- thanks very much!

---

### Post by oldos2er on 2011-11-23
You're welcome. Can you please mark the thread as 'Solved' (under Thread Tools)?

---

