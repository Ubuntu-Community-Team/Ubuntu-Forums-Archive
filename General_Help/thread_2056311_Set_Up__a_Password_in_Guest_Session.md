---
title: "Set Up  a Password in Guest Session"
date: 2012-09-11
forum: General Help
---

### Post by Richiegs on 2012-09-11
I am using Ubuntu 12.04. To make my computer a little more secure, I wonder if it is possible to also set up a login password  for the guest session. Thanks in advance.

---

### Post by newb85 on 2012-09-11
Not sure about adding a password, but if you don't need the guest session, you could disable it.

```
$ sudo gedit /etc/lightdm/lightdm.conf
```
At the bottom of the file add the line

```
allow-guest=false
```

To

---

### Post by grahammechanical on 2012-09-11
Have you read this?

[http://www.ubuntugeek.com/how-to-disable-or-enable-guest-session-in-ubuntu-12-04.html]("http://www.ubuntugeek.com/how-to-disable-or-enable-guest-session-in-ubuntu-12-04.html")

Having a password for the guest session would defeat the purpose of having a guest session. Ubuntu would not have a guest session by default if it weakened the security of the machine.

Regards.

---

### Post by newb85 on 2012-09-11
> It is a machine. It is more stupid than we are. It will not stop us from doing stupid things.

A pair of handcuffs is a machine that could stop a person from doing stupid things.  Of course, it would also stop a person from doing productive things...  ;)

---

### Post by newb85 on 2012-09-11
> **grahammechanical said:**
> Have you read this?

[http://www.ubuntugeek.com/how-to-disable-or-enable-guest-session-in-ubuntu-12-04.html]("http://www.ubuntugeek.com/how-to-disable-or-enable-guest-session-in-ubuntu-12-04.html")

Having a password for the guest session would defeat the purpose of having a guest session. Ubuntu would not have a guest session by default if it weakened the security of the machine.

Regards.

Arguably, there could still be a benefit to a password-ed guest session--lack of persistence.

---

### Post by Richiegs on 2012-09-11
Thanks. Instead of using command lines in the terminal, is there any graphical program in Ubuntu which can enable or disable the guess session?

---

