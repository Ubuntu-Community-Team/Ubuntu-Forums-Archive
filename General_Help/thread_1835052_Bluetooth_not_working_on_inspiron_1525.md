---
title: "Bluetooth not working on inspiron 1525"
date: 2011-08-28
forum: General Help
---

### Post by arunharidas on 2011-08-28
hi,
bluetooth not working on my dell inspiron 1525. I have read many posts but nothing could solve my problem. There is a 'x' mark on the bluetooth icon on the task bar. 
```
~$ sudo dellWirelessCtl --sw_bt 1 --bt 1

Set runtime settings for Bluetooth

Set runtime switch settings for Bluetooth

Radio Status for Bluetooth:
	Bluetooth enabled at boot
	Bluetooth supported
	Bluetooth enabled
	Bluetooth installed
	Bluetooth controlled by wireless switch at boot
	Bluetooth runtime switch control currently enabled
	Status Code: 0

```

help me please, thanks in advance.

---

### Post by LowSky on 2011-08-28
open terminal type this command:
```
sudo service bluetooth restart
```

---

### Post by arunharidas on 2011-08-29
> **LowSky said:**
> open terminal type this command:
```
sudo service bluetooth restart
```

```

~$ sudo service bluetooth restart

 * Stopping bluetooth     [OK]                                          
 * Starting bluetooth     [OK]         
```

but nothing happens new, everything the same.

---

### Post by arunharidas on 2011-08-29
so no help ?

---

### Post by arunharidas on 2011-09-04
Hi friends,
finally I got the bluetooth working!!! ... i just found the solution from this thread
[http://ubuntuforums.org/archive/index.php/t-1653435.html](http://ubuntuforums.org/archive/index.php/t-1653435.html) ...
I tried it on vista through virtual box, when i installed the driver which said by **Xanko** on vista through virtual box suddenly the bluetooth light began to glow and started working

---

