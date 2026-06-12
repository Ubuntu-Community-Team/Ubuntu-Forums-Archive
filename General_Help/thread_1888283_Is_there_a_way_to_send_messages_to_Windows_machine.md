---
title: "Is there a way to send messages to Windows machines?"
date: 2011-11-29
forum: General Help
---

### Post by Mars11 on 2011-11-29
Okay, this may sound n00bish, but I was wondering if there was a way in the Terminal to send commands to Windows machines? Anyone know?

---

### Post by Chronon on 2011-11-29
You can connect to a host computer running various services (ssh, sftp, etc.).  Whether the host computer is running Windows shouldn't make a difference.

---

### Post by Mars11 on 2011-11-29
I guess I worded that wrong; it was late. I meant to say messages. Is there a way to send messages to other computers running Windows from the Terminal?

---

### Post by deonis on 2011-11-29
It was working for win 2000 using smbclient, but not for winXP ++

---

### Post by deonis on 2011-11-29
here is some info about that: [http://www.linuxquestions.org/questions/linux-networking-3/smbclient-m-xxx-xxx-xxx-xxx-doesnt-work-465378/](http://www.linuxquestions.org/questions/linux-networking-3/smbclient-m-xxx-xxx-xxx-xxx-doesnt-work-465378/)

---

### Post by jonobr on 2011-11-29
try

```
smbclient -M <windows box>
```
enter the message and then
Control D will send

if you don't have it installed you will get an error message that its missing

---

