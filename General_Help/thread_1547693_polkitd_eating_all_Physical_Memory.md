---
title: "polkitd eating all Physical Memory"
date: 2010-08-07
forum: General Help
---

### Post by linuxyogi on 2010-08-07
Hi,

The problem is my pc is getting slow at times & the only way out (temporary) is restarting it.

I tried to do some troubleshooting myself.

I uninstalled kde, lxde, because system monitor was showing a lot of processes starting with "k". I thought all those belongs to kde & were responsible for this situation. I don't use KDE, it was installed with K3B. About LXDE, I just wanted to see its look n fell. So don't bother about these. But when unistalling these did not solve the issue I looked further (in system monitor)& saw **"polkitd" **is consuming almost the entire  remaining ram.

**Recently I enabled the apparmor profile for FF. Is that causing it ?**

**I had to edit ~/.pulse/default.pa  & ~/.pulse/daemon.conf in order to get surround sound working because as you know pulse audio defaults to 2 channels.**

Let me also mention that the computer doesn't get slow as soon as I boot it. It gets slow gradually.

**I can actually see polkitd growing in size, using System Monitor.**

Also, the **hdd LED on the front panel glows constantly**, indicating disk activity.

Please help.

---

### Post by linuxyogi on 2010-08-07
Deleting the this file  "~/.pulse-cookie" seems to have corrected the problem.

Got the idea by reading this 

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813]("https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813").

I guess I will wait for a few days & if all is well I will mark this thread as solved.

---

### Post by linuxyogi on 2010-08-13
This is the solution -------

Delete the file   "~/.pulse-cookie" 

Reboot.

---

### Post by rocsco on 2011-01-12
Hi

Here I am in 10.10 and polkitd is doing exactly as described.

I remove file "~/.pulse-cookie" and a few seconds later there it is again.
So I have set a crontab job to remove it every 5 seconds to get me by, sort of.
Now it takes a couple of days before memory is gone & I have to re-boot.

Is there a permanent solution to this problem?

---

### Post by linuxyogi on 2011-01-14
> **rocsco said:**
> Hi

Here I am in 10.10 and polkitd is doing exactly as described.

I remove file "~/.pulse-cookie" and a few seconds later there it is again.
So I have set a crontab job to remove it every 5 seconds to get me by, sort of.
Now it takes a couple of days before memory is gone & I have to re-boot.

Is there a permanent solution to this problem?

In my case removing the "~/.pulse-cookie" once resolved the issue. The "~/.pulse-cookie" appeared again but it was no longer consuming physical memory as before.

---

### Post by rocsco on 2011-01-15
Thanks for the advice. Unfortunately, it just goes on eating memory no matter how many times I delete the cookie or reboot the system.
One day ...

---

### Post by basich on 2011-02-03
Vmware tools or something for me renamed /etc/pulse/default.pa to /etc/pulse/default.pa.old

I renamed it back and rebooted and everything is working for me again.

The deletion of ~/.pulse* and ~/.dbus did not work.

---

