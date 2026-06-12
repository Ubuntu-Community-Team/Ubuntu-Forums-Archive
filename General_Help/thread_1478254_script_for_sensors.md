---
title: "script for sensors"
date: 2010-05-09
forum: General Help
---

### Post by pyrforos on 2010-05-09
hi guys! im trying to make a little script so i can export some data to a txt file , updated every 30 sec.

```
#!/bin/bash

first_entry=$(sensors |grep 'CPU Temperature' |cut -b 23,24,25,26) 
second_entry=$(sensors |grep 'MB Temperature:' |cut -b 23,24,25,26)
third_entry=$(sensors |grep 'temp1:'|cut -b 7,15,16,17,18,21)

while true

do 

echo " Cpu temp ${first_entry} C,M/B temp ${second_entry} C ,temp1 ${third_entry}">/home/user/dmesg
sleep 30
done
```

For some reason the dmesg file remains the same no matter what.Only if i restart the script gets updated..
Any solutions?

---

### Post by dino99 on 2010-05-09
maybe into programming forum you find more help

---

### Post by jobix on 2010-05-09
You need to pull that part where you have "first_entry = ...." etc into the while loop otherwise it will never get updated. Move all three lines into the loop.

---

### Post by pyrforos on 2010-05-09
THANK YOU! worked like a charm!

---

### Post by tgalati4 on 2010-05-09
I use gnome-applets with the taskbar temperature monitor.  It has an automatic logging facility and the ability to send alerts when temperatures get too high.

sudo apt-get install gnome-applets
right-click on the task bar, add-to-panel, select temperature monitor

---

