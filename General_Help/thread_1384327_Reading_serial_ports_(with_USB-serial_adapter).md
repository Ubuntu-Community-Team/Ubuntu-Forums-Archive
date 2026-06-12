---
title: "Reading serial ports (with USB-serial adapter)"
date: 2010-01-18
forum: General Help
---

### Post by erratosthenes on 2010-01-18
Hello All , 
I am an Ubuntu newbie and am trying to develop a serial port application to communicate with a bluetooth device. 
To begin with, I have read all online (well, most !!) resources about this and there is surely no dearth of those either. I have put together a code that works just fine for writing binary data to the device. (I have tested this using cutecom)
The trouble is with reading the reply from the device. For example, if I issue a binary reset request, I am supposed to get a standard reply from the device which I am unable to read. 
I have tried using "fcntl(2)" to change the file descriptors as well as various "open(2)" options. 
Is there any reason why the "read(2)" should return EAGAIN for most of my requests :confused:? 
I would like to hear from any experiences out there. 

Thank you so much for your time....

Cheers

-E

---

