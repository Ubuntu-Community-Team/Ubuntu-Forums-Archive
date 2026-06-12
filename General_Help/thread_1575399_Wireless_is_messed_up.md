---
title: "Wireless is messed up"
date: 2010-09-15
forum: General Help
---

### Post by Denton Larson on 2010-09-15
Hi everybody

I have a problem I think. I have Ubuntu 10.04 and a D-Link router, the wired is fine but the Ubuntu to my Dell mini-10 is goofed up.
The router is a dir-628 and it has the latest firmware in it.
This is what I get when I try to access google...
[http://dir-628.bsecure.com/newdevice.aspx?dmac=00:24:01:E2:10:8C&cmac=F0:7B:CB:32:49:0F&name=%27dlarson-lapdell%27&ip=192.168.0.247&deviceid=6&brandid=1&appid=7000703&url=%27http%3A%2F%2Fwww.google.com%2F%27](http://dir-628.bsecure.com/newdevice.aspx?dmac=00:24:01:E2:10:8C&cmac=F0:7B:CB:32:49:0F&name=%27dlarson-lapdell%27&ip=192.168.0.247&deviceid=6&brandid=1&appid=7000703&url=%27http%3A%2F%2Fwww.google.com%2F%27)

So i am at a loss to this.

Denton

---

### Post by barney385 on 2010-09-15
Does your wireless work elsewhere?

Have you made the necessary adjustments on your routers admin panel?

---

### Post by TwelveGauge on 2010-09-15
what do you get from 
```
iwconfig
```

---

### Post by Denton Larson on 2010-09-15
This is what I got, I don't know what it means.

---

### Post by Denton Larson on 2010-09-15
> **barney385 said:**
> Does your wireless work elsewhere?

Have you made the necessary adjustments on your routers admin panel?

It worked a few days ago, so I am stumped!

Denton

---

### Post by TwelveGauge on 2010-09-15
try: 
```
sudo ifconfig wlan0 up
```

---

### Post by Denton Larson on 2010-09-15
> **TwelveGauge said:**
> try: 
```
sudo ifconfig wlan0 up
```

I did try that and this is what I got

wlan0: ERROR while getting interface flags: No such device


Denton

---

### Post by barney385 on 2010-09-15
Which wireless card do you have?

Do you have the proper drivers activated?

Edit your wireless connections by deleting all entries and try again.

---

### Post by Denton Larson on 2010-09-16
SOLVED

I found it!

I turned off SECURESPOT in the router. It even was now in the wired side.

So now it is Solved!

Denton Larson

---

