---
title: "ofono and telepathy-ring"
date: 2010-10-23
forum: General Help
---

### Post by ngiannakas on 2010-10-23
trying to make empathy work with telepathy-ring and ofono but it keeps trying to connect to it for ever, ofono it self works well with my Huawei K3715 using the tests from their site (sending SMS at least)

---

### Post by pranay.singh on 2012-01-17
> **ngiannakas said:**
> trying to make empathy work with telepathy-ring and ofono but it keeps trying to connect to it for ever, ofono it self works well with my Huawei K3715 using the tests from their site (sending SMS at least)
 
Hi, 
 
I want to start phonesim simulator on ubuntu 10.4 x86 environment. I had installed phonesim-1.16 on linux machine and also installed all dependencies. Edited the configure file /ofono/phonesim.conf as:
Enable following lines:
1| Driver=phonesim
2| Address=127.0.0.1
3| Port=12345
 
But, when i start the phonesim simulator by running below cmd then it will try to connect it for ever, never complete this command.
ofono-phonesim -p 12345 -gui /home/ofono/phonesim-1.16/src/default.xml
How can i open ofono simulator on ubuntu 10.40.
 
 
Regards,
Pranay Singh

---

