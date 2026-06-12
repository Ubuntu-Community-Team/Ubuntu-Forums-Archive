---
title: "Skype trouble--error message"
date: 2011-05-26
forum: General Help
---

### Post by sewbiz on 2011-05-26
When I go to a terminal to start Skype....because my version 11.04-Natty is not working right. I have no other way to launch anything!  It gives me an error message.  How do I correct this? Please help. I'm a noob. :(


Error: "/var/tmp/kdecache-cathy" is owned by uid 1000 instead of uid 0.

---

### Post by Habitual on 2011-05-27
open a terminal and type:
```
chown root /var/tmp/kdecache-cathy
```

Start skype from terminal to verify (error) messages.

If that still fails try and move the file, it will NOT hurt your Skype profile...
```
sudo mv /var/tmp/kdecache-cathy /var/tmp/kdecache-cathy.org
```

Start skype from terminal to verify (error) messages.

---

### Post by wildmanne39 on 2011-05-27
> **sewbiz said:**
> When I go to a terminal to start Skype....because my version 11.04-Natty is not working right. I have no other way to launch anything!  It gives me an error message.  How do I correct this? Please help. I'm a noob. :(


Error: "/var/tmp/kdecache-cathy" is owned by uid 1000 instead of uid 0.
Hi, you say natty is not working right what is it doing? Have you installed drivers for video card? are you using desktop effects? Have you tried to use the cube?, what are your system specs? Also you can log out click on user name go to the bottom of the screen and click on ubuntu classic with no effect and see if that helps.:p

---

