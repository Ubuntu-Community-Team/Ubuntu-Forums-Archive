---
title: "Unable to install rpm files"
date: 2006-04-05
forum: General Help
---

### Post by Gracye on 2006-04-05
I'm trying to install Igloo FTP but when I go to instlal the rpm nothing happens:
this is what i'm typing in:

 cd Desktop
sudo alien -i igloo.rpm

the deb file shows up and then disapears right away.  what am I doing wrong?

---

### Post by aysiu on 2006-04-05
Probably nothing. It sounds as if it's working, actually.
Can you post the exact terminal output?

---

### Post by JoshHendo on 2006-04-05
Type in:

cd Desktop
sudo alien igloo.rpm

Hopefully that will create the deb file, then you install that normally. That is the way I always to it :)

---

### Post by Gracye on 2006-04-05
I wasn't getting anything in the terminal after typing that in.

but I've tried the other way (taking the -I out) and it works now :) Thanks guys!

---

