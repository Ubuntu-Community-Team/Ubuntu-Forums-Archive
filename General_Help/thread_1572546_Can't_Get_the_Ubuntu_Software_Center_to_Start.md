---
title: "Can't Get the Ubuntu Software Center to Start"
date: 2010-09-11
forum: General Help
---

### Post by corrytonapple on 2010-09-11
Hello all,
 I am having issues launching the Ubuntu Software Center. I click it and it appears to start, but a window never comes up. I would like to either uninstall it and reinstall it or start it from the terminal. Thank you for the help.

---

### Post by Lateralis on 2010-09-11
The Software Center package is helpfully named software-center.  Does Synaptic say the package is broken?  

You could try reinstalling it using aptitude.

---

### Post by Frogs Hair on 2010-09-11
You can remove and install from the synaptic pkg manager. search Ubuntu software center.

---

### Post by coffeecat on 2010-09-11
> **corrytonapple said:**
> or start it from the terminal.

Good idea. :) If you start it from the terminal you might get an error message that might tell us what the problem is. It's always worth doing this when an app won't start from the menu.

The terminal command you need is:

```
/usr/bin/software-center
```Post any terminal output you get.

---

### Post by abs_kkk on 2010-09-11
to remove the software centre......

> sudo apt-get remove software-centerand the re-install it ..........

> sudo apt-get install software-center

---

### Post by corrytonapple on 2010-10-11
> **coffeecat said:**
> Good idea. :) If you start it from the terminal you might get an error message that might tell us what the problem is. It's always worth doing this when an app won't start from the menu.

The terminal command you need is:

```
/usr/bin/software-center
```Post any terminal output you get.
I worked as soon as I changed my icon theme. Here is my terminal output:
```

corrytonapple@ubuntu-laptop:~$ /usr/bin/software-center
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()
ERROR:dbus.proxies:Introspect error on :1.180:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.181" (uid=1000 pid=6427 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.180" (uid=0 pid=6166 comm="/usr/bin/python))
corrytonapple@ubuntu-laptop:~$


```I do not know why, but it is working. I am not going to mark it as solved though until I get a few more things out of it. Also, I forgot to subscribe to this thread, so it got lost. :)
> **abs_kkk said:**
> to remove the software centre......

and the re-install it ..........
I will be sure to use that if it acts up and it cannot be fixed.

---

