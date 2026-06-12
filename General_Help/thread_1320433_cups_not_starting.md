---
title: "cups not starting"
date: 2009-11-09
forum: General Help
---

### Post by Woody1987 on 2009-11-09
When i turn on my computer, cups doesnt automatically start as it used to in jaunty. When i need to print i have to manually run it with sudo /etc/init.d/cups start. How can i get it to start automatically again?

---

### Post by Giblet5 on 2009-11-09
Make sure that there is a symbolic link from /etc/init.d/cups to /etc/rc2.d/S50cups

```
ls -l /etc/rc2.d/*cups
```

If not, then make one:

```
sudo ln -s /etc/init.d/cups /etc/rc2.d/S50cups
```

---

### Post by Woody1987 on 2009-11-09
> Make sure that there is a symbolic link from /etc/init.d/cups to /etc/rc2.d/S50cups

Code:

ls -l /etc/rc2.d/*cups



output: 

lrwxrwxrwx 1 root root 14 2009-10-23 21:06 /etc/rc2.d/S50cups -> ../init.d/cups

Any other ideas?

---

### Post by Giblet5 on 2009-11-09
Wow.

What run-level are you at? ```
who -r
```

It's simple stuff that goes on here...

Worst-case, you could add '/etc/init.d/cups restart' to /etc/rc.local...

(duct-tape, spare twisty, and spit fix)

---

### Post by Woody1987 on 2009-11-09
run-level 2  2009-11-09 12:13

---

### Post by Giblet5 on 2009-11-09
What's the output from ```
dmesg
```

(maybe cups is trying to tell us what's wrong)

---

### Post by Woody1987 on 2009-11-09
output from dmesg is very long so i ran dmesg | grep cups and got

[    3.974295] type=1505 audit(1257768828.467:9): operation="profile_load" pid=448 name=/usr/lib/cups/backend/cups-pdf
[    3.975138] type=1505 audit(1257768828.467:10): operation="profile_load" pid=448 name=/usr/sbin/cupsd
[   10.220148] type=1505 audit(1257768834.714:19): operation="profile_replace" pid=990 name=/usr/lib/cups/backend/cups-pdf
[   10.220754] type=1505 audit(1257768834.714:20): operation="profile_replace" pid=990 name=/usr/sbin/cupsd

---

### Post by Giblet5 on 2009-11-09
Was that from during a boot, when cups doesn't seem to start?

---

### Post by Woody1987 on 2009-11-09
yep

---

### Post by Giblet5 on 2009-11-09
It looks like cups is starting fine and running OK at boot time.

Is the printer hanging off of a USB hub? Does that hub have its own power supply?

---

### Post by Woody1987 on 2009-11-09
no, its connected straight to the computer.

---

### Post by Giblet5 on 2009-11-10
Well, there's the duct-tape fix I mentioned earlier...

---

