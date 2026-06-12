---
title: "Allowing Computer to Accept ssh connections"
date: 2009-10-30
forum: General Help
---

### Post by teward on 2009-10-30
Okay this is just a question, but I'd really like to be able to use ssh to remote into my computer.  But when I do this:
```
$ ssh myUserName@myComputerIPaddress
```I get this returned:
```
ssh: connect to host myComputerIPaddress port 22: Connection refused
```So, how do I unlock port 22 within Ubuntu?

NOTE: I only use my computer's IP address because my computer's name is not recognized on my local network.

**EDIT: myUserName and myComputerIPaddress replace confidential information regarding my user account and system address.  I actually connect to the REAL IP address.**

---

### Post by Grim76 on 2009-10-30
Did you install openssh-server?

sudo apt-get install openssh-server

---

### Post by teward on 2009-10-30
It works.  Thanks!

---

