---
title: "Display problem in ubuntu 9.10"
date: 2010-01-03
forum: General Help
---

### Post by ramvibhakar on 2010-01-03
Hi,
     I tried installing ubuntu 9.10 using live CD. But when i boot into live mode nor try installing i get coloured lines on the screen as shown in attachements. So i downloaded dvd version of the ubuntu 9.10 and installed it in text mode. After successful installation i cannot boot into ubuntu. I get the same problem of display after the ubuntu loading screen. Pls help me fix this problem. I'm a newbie.

     My system configuration is :

AMD Athlon x2 5000+
Asus m2n68-am mainboard
geforce 7050 pv/nvidia nforce 630a
2 gb RAM

---

### Post by Leppie on 2010-01-03
try installing the nvidia drivers:
```
$sudo apt-get install nvidia-glx-185
```

---

### Post by ramvibhakar on 2010-01-04
Thanks for the reply Leppie. But it didn't solve my problem. Any other methods to solve..

---

### Post by realzippy on 2010-01-04
..have you run:

**sudo nvidia-xconfig**

and restarted X?

---

### Post by ramvibhakar on 2010-01-08
Thanks for your great reply and sorry for my late reply.. It worked.. And I'm now enjoying karmic koala.. Thanks again..

---

