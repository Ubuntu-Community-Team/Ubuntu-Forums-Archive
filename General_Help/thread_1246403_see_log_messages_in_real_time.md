---
title: "see log messages in real time"
date: 2009-08-21
forum: General Help
---

### Post by liviusbr on 2009-08-21
Hello! I want to be able to see the log messages in real time, showing on the screen messages after inserting an usb device, for example. How can i do that ?

---

### Post by DaithiF on 2009-08-21
in a terminal:
```
tail -f /var/log/dmesg

```
when you have seen enough, press CTRL+C to stop

alternatively, running the command
```
dmesg

```
gives you the most recent messages, so plugging in your device and then running dmesg is usually fine (ie. no need to tail the log)

---

### Post by liviusbr on 2009-08-21
Thanks. One remaining thing : how can I see the timestamp for this log in a human readable format ?
This is how the message appears right now :

[  555.643281] usblp0: removed

I want to see the proper time instead of 555.643281.

Thank you.

---

### Post by dcstar on 2009-08-21
> **liviusbr said:**
> Thanks. One remaining thing : how can I see the timestamp for this log in a human readable format ?
This is how the message appears right now :

[  555.643281] usblp0: removed

I want to see the proper time instead of 555.643281.

Thank you.

That is the seconds since reboot, that is all you get.

---

