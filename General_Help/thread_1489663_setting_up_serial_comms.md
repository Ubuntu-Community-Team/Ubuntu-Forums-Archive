---
title: "setting up serial comms"
date: 2010-05-21
forum: General Help
---

### Post by radcom on 2010-05-21
I am wanting to set-up serial communications between my server (ubuntu 9.04) and a picaxe chip (a pic with a bootloader) I need to send data in the format of "1,1,1" or "1,1,0" at 9600 baud 8 data bits, no parity, 1 stop bit and no flow control. the data must be sent as numbers not ASCII I have tried ```
echo 1,1,0 > /dev/ttyS0
``` if anyone could help me with a simple shell script or even python I would greatly appreciate it.

---

### Post by radcom on 2010-05-21
any suggestions

---

### Post by BigMamma on 2010-05-21
You might consider using gtkterm.  It's a pretty straight-forward GUI tool that lets you connect directly to your serial port(s).

---

### Post by iponeverything on 2010-05-21
minicom is also a good terminal program.

---

### Post by radcom on 2010-05-21
I need to send the data from a shell script or python script that I can invoke and pass the data as a variable to it, as the data is coming from a php script. But that GtkTerm is great though 
if some one could post how to set /dev/ttyS0 up for 9600,8,N,1 that would be fantastic as I have looked on google but am confused by how to do it?

---

### Post by cariboo on 2010-05-21
I haven't play with serial communications for quite a while, but have a look at:

```
man setserial
```

for the parameters you need to setup.

---

### Post by radcom on 2010-05-21
That doesn't let me set the settings I need to set, that is to do with IRQs and interrupts the port works but just not at the right settings

---

### Post by iponeverything on 2010-05-21
> **radcom said:**
> That doesn't let me set the settings I need to set, that is to do with IRQs and interrupts the port works but just not at the right settings

cu ?

---

### Post by dcstar on 2010-05-22
```
man getty
```

---

