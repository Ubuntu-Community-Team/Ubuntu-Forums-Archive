---
title: "netbook does not hibernate when lid is closed"
date: 2010-01-16
forum: General Help
---

### Post by baconrad on 2010-01-16
My  netbook does not hibernate when lid is closed. Sometimes it does but usually not. At first I was thinking it was getting confused after recharging, thinking it was still in AC mode. I suppose it could be some process running in the background but don't know how to identify which one would cause that. If that were the case, would I be able to manually go to Hibernate?

I've checked my preferences and "On Battery Power" "When Lid is closed" is set to Hibernate.

I have an ASUS 1000. I recently upgraded to Ubuntu 9.1 karmic.

Anybody else have this problem or have any ideas?

---

### Post by nullmind on 2010-01-16
It sounds like hibernation is working okay on your system, but the lid switch or the communication about the lid switch event isn't being processed.

You can hibernate anytime by running:

pm-hibernate

So you could press ALT+F2 to run that. You can also manually hibernate by using the menu from the Shut Down.

---

