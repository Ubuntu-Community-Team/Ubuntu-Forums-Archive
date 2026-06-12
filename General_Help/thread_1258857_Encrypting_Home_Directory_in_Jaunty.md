---
title: "Encrypting Home Directory in Jaunty"
date: 2009-09-05
forum: General Help
---

### Post by mac9416 on 2009-09-05
Hello, all!

I am wondering if and how it is possible to encrypt my home directory in Jaunty without reinstalling using the alternate disc.

Thanks in advance!
-mac

---

### Post by ddrichardson on 2009-09-05
Dustin Kirkland led a session on this during OpenWeek:

[https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/EncryptHome](https://wiki.ubuntu.com/MeetingLogs/openweekJaunty/EncryptHome)

---

### Post by mac9416 on 2009-09-05
ddrichardson, thanks much for the reply. That's exactly what I need. Unfortunately, much of what I would need to know to follow those instructions could only be seen by users who were watching him work via SSH. Hopefully he has posted somewhere what exactly he did.

---

### Post by mac9416 on 2009-09-05
And here is it!: [http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html](http://blog.dustinkirkland.com/2009/06/migrating-to-encrypted-home-directory.html)

---

### Post by ScorpKing on 2009-09-05
One way of doing it is to use a loopback encryted disk/partition/directory and have the password read from a USB drive during boot. Saves you from typing a very long password every time you reboot. Using this method it is also possible to use a normal document/letterhead for a password and use sed to extract the password from it.

Here is the info how to set it up --> [http://www.scorpking.za.org/encryption](http://www.scorpking.za.org/encryption)

---

### Post by ddrichardson on 2009-09-05
FWIW, Karmic has encrypted home folder support.

---

