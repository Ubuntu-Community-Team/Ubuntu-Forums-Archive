---
title: "Serial Communication"
date: 2011-04-28
forum: General Help
---

### Post by nav09 on 2011-04-28
Hi, 

I am working on UART device driver. Before coding i need to check wether the serial port is working or not, so I am trying to do loop back via MINICOM, it is unable to echo the character what i type. 

I have stucked up here..please suggest me what to do now.

Regards, 
Naveen.

---

### Post by lkraemer on 2011-04-28
**DISCOVER the COMM PORT:**
To locate the possible used COMM PORTS in Ubuntu, cut and paste the following command:
```

ls -l /dev/ttyS*

```

Notice that ttyS0 through ttyS3 are defined as shown

crw-rw---- 1 root dialout 4, 64 2009-11-27 15:26 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 2009-11-27 15:26 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 2009-11-27 15:26 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 2009-11-27 15:26 /dev/ttyS3

Running this command will determine the Baud rate of the Port:
```

stty -F /dev/ttyS5 -a

```
and to change it to 300:
```

stty -F /dev/ttyS5 300
stty -F /dev/ttyS5 -a

```

If you have a DTE (Terminal versus DCE) you can connect Pin 2 (TX) to
Pin 3 (RX) to ECHO back what you transmit.  You may also have to Jump
Pin 4 to 5, and Pin 6 to Pin 8 to Pin 20 to complete the NULL Modem
configuration, if it doesn't Transmit.

```

echo Testing.... > /dev/ttyS5

```
Which proves characters were routed out to Pin 2 and back on Pin3.

lk

---

