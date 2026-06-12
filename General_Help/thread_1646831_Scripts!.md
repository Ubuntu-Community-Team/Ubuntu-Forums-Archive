---
title: "Scripts!"
date: 2010-12-16
forum: General Help
---

### Post by Spyderkid on 2010-12-16
Is it possible to add some lines to my script to make it run after restarting the computer after updates?

---

### Post by Wim Sturkenboom on 2010-12-16
You can add the script itself to rc.local (script will be started at the end of the boot sequence at every boot). At least that used to be the way; never sure with Ubuntu if something that is long established still functions.

---

### Post by Spyderkid on 2010-12-17
that wouldn't work because the script makes the computer restart so it would be a neverending loop of restarting booting up and then restarting again.

---

### Post by QLee on 2010-12-17
[QUOTE=Spyderkid]Is it possible to add some lines to my script to make it run after restarting the computer after updates?[/QUOTE]
The way you have chosen to state this is somewhat confusing.

Wim Sturkenboom's reply to your post is correct for what you have written.

If what you meant was a script to restart your machine after updates, you won't need that, the package manager will trigger a restart if it is needed after updates and it will present you with the option to do so now or later in a dialogue box.

---

### Post by Wim Sturkenboom on 2010-12-17
Can you elaborate on your script. What does your script do and what do you want to achieve ?

---

### Post by Spyderkid on 2010-12-28
this is my script so far....

```
#!/bin/bash
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
cd driver
cd rtl8712_8188_8191_8192SU_usb_linux_v2.6.0006.20100226/
make clean && make 
sudo make install && sudo modprobe 8712u && echo "8712u" | sudo tee -a /etc/modules &&
echo "reboot?"

read answ
if [ "$answ" = "y" ]
then
        sudo reboot
else
        echo "ok"
fi
```

---

### Post by Sub101 on 2010-12-28
So you just want to run the script after updating the system?

---

### Post by Spyderkid on 2010-12-29
yes please. can you help with that?

---

### Post by Spyderkid on 2011-01-30
BUMP

(not to moderators, please post this I haven't got a reply in 4 weeks)

---

