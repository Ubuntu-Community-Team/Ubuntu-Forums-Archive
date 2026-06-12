---
title: "Dual Monitor - unable to set notebook display as primary"
date: 2011-01-18
forum: General Help
---

### Post by Shellbak3 on 2011-01-18
I have 10.04 on a HP notebook with a Mobile GM965/GL960 Integrated Graphics Controller and use a Dell flat screen as a secondary display on "top" of the notebook display.

I cannot set the notebook display as the primary display.  Some windows and icons go to the Dell display and some behave as I expected and go to the notebook display.  Since I'm asked when logging in to supply a password to the keychain and that appears on the Dell display I cannot use the notebook without the Dell display. If I make sure that windows I close are in the notebook display then they will probably reopen there.  The keychain window can't be dragged. 

I found the monitor.xml and changed primary<no> to <yes> and rebooted to no effect.  There is no xorg.conf file.

What must I do to make the notebook display the default or primary display?

---

