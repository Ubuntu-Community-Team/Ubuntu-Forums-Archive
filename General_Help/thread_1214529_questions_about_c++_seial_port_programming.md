---
title: "questions about c++ seial port programming"
date: 2009-07-16
forum: General Help
---

### Post by devin0 on 2009-07-16
I have just started programming basic stamp microcontrollers from my ubuntu box. Everything is working fine now but I would like to make a C++ program to communicate with the stamp through the serial port and am unsure how. Can someone tell me how to go about this or give me a link to a good book or document explaining c++ serial communicatio?

---

### Post by JohnnySage50307 on 2009-07-16
I myself am currently tinkering with this, but you can communicate by doing a fprintf() to the /dev/ttyS#  where the #= your serial port number.
 
Now, mind you, this will send a character stream from the DTx line of your serial port.  Controlling RTX and CTX may require some different things.

---

