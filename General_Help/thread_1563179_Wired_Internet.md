---
title: "Wired Internet"
date: 2010-08-28
forum: General Help
---

### Post by henriquez00 on 2010-08-28
I have wired internet, but I can't connect to my modem. I have cable internet (Comcast) but my computer can't detect it. I do not know what do to. Tried a whole bunch a things, but I'm a novice, so Help! (Ubuntu 10.something
I tried to call but they say everything was okay and I keep telling the Comcast lady I had Ubuntu, but apparently she insisted I had Windows. I thought they were not very smart, so I gave up on them.

---

### Post by corncob on 2010-08-28
See if Comcast can help you on this.  I know I had to configure my DSL modem before I could connect.

---

### Post by ktmom on 2010-08-28
I had (past tense) comcast and their modem was connected to my router.  With that setup, using 9.10 I didn't have to do anything, the router just recognized the modem.  However, when the setup was installed, the installer had to spend some time on the phone getting his laptop to recognize the modem itself.

---

### Post by MooPi on 2010-08-28
I would try to power cycle all devices. First turn off your computer, then the router or switch if you have one, then power down the cable modem. After one minute power them up in the opposite order, cable modem, wait until its all lit up then your router or switch (if you have one) then your computer. Hopefully this will correct your connection issue.

---

### Post by Data 1 on 2010-08-28
If you are connected directly to the modem and are using DHCP on the linux box of any breed it should connect. I would check the ethernet cable.... make sure it isn't a crossover cable. 

There is an IP address you can summon the modem setup with when connected, usually 192.168.100.1 on cable modems but comcast should be able to tell you the IP. Alternately you could google the modem model number and find the default connection IP.

When you have the IP ping it. If you can't ping it then no use going any further until the connection works.

---

