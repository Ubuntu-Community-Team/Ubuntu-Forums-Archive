---
title: "Something weird is going on with my internet conection"
date: 2011-04-06
forum: General Help
---

### Post by Nitrozzy7 on 2011-04-06
Hi,
I checked task manager the other day and I discovered that on the network history monitor some bits and bites were transfered in a repeating pattern (like a beacon). The transfer rate (when active) is about 149b/s receiving. And about 70b/s sending.
What is this? 
No Internet-related program was running from my part...
**In an attempt to pinpoint what was causing this, I occidentally removed the tools located left and right on the time and date. I've rebooted since but still no tools. The 0/I button is also gone.**

---

### Post by linuxyogi on 2011-04-06
> **Nitrozzy7 said:**
> Hi,
I checked task manager the other day and I discovered that on the network history monitor some bits and bites were transfered in a repeating pattern (like a beacon). The transfer rate (when active) is about 149b/s receiving. And about 70b/s sending.
What is this? 
No Internet-related program was running from my part...



Install nethogs to find out if any program is accessing the internet.

```
sudo apt-get install nethogs
```Then in terminal type

```
sudo nethogs ppp0
``` or ```
sudo nethogs eth0
``` depending on your connection type.


> **Nitrozzy7 said:**
> Hi,
**In an attempt to pinpoint what was causing this, I occidentally  removed the tools located left and right on the time and date. I've  rebooted since but still no tools. The 0/I button is also gone.**

Are you using gnome or kde?

If its gnome, right click on the panel (beside the clock) and click add >>> network manager 

I am not sure about this one :confused:

---

### Post by grahammechanical on 2011-04-06
What you need is to right click the top panel and select Add to Panel and select Notification Area, Indicator Applet, Indicator Applet Session. They will appear wherever you click the top panel. You can then move them to where you want. A reboot should get everything in place.

As for the other stuff. I would not worry. If you are connected by wireless then the computer and the modem/router will be doing a little transmitting and receiving to maintain the connection. Otherwise the connection will break and you will get a disconnected message.

Regards.

---

### Post by Nitrozzy7 on 2011-04-06
Thnx a lot. Right clicking did the trick! Same for nethogs. 
There is one program named "uknown TCP" (root, PID 0), but it's not active at the moment, according to nethogs. But I DO see the same activity (as I mentioned earlier) on the system monitor... WTF?!
And I'm not connected wirelessly.

---

### Post by Nitrozzy7 on 2011-04-06
:???

---

### Post by Nitrozzy7 on 2011-04-07
I used this command:
```
gksudo nautilus
```
to open a root window; I used Ctrl+H to dispay hidden files; there I found a file named "pulse.cookie"; shift+del and now problem solved! Or so it appears...

---

