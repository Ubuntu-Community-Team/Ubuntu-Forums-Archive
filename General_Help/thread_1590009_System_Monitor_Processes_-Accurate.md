---
title: "System Monitor Processes -Accurate?"
date: 2010-10-07
forum: General Help
---

### Post by Quarkrad on 2010-10-07
When I enter the command **sudo killall NetworkManager** I believe network manager is no longer functioning (I have already lost connection at this point so I have no way of checking.  My Internet wireless connection randomly disconnects).  I then enter the command **sudo NetworkManager** and I get the response: **** (NetworkManager:1790): WARNING **: NetworkManager is already running (pid 1787)**

When I look in System/Admin/System Monitor/Processes I find there is no process 1787.  If I close down terminal and restart network manager I am still told a process is already running but there is no process according to System Monitor.  Is there some other way of 'seeing' running processes?

---

### Post by philinux on 2010-10-07
> **Quarkrad said:**
> When I enter the command **sudo killall NetworkManager** I believe network manager is no longer functioning (I have already lost connection at this point so I have no way of checking.  My Internet wireless connection randomly disconnects).  I then enter the command **sudo NetworkManager** and I get the response: **** (NetworkManager:1790): WARNING **: NetworkManager is already running (pid 1787)**

When I look in System/Admin/System Monitor/Processes I find there is no process 1787.  If I close down terminal and restart network manager I am still told a process is already running but there is no process according to System Monitor.  Is there some other way of 'seeing' running processes?

```
ps aux
```

See man ps

---

### Post by Quarkrad on 2010-10-07
Thank you - that command certainly shows a lot more processes. If, as it appears, **sudo killall NetworkManager** is not actually killing my gnome network manager, do you know of a command that will kill this process?

---

### Post by philinux on 2010-10-07
> **Quarkrad said:**
> Thank you - that command certainly shows a lot more processes. If, as it appears, **sudo killall NetworkManager** is not actually killing my gnome network manager, do you know of a command that will kill this process?

It's nm-applet.

I use system monitor. Processes>View show all. Click the process name tab to sort.

Then find the process highlight, and kill it if I need to.

---

### Post by Quarkrad on 2010-10-07
Next time my wireless connection drops (I normally have to reboot to get a connection back) shall I:

[LIST]
[*]find the nm-applet process and kill it*
[*]sudo NetworkManager
[/LIST]

to effectively close down and restart my wireless connection?

* will killing this process kill all processes to do with my wireless Internet connection?

---

### Post by philinux on 2010-10-07
> **Quarkrad said:**
> Next time my wireless connection drops (I normally have to reboot to get a connection back) shall I:

[LIST]
[*]find the nm-applet process and kill it*
[*]sudo NetworkManager
[/LIST]

to effectively close down and restart my wireless connection?

* will killing this process kill all processes to do with my wireless Internet connection?

Seems not. It just kills the panel applet. Although killing NetworkManager should be it. Mine is set to reconnect auto.

---

