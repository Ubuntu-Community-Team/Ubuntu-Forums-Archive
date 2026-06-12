---
title: "LAN and Wireless LAN problems"
date: 2010-04-08
forum: General Help
---

### Post by Valorin X on 2010-04-08
I run a Toshiba T135 S1310 and recently installed ubuntu. I got everything working but I can not find a driver for my wireless anywhere online. My laptop has a Realtek® 802.11b/g/n wireless LAN. If anyone has made a driver for this or the LAN for the Ubunto 9.10, can you please help.

---

### Post by bobcollard on 2010-04-08
> **Valorin X said:**
> I run a Toshiba T135 S1310 and recently installed ubuntu. I got everything working but I can not find a driver for my wireless anywhere online. My laptop has a Realtek® 802.11b/g/n wireless LAN. If anyone has made a driver for this or the LAN for the Ubunto 9.10, can you please help.
Did you try Hardware Drivers under the System Menu in Ubuntu?  Quite often it finds the card and driver for you, all you need to have is an Ethernet connection to download the driver and then set it up using the Panel Internet Icon.

---

### Post by Valorin X on 2010-04-08
Yeah, it doesn't locate the driver, and I unfortunately have yet to find a driver online that works with it.

---

### Post by bobcollard on 2010-04-09
> **Valorin X said:**
> Yeah, it doesn't locate the driver, and I unfortunately have yet to find a driver online that works with it.
Run the following command in Terminal to find out the exact card you have:
  	 	 	 	 	 	  ```
sudo iwconfig
```

---

### Post by ivanovnegro on 2010-05-06
I hope I'm right here.
I have a strange problem with the LAN cable. My internet works but when I shut down my netbook and want to start it the next morning I have to start two times to have internet connection. 
The steps: I start my notebook normally, no connection than I have to put the cable out and restart, I have connection. 
I thought it's the cable so I put it out for the night but the same problem, I have to do everytime the described steps to have connection.
I hope for information

---

### Post by bobcollard on 2010-05-06
> **ivanovnegro said:**
> I hope I'm right here.
I have a strange problem with the LAN cable. My internet works but when I shut down my netbook and want to start it the next morning I have to start two times to have internet connection. 
The steps: I start my notebook normally, no connection than I have to put the cable out and restart, I have connection. 
I thought it's the cable so I put it out for the night but the same problem, I have to do everytime the described steps to have connection.
I hope for information
This is a different problem and should be in a thread of it's own.  Please open a new post.

---

### Post by kamaboko on 2010-05-21
> **Valorin X said:**
> I run a Toshiba T135 S1310 and recently installed ubuntu. I got everything working but I can not find a driver for my wireless anywhere online. My laptop has a Realtek® 802.11b/g/n wireless LAN. If anyone has made a driver for this or the LAN for the Ubunto 9.10, can you please help.

I've got the same laptop. I just installed 10.04, ran the updates (via ethernet cable connection), and all is good.  Everything works...wifi, video, etc.

Update: everything but the built-in mic.

---

