---
title: "Help with Serial Ports"
date: 2010-06-08
forum: General Help
---

### Post by maserowik on 2010-06-08
I am new to Ubuntu and having a some problems trying to get multiple serial ports woking. I have followed the instruction at [hxxp://lare-india.blogspot.com/2010/02/getting-serial-port-to-work-under.html]("http://lare-india.blogspot.com/2010/02/getting-serial-port-to-work-under.html"). All appeared to have worked. I then fired up my VM ( windows xp ) and tried to get the comport to be seen by the host OS, I am unable to get data from them
The host came from a working windows machine that use the comports with out any issues. 
 
here is my setserial display
m-host@vm-host:~$ setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
Cannot get serial info: Input/output error
/dev/ttyS2, UART: 16550A, Port: 0x2080, IRQ: 20
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
 
I am a complete Noob to Ubuntu. 
 
Thanks
Mike

---

