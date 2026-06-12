---
title: "what ubuntu am i running"
date: 2012-10-10
forum: General Help
---

### Post by jtmedin on 2012-10-10
how do i find out what ubuntu version i am running?

---

### Post by pissedoffdude on 2012-10-10
As in 64-bit, or release number? 

I think the system monitor will tell you both of these.  If you have an older version of Ubuntu, it should be under System>Administration (or maybe preferences?)

Otherwise, you can search  for system monitor in the dash

---

### Post by wojox on 2012-10-10
> **jtmedin said:**
> how do i find out what ubuntu version i am running?
Open a terminal (Ctrl+Alt+T)
```
cat /etc/lsb-release
```

---

### Post by jrog on 2012-10-10
> **wojox said:**
> Open a terminal (Ctrl+Alt+T)
```
cat /etc/lsb-release
```
```
lsb_release -cd
```looks nicer. :P

---

### Post by jtmedin on 2012-10-11
Ok thanks. I was downloading 12.04 to a usb stick & when i rebooted i was on 12.04. Before i was runing 10.04 as i remember. So i must have done something wrong/right :-).

---

