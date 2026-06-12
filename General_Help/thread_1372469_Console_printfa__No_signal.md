---
title: "Console printf\a : No signal"
date: 2010-01-04
forum: General Help
---

### Post by 010101 on 2010-01-04
I wrote a c console-programme with should output a system beep.But I cannot hear any sound.Which setting of Ubuntu avoid the beep.
Please answer.

---

### Post by cariboo on 2010-01-04
If you are running Jaunty or later, the pc speaker driver is blacklisted. The blacklist is in /etc/modprobe.d. In Jaunty it is just called blacklist, in Karmic it is called blacklist.conf.

Open the file in a text editor, press Alt-F2 and type 

```
gedit /etc/modprobe.d/blacklist.conf
```

and comment out **snd_pcsp**

install the module by opening a terminal and typing:

```
sudo modprobe snd_pcsp
```

Doing this may cause a confilct with your sound card. If it does you can just uncomment the entry and remove the module:

```
sudo rmmod snd_pcsp
```

---

### Post by 010101 on 2010-01-09
It didn't work.
Do I have to have a beeper on my motherboard if I want to generate a system beep?
Because I'm not sure if my motherboard has one.My computer is a netbook.

---

