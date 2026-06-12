---
title: "Cannot shut down"
date: 2009-12-08
forum: General Help
---

### Post by bossa on 2009-12-08
Hi All
Shutting down ,logging out does not work since last night .I get the option dialogue turns up, choose shut down/log out and then nothing.Ctrl+Alt+Delete does not work .The only thing that will work is hibernate and switch user ? Halting only via terminal . Tried with earlier kernels but get the same thing .
Any ideas ?

---

### Post by SuperSonic4 on 2009-12-08
What happens when you issue ```
sudo shutdown -hP now
```

(if this works it should power off the system via shutdown so be sure to save any data before issuing it)

---

### Post by LeifAndersen on 2009-12-08
Also, for future reference, to my knowledge, Ctrl+Alt+Del doesn't really do anything in linux.  Ctrl+Alt+Backspace used to, but not any more.

---

### Post by SuperSonic4 on 2009-12-08
> **LeifAndersen said:**
> Also, for future reference, to my knowledge, Ctrl+Alt+Del doesn't really do anything in linux.  Ctrl+Alt+Backspace used to, but not any more.

Ctrl+Alt+Del does bring up the shutdown menu in KDE 4.4 and probably 4.3

---

### Post by LeifAndersen on 2009-12-08
Great, I must say it's about time. :)

---

### Post by bossa on 2009-12-08
> **SuperSonic4 said:**
> What happens when you issue ```
sudo shutdown -hP now
```

(if this works it should power off the system via shutdown so be sure to save any data before issuing it)

Hi SuperSonic4

Yeah almost instantaneous shut down, but how do I get the normal shut down/logout options to work ?

---

### Post by rnerwein on 2009-12-08
;)> **LeifAndersen said:**
> Also, for future reference, to my knowledge, Ctrl+Alt+Del doesn't really do anything in linux.  Ctrl+Alt+Backspace used to, but not any more.
just have a look at /proc/sys/kernel/ctrl-alt-del (cat ctrl-alt-del)  - my value is set to zero and the the maual page (see: man 5 proc) told me that ctrl-alt-del is trapped and send
to init to handle a graceful restart. i tried it - the result on my pc was  -> a dead of kiss was send to the system - results in power off (gulp).

---

### Post by bossa on 2009-12-09
bump

---

