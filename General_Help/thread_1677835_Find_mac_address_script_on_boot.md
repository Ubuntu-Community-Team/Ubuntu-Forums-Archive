---
title: "Find mac address script on boot?"
date: 2011-01-29
forum: General Help
---

### Post by Deadmode on 2011-01-29
I work at a University and every year or every other year we get new computers for the campus. More often than not it is my job to document the mac address for each PC. I'm trying to save myself time when I have to do this again. Can I make a script to find the mac address on boot up? Or perhaps I should make a customized distro of linux? Booting off of usb would be ideal. How should I approach this?

---

### Post by tredegar on 2011-01-29
**ifconfig | grep HWaddr**
Will tell you what you want to know.

You could make a USB ubuntu stick that auto-logged you in and then ran that command in a terminal window. 

Or you could make it prettier with **zenity**```
ifconfig | grep  HWaddr | zenity --title "Detected MACs" --text-info --width 500

```
Or.....

---

### Post by Habitual on 2011-01-29
the "script" is already there.
```
dmesg | grep eth0 | grep IRQ
```

---

