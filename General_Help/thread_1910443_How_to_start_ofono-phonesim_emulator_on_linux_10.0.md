---
title: "How to start ofono-phonesim emulator on linux 10.04"
date: 2012-01-17
forum: General Help
---

### Post by pranay.singh on 2012-01-17
[COLOR=black][FONT=Verdana]Hi, 

I want to start phonesim simulator on ubuntu 10.04 x86 environment. I had installed phonesim-1.16 on linux machine and also installed all dependencies. Edited the configure file /ofono/phonesim.conf as:
Enable following lines:
1| Driver=phonesim
2| Address=127.0.0.1
3| Port=12345

But, when i start the phonesim simulator by running below cmd then it will try to connect it for ever, never complete this command.
ofono-phonesim -p 12345 -gui /home/ofono/phonesim-1.16/src/default.xml
How can i open ofono simulator on ubuntu 10.04.


Regards,
Pranay Singh[/FONT][/COLOR]

---

