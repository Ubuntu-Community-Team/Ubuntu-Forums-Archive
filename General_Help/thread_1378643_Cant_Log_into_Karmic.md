---
title: "Cant Log into Karmic"
date: 2010-01-11
forum: General Help
---

### Post by ryan455 on 2010-01-11
Hello

I have installed ubuntu on numerous computers, but for some reason I am getting this problem on this computer

When I try to log in GDM flickers then goes back to the user selection screen. After like 10 attempts i can log in. It doesn't always do this either.

Hopefully these log errors will help solve this problem.

> Jan 11 14:34:18 arnold-desktop gdm-binary[1367]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan 11 14:34:18 arnold-desktop gdm-binary[1367]: WARNING: Unable to find users: no seat-id found
Jan 11 14:34:18 arnold-desktop gdm-simple-slave[1414]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Jan 11 14:34:18 arnold-desktop acpid: client connected from 1422[0:0]
Jan 11 14:34:21 arnold-desktop console-kit-daemon[690]: WARNING: Couldn't read /proc/689/environ: Failed to open file '/proc/689/environ': No such file or directory

I hope I can get help with this, I have reinstalled ubuntu twice and reinstalled GDM.

---

### Post by Spencer William on 2010-01-11
I'm getting the same problem in Ubuntu Studio (Karmic). I've had it for weeks and it just started doing this. I can log in to a shell with no problem as well as root. (I was doing this from recovery mode) 

Something of interest to me was that my sudoers file had been apparently reset. It no longer contained my login name under the privileges section. I'm going to look into it further.

---

### Post by ryan455 on 2010-01-14
bump?

---

### Post by warfacegod on 2010-01-14
I would suggest getting all updates as a first step.

---

### Post by ryan455 on 2010-01-14
I have done that.

---

### Post by warfacegod on 2010-01-14
I assume you have all the proper drivers for your hardware and that they are activated.

You should give a brief description of your computer. Make, model, specs, etc. and post any error logs.

---

