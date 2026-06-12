---
title: "Sensors Applet displays only one sensor"
date: 2009-11-16
forum: General Help
---

### Post by gabe17 on 2009-11-16
Hi, I have installed Sensors Applet (with lm-sensors), but it displays only one sensors (HDD temp. sensor). How can I display more sensors? (MB, CPU, or FAN speeds etc.)

---

### Post by samuelhug on 2009-11-16
right click the applet > prefernces > sensors tab. Then click the enabled checkbox next to the sensors you want. If there are not any other sensors then run sudo sensors-detect

---

### Post by nikgare on 2009-11-16
Have you run **sensors-detect** ?

---

### Post by gabe17 on 2009-11-17
Of course, I've enabled all sensors which are in the list of sensors, but there ís only the HDD sensor. I've run detect-sensors, too.

---

### Post by nikgare on 2009-11-17
Did you get it to add the lines to /etc/modules for you, and did you reboot or modprobe the drivers?

Which sensors did sensors-detect find?

---

### Post by gabe17 on 2009-11-17
Yes I did (if you mean the last question that was it asking me), I did reboot Ubuntu. I don't know what is modprobe. It found only HDD temperature sensor.

---

### Post by ppeloton on 2009-11-17
Hi!

There's a thread about lm-sensors, from there I found possible solution :

"For 9.10, I had to add kernel option "acpi_enforce_resources=lax" to /etc/default/grub (2.x, or /boot/grub/menu.lst w/ grub 1.x)."

---

### Post by gabe17 on 2009-11-24
Please, could you send me the link on this thread?

---

### Post by ppeloton on 2009-11-24
Sorry for me being a bit inaccurate with the latest reply!
I can't locate this thread right now, but it's somewhere in ubuntuforums...

now about the lm-sensors...
try typing (in the terminal):
sudo gedit /etc/default/grub

and in the end of the file add line :
acpi_enforce_resources=lax

then save file, exit and type
sudo grub-update

and then reboot

hope this helps

---

### Post by gabe17 on 2009-11-25
I added the text on the end of the file, but if I try to run "sudo grub-update", it writes "command not found".

---

### Post by dcstar on 2009-11-25
> **gabe17 said:**
> I added the text on the end of the file, but if I try to run "sudo grub-update", it writes "command not found".
Try:
```
sudo grub-update2
```

---

### Post by Mr Pestle on 2009-11-27
sudo update-grub 
works for me :-)

---

### Post by gabe17 on 2009-11-28
Yes, sudo-update works, but it still hasn't found any sensors...

---

