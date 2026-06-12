---
title: "Ubuntu Won't Recognize USB?"
date: 2009-10-01
forum: General Help
---

### Post by Arceux on 2009-10-01
Hi, I've got Ubuntu 9.04 Jaunty and whenever I insert my flash drive, or any flash drives Ubuntu doesn't show them. Just asking if anybody knows of a solution.

---

### Post by JC Cheloven on 2009-10-01
It is unusual, I never had a problem with this. Can you please plug your pendrive, wait some seconds, open a terminal (applications->accesories->terminal), and post the output of ```
lsusb
```

note.- to copy from terminal, select with the mouse and type ctrl-shift-c

---

### Post by MarkeyMark on 2009-10-01
I'm having the exact same problem with my Sandisk Sansa Fuze 8GB media player. This is my lsusb output:  > markadmin@MarksLaptop:~$ lsusb Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub markadmin@MarksLaptop:~$  

---

### Post by wilee-nilee on 2009-10-01
If you have nothing on the thumb drives and you have gone to home then computer to see if you can manually mount it, then reformat them with gparted called partition manager if this is not installed run sudo apt-get install gparted in the terminal. Format the to fat32.

---

### Post by JC Cheloven on 2009-10-01
@ MarkeyMark: In future occasions, perhaps you could try to put your info in a more readable manner, to help others help you. Something like:
> Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Well, nothing except a fingerprint reader is listed here. ¿does your device have a fingerprint reader, or is there anywhere in your system a fp reader?

---

### Post by Arceux on 2009-10-03
Here is my output.

thomas@loft-ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
thomas@loft-ubuntu:~$

---

