---
title: "How to find out the mac address of your wireless card"
date: 2012-02-14
forum: General Help
---

### Post by TheKismet on 2012-02-14
I would like to find out the mac address of my internal wireless card. Do you know how to do it? Thanks in advance.

---

### Post by HiImTye on 2012-02-14
you should be able to get it using
```
ifconfig
```

---

### Post by TheKismet on 2012-02-14
thanks

---

### Post by Khayyam on 2012-02-14
TheKismet ..

Firsty is the wireless-tool package installed? If not then ..[FONT=monospace] 

[/FONT]```
apt-get install wireless-tools
```[FONT=monospace]

[/FONT]You can then use the command 'ip' which will show the MAC[FONT=monospace]

[/FONT]```
ip addr
```HTH ..[FONT=monospace]
[/FONT]

---

