---
title: "Root Admin Issues."
date: 2010-07-06
forum: General Help
---

### Post by fasteddiedwards on 2010-07-06
Greetings;
I am new to Ubuntu 10.04 and have a problem with loading the Linux printer drivers for my new Lexmark printer.
When I try to load up the printer driver downloaded from the Lexmark site I am asked to enter a root administrator password, but when I enter the password I used to setup the OS it will not accept it.
I have reviewed the "sudo" terminal password info, but as I am a newbie I was concerned about wrecking the installation.
Is there any way to correct this problem?
Thanks

---

### Post by wilee-nilee on 2010-07-06
Have you looked in system-admin-printer to see if there is a onboard driver?

---

### Post by WorMzy on 2010-07-06
Check your caps-lock key, your sudo password is the same as your login password, if it's not being accepted then you are probably either 1) inputting it wrong, or 2) inadvertently typing it all in capitals due to caps-lock.

---

### Post by fasteddiedwards on 2010-07-09
Thanks for you help guys;
I tried both suggestions but to no avail.
However I did notice that the driver from Lexmark does not list 10.04 support yet, perhaps that's the issue. I may have to wait a while for them to catch up.

---

### Post by matey3 on 2010-07-09
do
 sudo passwd root
to change/set root's password.
then try to run the printer drivers.

but usually linux finds the drivers and installs them for you, I downloaded my wireless NIC drivers but still they did not help. only running the updates fixed the problem!

---

