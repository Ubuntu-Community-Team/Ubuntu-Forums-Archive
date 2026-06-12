---
title: "Suddenly lsb start_daemon does not fork the new pid at bootup, fine once booted"
date: 2010-03-16
forum: General Help
---

### Post by mdlueck on 2010-03-16
Starting with Ubuntu 9.10, and presisting through today's daily ISO of Lucid, services which use lsb start_daemon to start their service, start_daemon does not fork off the daemon process WHEN THE SERVICE IS STARTED AT BOOTUP. However, killing the daemon process which in turn clears up the hung start script to clean up the environment - then starting the service interactively, the start script runs cleanly through to completion.

I have opened a bug against this behavior against 9.10, and also verified that versions of Lucid do it, up through today's daily ISO.

Does anyone know of other software which uses lsb start_daemon to start services so I could compare if also affects other packages using lsb start_daemon?

What is different DURING BOOT TIME that lsb start_daemon is unable to fork the daemon process, but once booted it forks properly and completes the script?

Here is my bug report:
"Suddenly start_daemon does not fork the new pid, hangs the script"
[https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/532341](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/532341)

I have checked and the other two start service methods the start script looks for do not come as part of Ubuntu, so lsb start_daemon is the only choice it seems on Ubuntu to start the service.

---

### Post by dcstar on 2010-03-16
> **mdlueck said:**
> Starting with Ubuntu 9.10, and presisting through today's daily ISO of Lucid, services which use lsb start_daemon to start their service, start_daemon does not fork off the daemon process WHEN THE SERVICE IS STARTED AT BOOTUP. However, killing the daemon process which in turn clears up the hung start script to clean up the environment - then starting the service interactively, the start script runs cleanly through to completion.

I have opened a bug against this behavior against 9.10, and also verified that versions of Lucid do it, up through today's daily ISO.

Does anyone know of other software which uses lsb start_daemon to start services so I could compare if also affects other packages using lsb start_daemon?

What is different DURING BOOT TIME that lsb start_daemon is unable to fork the daemon process, but once booted it forks properly and completes the script?

Here is my bug report:
"Suddenly start_daemon does not fork the new pid, hangs the script"
[https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/532341](https://bugs.launchpad.net/ubuntu/+source/lsb/+bug/532341)

I have checked and the other two start service methods the start script looks for do not come as part of Ubuntu, so lsb start_daemon is the only choice it seems on Ubuntu to start the service.

AFAIK 9.10 onwards use asynchronous starting of services ("parallel") instead of ordered starting as in previous versions to decrease boot times.

Chances are that your package is trying to start before another dependant service has completed initialising.

There is a config setting called "CONCURRENT=" somewhere that you can change to make is behave as before, you'll have to do a search to find its location.

---

### Post by mdlueck on 2010-03-17
> **dcstar said:**
> AFAIK 9.10 onwards use asynchronous starting of services ("parallel") instead of ordered starting as in previous versions to decrease boot times.

Aaahhh... that might be the difference then!

I sent the support team for the affected software an update / link to this thread. Thank you so much!

---

### Post by mdlueck on 2010-03-19
On Windows I ended up needing to update the Apache service and stipulate that it relies on the RxAPI service being running. That cured a race between Apache starting and the RxAPI service.

I suppose that same sort of thing needs to be done to work with Ubuntu and the new parallel starting of services.

Where may we read up on how services may be ordered in the parallel service way of operation?

---

### Post by mdlueck on 2010-03-19
One of the ooRexx developers replied that the main thing rxapid needs is for networking sockets to be available. So how does one order the starting of services that networking / sockets needs to get started BEFORE rxapid?

---

