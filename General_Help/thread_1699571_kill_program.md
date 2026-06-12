---
title: "kill program"
date: 2011-03-03
forum: General Help
---

### Post by &lt;(-.-)&gt; on 2011-03-03
I cannot kill a program.  it has <defunct> after it in processes.  kill, killall, kill -9 wont work and i don't want to have to reboot my computer every this problem happens.  how can i kill it?

---

### Post by rvchari on 2011-03-03
> **<(-.-)> said:**
> I cannot kill a program.  it has <defunct> after it in processes.  kill, killall, kill -9 wont work and i don't want to have to reboot my computer every this problem happens.  how can i kill it?

try this.
first open terminal abd type top
you will get a list of processes with its name and pid.
note that and open another terminal window and type kill (PID NUMBER) this should solve your problem.

alternatively if you are using conky, make it list your top 3 processes with PID. in this case you need not type top everytime you need to kill a process with its PID.

third option... use this command
killall -e NAME-OF-PROCESS (example conky, chromium etc)

---

### Post by asmoore82 on 2011-03-03
A process labeled as defunct or zombie is as good as dead.
This should not happen under ordinary operations.
Is it one particular program that keeps having this problem?

---

