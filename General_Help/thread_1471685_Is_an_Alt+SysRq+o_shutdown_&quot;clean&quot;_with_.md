---
title: "Is an Alt+SysRq+o shutdown &quot;clean&quot; with regard to disk buffers?"
date: 2010-05-03
forum: General Help
---

### Post by frappe1 on 2010-05-03
I've been having a [bad problem with X freezing up]("http://ubuntuforums.org/showthread.php?t=1470708") (but not the whole system), and I hate continually performing unclean shutdowns with the power button.

Will an Alt+SysRq+o shut down the system in a way that doesn't cause the loss of disk buffers? Obviously, whatever hasn't been saved to the buffer will be lost, but my concern extends to the buffers themselves.

ext4 and autofsck make this less of an issue, but I hate the thought of unnecessary silent corruption until the freezing stops.

---

### Post by sisco311 on 2010-05-03
Try Alt+SysRq+k to kill all processes on the current virtual console or try "Raising Elephants" :) Alt+SysRq+reisub (**R**aising **E**lephants **I**s **S**o **U**tterly **B**oring).

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by tgalati4 on 2010-05-03
Don't know, but REISUB seems to be the preferred order of ungraceful shutdown.

---

### Post by frappe1 on 2010-05-03
Will the reiusb ensure buffer contents are not lost when the sequence eventually reaches the b?

I know the chance of corruption is small, but I expect several hundred more freezes in the next week or so. Small risks become huge problems given enough instances.

---

### Post by hansdown on 2010-05-03
Hi frappe1.

Here is an explanation of this command.

[http://www.matejunkie.com/magic-sysrq-reisub/](http://www.matejunkie.com/magic-sysrq-reisub/)

The order that the keys are pressed makes little difference.

---

### Post by tgalati4 on 2010-05-04
However, it's recommended that a few seconds pass between each command so that you ensure the actions are captured and executed before "b".

---

### Post by hansdown on 2010-05-04
> **tgalati4 said:**
> However, it's recommended that a few seconds pass between each command so that you ensure the actions are captured and executed before "b".

Thanks tgalati4.

I should have pointed that out.

---

