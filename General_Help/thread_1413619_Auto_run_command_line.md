---
title: "Auto run command line"
date: 2010-02-22
forum: General Help
---

### Post by Hyperactiveman on 2010-02-22
Hi there!

I've Ubuntu installed on a SD card running on my Eee PC 1000H and have to type in, everytime after startup, this line:

```
sudo hdparm -B 1 -S 1 /dev/sda
```

to turn off the noisy HDD. How can I auto execute this command?! *System>Startup Applications* didn't work.

THX in advance

---

### Post by 542 on 2010-02-22
You could add the line into /etc/rc.local which is a file that is run by root at the end of the boot process.

You shouldn't need the sudo part of the command as it will run as root anyway.

so...
```
sudo gedit /etc/rc.local
```

And somewhere above the 'exit 0' line add as a new line: 
```
hdparm -B 1 -S 1 /dev/sda
```

Prehaps there is a better place to put drive configuration stuff, but this should work.

---

### Post by Hyperactiveman on 2010-02-22
Thanks for the quick reply, works perfect! Merci! :D

---

### Post by Schwingi on 2010-02-23
Another issue occured.

When I fire my Eee PC up after suspend mode, the HDD "awakes" again and I have to disable it again per terminal. Where can I place: 

```
hdparm -B 1 -S 1 /dev/sda 
```

that it will run automatically after activating from suspend mode?

---

