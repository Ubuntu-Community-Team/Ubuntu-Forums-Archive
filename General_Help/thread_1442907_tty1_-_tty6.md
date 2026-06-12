---
title: "tty1 - tty6"
date: 2010-03-30
forum: General Help
---

### Post by Directive 4 on 2010-03-30
hi, when i go to tty 1 (ctrl alt f1)

i am unable to accers the cli.

it says.

ubuntu 9.10 directive 4 tty1

directive 4 login:

after i enter my username it asks for a password, i enter my password and after a few seconds
it says, login incorrect and goes back to the start, what am i doing wrong, thanks in advance for any answers.

---

### Post by vzomik on 2010-03-31
in theory&#65292;it is right 
and actually&#65292;it is right, too
but , are you sure the username is available and the passwd is correct ??
at last , is the username locked ??

---

### Post by Directive 4 on 2010-04-02
yea, so there is only one users, me.
i can log on to the gui, so why not here, 

how to check if it's locked?

---

### Post by Directive 4 on 2010-04-09
bump

---

### Post by Iowan on 2010-04-09
I presume you've checked the CAPSLOCK...

---

### Post by Directive 4 on 2010-04-09
yea, it's not that,

it's confusing,

it says 

directive4 login:


do i type directive4

if it allready knows it's me, why ask?

umm




it ends up like this


directive4 login:directive4
Password:

Login incorrect
directive4 login:






cheers for any help

---

### Post by ibuclaw on 2010-04-09
> **Directive 4 said:**
> 
directive4 login:directive4
Password:


directive4 is the hostname of your computer, I have a feeling that is also not the username you set when you installed the workstation either.

When in GUI, open a terminal: Applications->Accessories->Terminal

Then have a look at the prompt. It should have something like:
```
**user**@directive4:~$
```

Make a note of the user name (what comes before the '@') and use that instead as the username to login as.

Regards.

---

### Post by Directive 4 on 2010-04-09
> **ibuclaw said:**
> directive4 is the hostname of your computer, I have a feeling that is also not the username you set when you installed the workstation either.

When in GUI, open a terminal: Applications->Accessories->Terminal

Then have a look at the prompt. It should have something like:
```
**user**@directive4:~$
```Make a note of the user name (what comes before the '@') and use that instead as the username to login as.

Regards.


ha!

well done mate.

problem is fixed

thanks

---

