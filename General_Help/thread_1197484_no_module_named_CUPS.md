---
title: "no module named CUPS"
date: 2009-06-26
forum: General Help
---

### Post by bindkeeper on 2009-06-26
Hi I cannot get access to my printing jobs

Applications => Accessories => Manage Printing Jobs

In terminal 
```
/usr/bin/system-config-printer-applet --no-tray-icon

```
gave me this error
```
Traceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 20, in <module>
    import cups
ImportError: No module named cups

```

according to my synaptic I do have cupsys installed

---

### Post by SteveDee on 2009-06-26
Don't know if this helps, but searching in Synaptic for "cups" on my system gave this list of installed packages...

---

### Post by dka on 2009-06-26
Lets first make sure it is running, since synaptic says you have it.

Run the command: sudo /etc/init.d/cups restart .  It will simply restart the cups service if it is running, or start it if it is some how not running.

---

### Post by bindkeeper on 2009-06-26
strange
```
sudo /etc/init.d/cups restart
```

gave me this

```
sudo: /etc/init.d/cups: command not found

```

---

### Post by bindkeeper on 2009-06-28
I attached a screen shoot from the synaptic

---

### Post by bindkeeper on 2009-06-28
ok I download the CUPS from.org and installed it 
I can work with it in command line, but when I try to run the "print job manger"

```
 usr/bin/system-config-printer-applet --no-tray-icon

```

it still returns

```
Traceback (most recent call last):
  File "/usr/share/system-config-printer/applet.py", line 20, in <module>
    import cups
ImportError: No module named cups

```

---

