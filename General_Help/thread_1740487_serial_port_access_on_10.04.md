---
title: "serial port access on 10.04?"
date: 2011-04-27
forum: General Help
---

### Post by kin37ik on 2011-04-27
ive been looking through several online documents and forum posts but i cant get a clearcut answer on how to set up serial port acces in ubuntu 10.04 (server), could anyone help out?

---

### Post by elliotbeken on 2011-04-27
have you tried using minicom ?

---

### Post by Lars Noodén on 2011-04-27
There is also a program called [cu](http://linux.die.net/man/1/cu) that you can use.

e.g.

```

cu -s 19200 -l /dev/ttyUSB0

```

---

### Post by kin37ik on 2011-04-27
well ive tried using minicom but i could not get into my SPARC server and heard that i need to enable serial port access by adding a line or two to a certain file?

ill try cu but im hoping it doesnt go the same way that minicom did

---

### Post by kin37ik on 2011-04-29
cu didnt work for me either, any other ideas? :S

---

### Post by Lars Noodén on 2011-04-29
> **kin37ik said:**
> well ive tried using minicom but i could not get into my SPARC server and heard that i need to enable serial port access by adding a line or two to a certain file?

ill try cu but im hoping it doesnt go the same way that minicom did

What are the serial settings for your server. (e.g. 9600bps, 8, N, 1,)  What you feed cu has to match what it will get.

---

### Post by kin37ik on 2011-04-30
i dont know what the serial settings for the SPARC server are as i got it with no documentation or anything like that, ive looked at some PDF's via google but the only thing they describe for serial settings is using dev/ttyA or dev/ttyB, it doesnt specify the bitrate's or anything else for it  :S

---

### Post by Lars Noodén on 2011-05-01
> **kin37ik said:**
> i dont know what the serial settings for the SPARC server are

It's probably 8N1 at one of the following speeds: 9600, 19200, 38400, 57600 or 115200

---

