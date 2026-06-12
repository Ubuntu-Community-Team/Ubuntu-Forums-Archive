---
title: "Can not shutdown my PC"
date: 2011-09-09
forum: General Help
---

### Post by Tariq Bashir Malhi on 2011-09-09
I start facing two problems while working on ubuntu 10.04, and need your help in resolving them.

[LIST=1]
[*]I was able to shutdown my PC when required, without sudo or as root, but now can not. Now i have to login as root to shutdown.
[*]Earlier when ever i insert USB into PC, this instantly appears on my Desktop and file browser. Now it do not show. I need same and do not want to use command line for this purpose. My usb port is perfect as i can access usb via command line.
[/LIST]
Thanks in advance.

---

### Post by BlacqWolf on 2011-09-09
Hello Tariq Bashir Malhi,

I'm blank at the moment, but as I research information, may I ask if you've updated to the latest packages via Update Manager or Synaptic, and which packages have you installed when this issue first occurred? Thanks.

Note: you can get package install history through Ubuntu Software Center's History, available through the left pane of the Software Center.

---

### Post by Bodsda on 2011-09-09
> **Tariq Bashir Malhi said:**
> I start facing two problems while working on ubuntu 10.04, and need your help in resolving them.

[LIST=1]
[*]I was able to shutdown my PC when required, without sudo or as root, but now can not. Now i have to login as root to shutdown.
[*]Earlier when ever i insert USB into PC, this instantly appears on my Desktop and file browser. Now it do not show. I need same and do not want to use command line for this purpose. My usb port is perfect as i can access usb via command line.
[/LIST]Thanks in advance.
 
If you launch a terminal as a normal user, and run
```

shutdown -P now

```
 
What happens?
 
Thanks,
Bodsda

---

### Post by Tariq Bashir Malhi on 2011-09-09
eobi@eobi-desktop:~$ shutdown -P now
shutdown: Need to be root
eobi@eobi-desktop:~$

---

