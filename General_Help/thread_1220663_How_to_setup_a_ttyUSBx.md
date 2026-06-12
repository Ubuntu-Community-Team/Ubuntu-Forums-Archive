---
title: "How to setup a ttyUSBx"
date: 2009-07-23
forum: General Help
---

### Post by Davlav on 2009-07-23
Hello,

I need to interface with some TTL USART RS-232 devices. As the PC 'only' has USB's, I use a USB/Serial converter for each device.

I have found several docs on ttySx, but none for ttyUSBx's.

I'm programming the software on C++ (compiled on g++). Right now, I use the port as a file, but I could change it if advised otherwise. 

I would need to setup de speed of the port, to send/flush when asked, and to receive interruptions on reception. Exactly as I would do with a microcontroller (but I need it on a Linux box).

- I use "stty -F /dev/ttyUSBx <<the baudrate>>" to setup the velocity, but it is not much robust and doesn't work at 38400 bauds, for instance.

- I "myfile.flush();" so that it sends what is contained on the buffer, but the microcontroller receives it noticeably later (on WinXP it is faster! :().

- I have to waste CPU cycles polling for the input...

How could I achieve that?

What would you advise?

Any suggestions are most welcome!

Best regards,

David

---

