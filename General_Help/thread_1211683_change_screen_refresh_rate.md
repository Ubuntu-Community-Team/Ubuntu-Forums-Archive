---
title: "change screen refresh rate"
date: 2009-07-12
forum: General Help
---

### Post by venkat m on 2009-07-12
i have changed screen refresh rate from 60 to 85 in ubuntu.
then iam not able to log in .
after logging in the system is restarting.
i think my monitor is not compatible with 85 hertz.
can you tell how to change the refresh rate ??

---

### Post by venkat m on 2009-07-12
> **venkat m said:**
> i have changed screen refresh rate from 60 to 85 in ubuntu.
then iam not able to log in .
after logging in the system is restarting.
i think my monitor is not compatible with 85 hertz.
can you tell how to change the refresh rate ??
plzzz tell me...................

---

### Post by mano cazalet on 2009-07-12
if you boot in recovery mode you should be able to set up your monitor settings with 
> sudo dpkg-reconfigure xserver-xorg


ps: and please do not bump ur thread so quickly, someone will always help

---

### Post by venkat m on 2009-07-12
i have booted it in recovery mode.
then what to do??

---

### Post by venkat m on 2009-07-12
> **mano cazalet said:**
> if you boot in recovery mode you should be able to set up your monitor settings with 



ps: and please do not bump ur thread so quickly, someone will always help
then what to do
??????

---

### Post by CatKiller on 2009-07-13
> **venkat m said:**
> i have changed screen refresh rate from 60 to 85 in ubuntu.
then iam not able to log in .
after logging in the system is restarting.
i think my monitor is not compatible with 85 hertz.
can you tell how to change the refresh rate ??

If you mean that the login window displays properly, but when you log in you don't get a display you can reset your per-user resolution setting by switching to a virtual console with Ctrl-Alt-F1 and logging in there. Do ```
rm .config/monitors.xml
```to remove your existing configuration and then switch back to the login screen with Alt-F7.

---

