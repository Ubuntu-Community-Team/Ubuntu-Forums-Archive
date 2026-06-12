---
title: "rt2870 wireless chipset"
date: 2011-02-02
forum: General Help
---

### Post by Rr2516 on 2011-02-02
This was working for me then it stopped working. The issue is I am unable to establish a connection over WPA2.

I have read every thread about this and none of it has helped.

I have taken the following steps.

download latest driver 

sudo rmmod rt2870sta

cd into driver directory

make

sudo make install

cd /os/linux

sudo insmod rt2870sta.ko

and now the driver works. BUT WAIT. Reboot. Now I have the same problem. 

Is there any way I can fix this, or at the very least, automate this whole thing?

thank you in advance

---

### Post by Bucky Ball on 2011-02-02
```
sudo su
make
make install
```Try that then reboot. Using:

```
sudo make
```... doesn't seem to work properly for some odd reason when installing my wireless driver at least.

---

### Post by Rr2516 on 2011-02-02
Man, I wish it was that easy. 

sudo su yields the same result.

---

