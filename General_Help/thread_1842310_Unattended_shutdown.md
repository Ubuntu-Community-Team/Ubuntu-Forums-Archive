---
title: "Unattended shutdown"
date: 2011-09-11
forum: General Help
---

### Post by dryder on 2011-09-11
I am using computertemp to monitor my cpu temp etc.

In the 'High alarm command' box I want to put a non sudo command that shutsdown the computer. > /sbin/shutdownonly works for sudo - which doesn't help if I'm asleep! :)

Any suggestions, please?

David

---

### Post by The Cog on 2011-09-11
It is possible to modify /etc/sudoers so that selected users/commands don't need to provide a sudo password. This post might help:
[http://www.linuxquestions.org/questions/linux-software-2/no-password-for-sudo-442808/](http://www.linuxquestions.org/questions/linux-software-2/no-password-for-sudo-442808/)

---

### Post by hakermania on 2011-09-11
Hello, you can shutdown you PC without using sudo using the following command:
```

dbus-send --print-reply --system --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Shutdown

```

---

### Post by dryder on 2011-09-12
Many thanks for replying.

I'll give both a try ..

David

---

