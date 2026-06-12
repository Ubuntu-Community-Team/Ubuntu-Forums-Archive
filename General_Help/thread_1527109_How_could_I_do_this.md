---
title: "How could I do this?"
date: 2010-07-08
forum: General Help
---

### Post by dragos240 on 2010-07-08
Here's the deal. I want to try out polyphasic sleep. If you don't know what it is, look it up. Basically, I need to set up some sort of daemon to sound an alarm every 4 hours, also it needs to sound another alarm 20 minutes after each 4 hour sound. How can I do this?

---

### Post by marshmallow1304 on 2010-07-08
[Cron]("http://linuxtidbits.wordpress.com/2008/01/19/cron-alarm-clock/")?

---

### Post by NFblaze on 2010-07-09
Im not that good at programming but what about creating 2 scripts.

4hour.sh

[I]while
do
sleep 4h && aplay ~/alarm.wav && sh ~/20min.sh
done[/I]


20min.sh

*sleep 20m && aplay ~/alarm.wav && exit*

---

