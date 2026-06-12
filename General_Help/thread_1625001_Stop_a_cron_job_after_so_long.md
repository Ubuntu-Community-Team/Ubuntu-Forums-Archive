---
title: "Stop a cron job after so long?"
date: 2010-11-18
forum: General Help
---

### Post by CrusaderAD on 2010-11-18
Is it possible to set a cron to run for so long and then end it automatically?

---

### Post by 13½% on 2010-11-18
Cron is a **Service** that runs continuously,
a cron Job (an entry pointing to a script file) gets executed by Cron.

You need a script that does the/a task and that needs to entered into the crontab after testing the script.

Please clarify this situation.

---

### Post by CrusaderAD on 2010-11-18
It's a cron job. Like the title says.

---

### Post by amauk on 2010-11-18
You'll have to split the job up into 2 parts

The user-facing parent part that records the time at the start, then spawns a child that does the work.
Parent waits for either a) child to complete or b) a certain time to elapse, then exits (aborting the child if still running)

---

### Post by CrusaderAD on 2010-11-18
Excellent, thank you!

---

