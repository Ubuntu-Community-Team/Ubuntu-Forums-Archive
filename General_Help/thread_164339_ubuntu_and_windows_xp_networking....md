---
title: "ubuntu and windows xp networking...??"
date: 2006-04-22
forum: General Help
---

### Post by JohnnyHaff on 2006-04-22
how can i network my ubuntu with my existing windows xp network??

---

### Post by AndyCooll on 2006-04-22
You need to use Samba.

[Setting Up Samba]("https://wiki.ubuntu.com/SettingUpSamba?highlight=%28samba%29")

:cool:

---

### Post by Computeruser on 2006-04-22
I just put correct and appropriate information into Places -> Connect to Server and eventually got Ubuntu to talk to my Windows host. Samba came installed on first load IIRC. A couple of things: (1) Samba defaults to MSHOME for workgroup (it calls it domain in places) - I changed smb.conf to default to WORKGROUP.  (2) When identifying your Windows machine, don't use the traditional Windows backslashes. So in Connect to Server, enter Windows Share as service type, enter your Windows machine name (bobscomputer) under server, and enter C$ as share. Then authenticate and try to connect. I had to play with it a bit, but it works fine on my Desktop and on my Laptop.  Good Luck.

---

