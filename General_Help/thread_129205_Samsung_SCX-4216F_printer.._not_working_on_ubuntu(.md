---
title: "Samsung SCX-4216F printer.. not working on ubuntu(i have installed the driver anyway)"
date: 2006-02-13
forum: General Help
---

### Post by hak on 2006-02-13
ports names in linux are different from those on windows.. that is why i am having a trouble in printing a test page after installing the driver for that printer..
it always fails to connect to the printer since the port designated is wronge..

i went to the properties of that printer, provided it with the name of the printer but for the port i have the following options:

**Parallel:**
/dev/mfp0
/dev/mfp1
/dev/mfp2
/dev/mfp3

**USB**
/dev/mfp4
/dev/mfp5
/dev/mfp6
/dev/mfp7
/dev/mfp8
/dev/mfp9
/dev/mfp10
/dev/mfp11
/dev/mfp12
/dev/mfp13
/dev/mfp14

i dont know what port shall i choose i tried almost all of of them but it always fails to open the port and consequently it does not print...

so what to do?? any ideas???

---

### Post by hulleye on 2006-04-18
Hi, have you had any luck with the SCX-4216f since your last post? I am facing the exact same problem as you. I have installed the driver and got the same error msg, so I installed CUPS but did not try re-installing the driver (you stated that it gave the same error msg regardless).

Ubuntu seems to communicate with the printer and it even states "Printing..." on the printer itself, but no pages are actually printed :(

anyone have any idea what's going on?

---

### Post by hulleye on 2006-04-19
hak, i don't know if this will work but just saw a post on linxprinting.org that states if there are no other USB printers plugged in, the port to use would be /dev/usb/lp0 

will give it a try later today

---

