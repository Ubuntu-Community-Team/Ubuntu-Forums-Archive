---
title: "type to xorg.conf from command prompt [ 10.10 not booting ]"
date: 2010-12-26
forum: General Help
---

### Post by Mecasickle on 2010-12-26
Hey guys,

Just found a thread that could help my booting problem (conflict from Nvidia graphics card and default graphics card, that wont let me log on to my GUI screen.)

Part of the instructions say that I should add some lines on the xorg.conf file:

Section "ServerFlags"
Option "IgnoreABI" "True"
End Section

all I can think of is:
sudo cat>>/etc/X11/xorg.conf

but its giving me an error message.
Any other way of trying to add text to the xorg.conf file *Without* a GUI (my desktop isnt popping up..)?

---

### Post by susema on 2010-12-26
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

---

### Post by Mecasickle on 2010-12-26
Hmm..
can't type anything, still stuck in the command prompt!
 Any other ideas?

---

### Post by Claus7 on 2010-12-26
Hello,

1) ```
lspci | grep VGA
``` for start... Just paste here the outcome.

2) what errors do you get? are you having problems adding those lines in xorg.conf, or after a reboot? 

3) post your xorg.conf file here, so as to give us a clue on what is going on...

4) have you activated any proprietary drivers for your system? 

5) when you say that your desktop is not popping up, do you end up facing a black command prompt screen?

Regards!

---

### Post by Claus7 on 2010-12-26
...

> **Mecasickle said:**
> Hmm..
can't type anything, still stuck in the command prompt!
 Any other ideas?

since you are left with command prompt you can navigate anywhere on your system and do many things. I would recommend the vi(m) editor for changing things. In case you tamper with xorg (and I guess you are going to do it sooner or later) just keep a backup of your original files. 

Regards!

---

### Post by oldos2er on 2010-12-26
The nano editor is fairly simple to use: ```
sudo nano /etc/X11/xorg.conf
```

Edit: If you're booted into recovery mode, you can forego "sudo"

---

