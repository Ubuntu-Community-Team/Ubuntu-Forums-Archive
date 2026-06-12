---
title: "Sytem font"
date: 2009-07-01
forum: General Help
---

### Post by Brian Carruthers on 2009-07-01
hello. I've just upgrade my son's old computer (running dapper drake), and now the system font appears as rectangles instead of text characters...how can I change this?  I have access to terminal. Thanks.

---

### Post by akakingess on 2009-07-01
> **Brian Carruthers said:**
> hello. I've just upgrade my son's old computer (running dapper drake), and now the system font appears as rectangles instead of text characters...how can I change this?  I have access to terminal. Thanks.
Does it still look like that if you go under Preferences --> Appearance and the Font tab and change it from within there, just a thought so that we might start narrowing down the problem.

akakingess

---

### Post by master_kernel on 2009-07-01
Either that or the character encoding is set wrong. But I wouldn't know how to fix this. It would need to be UTF-8.

---

### Post by Brian Carruthers on 2009-07-01
> **akakingess said:**
> Does it still look like that if you go under Preferences --> Appearance and the Font tab and change it from within there, just a thought so that we might start narrowing down the problem.

akakingess

Yes, it stays the same.
However, on boot up it shows "setting kernel variables - failed".
Could that be the problem?

---

### Post by akakingess on 2009-07-01
> **Brian Carruthers said:**
> Yes, it stays the same.
However, on boot up it shows "setting kernel variables - failed".
Could that be the problem?
Which kernel are you running currently? .11 or .13?

akakingess

---

### Post by Brian Carruthers on 2009-07-01
> **akakingess said:**
> Which kernel are you running currently? .11 or .13?

akakingess

Sorry, where should I look to find the kernel #? On boot?

---

### Post by Brian Carruthers on 2009-07-01
> **Brian Carruthers said:**
> Sorry, where should I look to find the kernel #? On boot?

It's probably the later one (.13) since I just did an update.

---

### Post by XCan on 2009-07-01
> **Brian Carruthers said:**
> Sorry, where should I look to find the kernel #? On boot?

You can see it by typing
uname -r

---

### Post by akakingess on 2009-07-01
If you are dual booting then when the Grub menu comes up it will show the kernel version, otherwise you would open a terminal and type ```
uname -a
```

akakingess

---

### Post by Brian Carruthers on 2009-07-01
uname -r results in following: 
2.6.15-54-386

The computer was previously Windows (xp?),now Ubuntu only.

uname -a results in:
2.6.15-54-386 #1 PREEMPT Thu Apr 2 20:08:45 UTC 2009 i6 86 GNU/Linux

---

