---
title: "Ubuntu 11.04 on asus eee pc 1001pxd netbook"
date: 2011-09-01
forum: General Help
---

### Post by QuickSphinx on 2011-09-01
Hi Everyone,

I recently tried to install Ubuntu 11.04 (32bit) on my new asus netbook - everything went fine... Until I wanted to reach the internet. It is not picking up the hardline ethernet connection, and when I try to connect to my home wifi the computer lags up so severely that I need to re-install Ubuntu (as it continues to try to connect to the wifi every time I start it up).

The only linux drivers I could find were for upgrading the bios.

Any help is appreciated.

---

### Post by CrusaderAD on 2011-09-01
Hm, I have an eee PC HA100 (or something like that) and it works great. Do you have these problems with the live cd? If so, it's not your installation. Maybe find out what the make and model of the ethernet adapters are, see what support is out there for them. I would try out the live cd tho, see if it works then. If it does, reinstall.

---

### Post by QuickSphinx on 2011-09-01
1. Thank you for your reply,

2. The hard-line works on the live-cd, and now on the actual installation (I didn't do anything, I swear).

3. The wi-fi still freezes up the computer on the live-cd - Did you have to install any wireless drivers?

---

### Post by CrusaderAD on 2011-09-01
> **QuickSphinx said:**
> 3. The wi-fi still freezes up the computer on the live-cd - Did you have to install any wireless drivers?

Nope, it worked out of the box for me. Did you try the "Additional Drivers" tool? I've only ever used that tool for finding display drivers, but it might find some wifi drivers for you. Other than that, you may just have to do some research on what card that machine has and go from there.

---

### Post by QuickSphinx on 2011-09-01
Success! I ended up installing a program called "Windows Wireless Drivers" through the Ubuntu Software Center, and grabbing the Windows XP driver from here: 

[http://support.asus.com/download.aspx?SLanguage=en&m=Eee%20PC%201001PQD&p=20&s=1&os=17&hashedid=3qppYKbz4HQ2WNsm](http://support.asus.com/download.aspx?SLanguage=en&m=Eee%20PC%201001PQD&p=20&s=1&os=17&hashedid=3qppYKbz4HQ2WNsm)

Thank you for your help!

---

### Post by CrusaderAD on 2011-09-02
Nice! Glad you got it working.

---

