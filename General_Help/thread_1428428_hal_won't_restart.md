---
title: "hal won't restart"
date: 2010-03-12
forum: General Help
---

### Post by the_damian_child on 2010-03-12
Various places on the net have told me to put 'sudo /etc/init.d/hal restart' in a terminal to restart hal.
But when I did it told me I should just type 'restart hal'

But then I get this

restart: Rejected send message, 1 matched rules; type="method_call", sender=":1.120" (uid=1000 pid=13705 comm="restart) interface="com.ubuntu.Upstart0_6.Job" member="Restart" error name="(unset)" requested_reply=0 destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init"))

What's the matter?

---

