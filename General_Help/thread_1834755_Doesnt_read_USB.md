---
title: "Doesnt read USB?"
date: 2011-08-28
forum: General Help
---

### Post by QuantumMonkey on 2011-08-28
I just put in my USB stick, waited a couple minutes, and nothing happened. Does Ubuntu just not recognize USB's? Or am I doing it wrong? :s

---

### Post by QuantumMonkey on 2011-08-28
:( I need helppp :P

---

### Post by QuantumMonkey on 2011-08-28
What a helpful bunch of people you are. -.-

---

### Post by dino99 on 2011-08-28
oh , you request help ? but without knowledge about your system config and hardware, its quite useless.
So to get good answer, first send usefull question, thats it.

how are usb settings inside the bios ?

---

### Post by haqking on 2011-08-28
> **QuantumMonkey said:**
> What a helpful bunch of people you are. -.-

Support here is free and at disgression, not getting a respone in a couple of hours is quite normal

Attitude adjustment first then people might be more helpful ;-)

---

### Post by fdrake on 2011-08-28
open the terminal and run:
```
lsusb
dmesg | grep usb
less /etc/fstab

```

copy and paste the outputs in your posts. 

ps.Your question is too generic that's why ppl don't answer. It's like asking "who am I?".

---

### Post by OmerTatar on 2011-08-28
fdisk -L

Copy the output...I had the same situation with usb flash memory stick..it was previously plugged to Windows machine infected by tones of viruses...well that was on Centos 5...

---

### Post by fdrake on 2011-08-28
> **OmerTatar said:**
> fdisk -L

Copy the output...I had the same situation with usb flash memory stick..it was previously plugged to Windows machine infected by tones of viruses...well that was on Centos 5...

> fdisk -L 

it should be
```

sudo fdisk -l

```
l lowcas (linux is case sensitive) ;)
sudo (you need root privileges to run fdisk)

---

