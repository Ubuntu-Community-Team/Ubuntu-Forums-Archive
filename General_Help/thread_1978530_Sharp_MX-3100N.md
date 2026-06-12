---
title: "Sharp MX-3100N"
date: 2012-05-11
forum: General Help
---

### Post by Ubun2to on 2012-05-11
My dad is having me redo his network, but he has to keep some Windows stuff. Anyway, I'm having trouble installing the Sharp MX-3100N drivers (the printer is hosted on Windows, by the way).
The drivers require root access, which I have no idea how to get. I've tried everything I've found, but nothing has worked.
I've tried the CUPS drivers, which haven't worked, the Samba option on the Printing menu, and just about everything else I can think of.
Please help.

---

### Post by lisati on 2012-05-11
> **Ubun2to said:**
> 
The drivers require root access, which I have no idea how to get. 


Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Ubun2to on 2012-05-11
> **lisati said:**
> Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I found that link on another post, but I can't install it. This is what I type in:
```
gksudo install /home/mynamehere/Downloads/MXColor-PPD-1.2-Linux/setup
```
This is what I get:
```
Failed to run install '/home/namehere/Downloads/MXColor-PPD-1.2-Linux/setup' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.
```
Why is this?

---

