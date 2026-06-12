---
title: "How to disable notification balloons?"
date: 2011-12-05
forum: General Help
---

### Post by woodyg on 2011-12-05
Is there a way to disable the notification balloons? Every time I open the lid to my laptop I am greeted by two messages, the power manager and the network one. The power manager notification disappears after a few seconds (but is still annoying) and the network notification stays forever unless I manually close it... seems to be some bug.

(I remember there recently was a bug where the network notifications multiplied, so maybe it is related)

---

### Post by bluexrider on 2011-12-05
If you really don't want to ever see any notification balloons, you should be able to:

 	Code:
 	sudo chmod -x /usr/lib/notification-daemon/notification-daemon pkill notification-daemon 
That makes the daemon non-executable and will prevent it from ever  being started.  You can't just "apt-get remove" it without taking some  other important packages with it so, this is the only method I know of  if you want to disable all the balloons.

---

