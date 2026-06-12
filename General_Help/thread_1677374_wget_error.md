---
title: "wget error"
date: 2011-01-28
forum: General Help
---

### Post by Spyderkid on 2011-01-28
I ran this and got an error 404 why did i get that and i think its a internet error not a computer error

```

---@Ubuntu:~$ wget http://samiux.volospin.com/rtl8192SU_usb_linux_v2.6.0006.20100226.zip
--2011-01-28 21:04:50--  http://samiux.volospin.com/rtl8192SU_usb_linux_v2.6.0006.20100226.zip
Resolving samiux.volospin.com... 173.236.134.147
Connecting to samiux.volospin.com|173.236.134.147|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-01-28 21:04:51 ERROR 404: Not Found.


```

---

### Post by QLee on 2011-01-28
> **Spyderkid said:**
> I ran this and got an error 404 why did i get that and i think its a internet error not a computer error

```

---@Ubuntu:~$ wget http://samiux.volospin.com/rtl8192SU_usb_linux_v2.6.0006.20100226.zip
--2011-01-28 21:04:50--  http://samiux.volospin.com/rtl8192SU_usb_linux_v2.6.0006.20100226.zip
Resolving samiux.volospin.com... 173.236.134.147
Connecting to samiux.volospin.com|173.236.134.147|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
2011-01-28 21:04:51 ERROR 404: Not Found.


```

I don't know where you got the URL but wget is telling the truth, that zip file you want is not there.

---

### Post by plucky on 2011-01-28
Try this ```
wget http://sites.google.com/site/solidpace/rtl8712_8188_8191_8192SU_usb_linux_v2.6.0005.20091112.p4.zip
```

Found [Here](http://ubuntuforums.org/showthread.php?t=1374037)

Good Luck

---

### Post by Spyderkid on 2011-01-29
thanks plucky :)

---

