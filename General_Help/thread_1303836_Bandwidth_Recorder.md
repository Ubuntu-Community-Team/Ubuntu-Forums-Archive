---
title: "Bandwidth Recorder"
date: 2009-10-28
forum: General Help
---

### Post by Monotoko on 2009-10-28
Hiya :)

Im after a program which will record how much bandwidth i use because our ISP have put us on a quota.

This quota is 40GB a month, so i need to ensure that im never going above that or we get charged a lot.

Is there anything that I can run in the background that will add up how much bandwidth I'm using? This might be asking a lil bit too much, but could it also cut me off after say...1.5GB a day?

If there isnt such a thing, would someone mind pointing me in a direction to program such a thing? Language etc

~Daniel

---

### Post by CharlesA on 2009-10-28
Are you using a linux box as a router/NAT? If so, you can check out system monitor for data transferred/received.

---

### Post by Monotoko on 2009-10-28
Nahh we have a router downstairs, i just need it to watch the amount of data that comes into and goes out of my laptop

---

### Post by Giblet5 on 2009-10-28
There's no graphical tool that I know of, but the ifconfig command will show the read/written stats since the interface was enabled.

List your network interfaces. Open a terminal and enter ```
ifconfig
```

Let's assume we're using eth0, but you use what you have.

```
ifconfig eth0
```

See the RX bytes and TX bytes? You could use that.

You can reset those values via ```
sudo ifdown eth0
sudo ifup eth0
sudo /etc/init.d/networking restart
```

(again, substitute your actual interface for eth0)

---

### Post by Monotoko on 2009-10-28
Ahha! Thank you for the very informative post, that was precisely what i was looking for...i assume that RX is download and TX is upload?

How would i go about making this script run every 5 minutes and recording what it has somewhere? Something to do with Cron i should assume?

---

### Post by OpenGuard on 2009-10-28
```
sudo apt-get install vnstat

```
Project: [http://humdi.net/vnstat/](http://humdi.net/vnstat/)

---

### Post by CharlesA on 2009-10-29
> **OpenGuard said:**
> ```
sudo apt-get install vnstat

```
Project: [http://humdi.net/vnstat/](http://humdi.net/vnstat/)

Thanks for the link. That sounds quite handy. :-)

---

### Post by Monotoko on 2009-10-29
very handy thank you :)

Solved :D

---

