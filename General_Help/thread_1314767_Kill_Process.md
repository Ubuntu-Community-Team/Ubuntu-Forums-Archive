---
title: "Kill Process"
date: 2009-11-04
forum: General Help
---

### Post by KlinerDraken on 2009-11-04
Is there any thing I can do (besides rebooting) to end a process that will not end with "kill -9 <PID>"?

---

### Post by Zoot7 on 2009-11-04
Run:
```
sudo top
```
Identify the PID of the process you want to kill, press k, enter the PID, and hit enter.

Or another thing that works with applications is to use pkill, not sure whether it works for arbitary processes: eg.
```
pkill firefox
```

Alternatively, you can do
```
ps -ef | grep <process name>
```
That'll return the PIDs of the process, and then
```
kill <PID> or sudo kill <PID>
```
Depending on whether you've permissions to kill it or not.

---

