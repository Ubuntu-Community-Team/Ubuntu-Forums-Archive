---
title: "Administrative Panel problem in Jaunty"
date: 2009-07-14
forum: General Help
---

### Post by Bit101 on 2009-07-14
After updating dbus yesterday, I logged in today to find that A: I couldn't access administrative options, even as root B: instead of tau (my localhost name) it just says localhost, and C: I cannot access internet at all on an admin account, and wired only on root. I'm assuming there is a problem with dbus or group permssions. Please help, thank you in advance.

---

### Post by cariboo on 2009-07-14
Is dbus starting and running properly?

---

### Post by Bit101 on 2009-07-14
I think so. However, when I run network-admin from command line, it throws a "Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success" and pops up a little box saying "Can not access system configuration"

---

### Post by Bit101 on 2009-07-14
*bump*

---

### Post by Bit101 on 2009-07-14
*bumpipty bump* (normally I would be more patient but I got a report to write >.<)

---

### Post by Bit101 on 2009-07-14
After changing the Failed to execute program dbus-daemon-launch-helper to excutable, it now gives ** (network-admin:23809): CRITICAL **: The permission of the setuid helper is not correct

---

### Post by CatKiller on 2009-07-14
> **Bit101 said:**
> instead of tau (my localhost name) it just says localhost

I can't give you specific guidance I'm afraid, but I have seen problems with the hostname mess up the admin functions before. I don't know how it works, but somehow the sudo mechanism is tied to the hostname.

The problem that I've seen before had different names for the machine in /etc/hostname and /etc/hosts. I don't know if that's part of the problem you're currently experiencing.

---

### Post by Bit101 on 2009-07-14
Problem has been solved by reinstalling dbus.

---

