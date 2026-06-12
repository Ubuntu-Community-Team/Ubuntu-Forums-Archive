---
title: "serial card problem on ubuntu 9.10"
date: 2010-07-10
forum: General Help
---

### Post by jakjok on 2010-07-10
i have serial card 6s port  on ubuntu 9.10 
just three of it is work

i read about this and know just 4 serial port is work 

i have serial port on motherboard and 6 port on serial card

and as i saying just three of it is work 

Mknod /dev/ttyS4 C 4 68
but when i try 
setserial /dev/ttyS4 uart 16550a


the result is:

/dev/ttyS4: No such file or directory



please help

---

