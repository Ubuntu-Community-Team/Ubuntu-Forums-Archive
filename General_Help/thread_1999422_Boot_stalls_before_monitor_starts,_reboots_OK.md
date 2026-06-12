---
title: "Boot stalls before monitor starts, reboots OK"
date: 2012-06-08
forum: General Help
---

### Post by SomethingFishy on 2012-06-08
Hi

At the moment when I boot up the process doesn't get very far before hanging up.  The power indicator light is on and the fan is whirring, the monitor begins to start up from its standby mode and then shuts down again and there's no more sign of disk activity.  A reboot using the restart/reset button on the PC boots me up fine.  A look at bootlog doesn't help because that only shows the most recent boot.

This is an intermittent problem. It was happening a few weeks ago, stopped happening for no apparent reason, then started again a couple of days ago.

Any thoughts?

---

### Post by wilee-nilee on 2012-06-08
Did you install a 3rd party graphics driver?

---

### Post by SomethingFishy on 2012-06-08
Thanks for the reply.  In answer, no, but I should have mentioned I've changed the monitor.

---

### Post by SomethingFishy on 2012-07-22
Finally worked out that this issue occurs when the periodic automatic error check of hard disk is activated.  I kept hitting C to cancel it - impatient I'm afraid - and when I let it run the problem disappeared.  The problem just occured again and was cured by letting the scan run, so that must be it.

---

