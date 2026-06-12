---
title: "How can i get 'Ipconfig' Infos?"
date: 2010-05-11
forum: General Help
---

### Post by GoldyW on 2010-05-11
I am a beginer on Ubuntu.

On Windows command window, i can type 'IpConfig' to get network infos

How can i do it on Ubuntu ?

thanks.

---

### Post by chappajar on 2010-05-11
ifconfig

---

### Post by karthick87 on 2010-05-11
To view network infos,type

```
**ifconfig**
```To view wireless infos,type

```
**iwconfig**
```To scan for wireless networks

```
**iwlist scan**
```To restart network connections

```
**/etc/init.d/networking restart**
```To enable interface

```
**ifup eth0**
```To disable interface

```
**ifdown eth0**
```

---

### Post by GoldyW on 2010-05-11
thanks,.. good

---

### Post by zaphod777 on 2010-05-11
also 

```
route
```

will show you default gateway info

---

